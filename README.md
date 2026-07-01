<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CHUD toucher</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:Arial,Helvetica,sans-serif;
    background:linear-gradient(180deg,#73c1ff,#4f8de8);
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    height:100vh;
    overflow:hidden;
}

h1{
    color:white;
    margin-bottom:8px;
    text-shadow:2px 2px 4px rgba(0,0,0,.2);
}

#score{
    color:white;
    font-size:34px;
    margin-bottom:25px;
    font-weight:bold;
}

#blob{
    width:300px;
    height:240px;
    background:white;
    border-radius:58% 42% 53% 47% /
                   44% 56% 38% 62%;
    position:relative;
    cursor:pointer;
    transition:transform .08s;
    box-shadow:
        inset -12px -12px 20px rgba(0,0,0,.08),
        0 18px 35px rgba(0,0,0,.25);
}

#blob:hover{
    animation:wobble .8s infinite alternate;
}

#blob:active{
    transform:scale(.95);
}

.eye{
    width:62px;
    height:82px;
    background:#111;
    border-radius:50%;
    position:absolute;
    top:62px;
}

.left{
    left:75px;
}

.right{
    right:75px;
}

.pupil{
    width:22px;
    height:22px;
    background:white;
    border-radius:50%;
    position:absolute;
    top:14px;
    left:16px;
}

.pupil2{
    width:10px;
    height:10px;
    background:white;
    border-radius:50%;
    position:absolute;
    bottom:18px;
    right:12px;
}

@keyframes wobble{
from{
border-radius:58% 42% 53% 47% /
               44% 56% 38% 62%;
}
to{
border-radius:45% 55% 42% 58% /
               60% 40% 55% 45%;
}
}

#achievementPopup{
    position:fixed;
    top:20px;
    right:20px;
    background:white;
    color:#222;
    padding:15px 20px;
    border-radius:15px;
    box-shadow:0 10px 25px rgba(0,0,0,.25);
    transform:translateX(350px);
    transition:.5s;
    font-weight:bold;
    min-width:220px;
}

#achievements{
    position:fixed;
    left:20px;
    top:20px;
    width:240px;
    background:rgba(255,255,255,.92);
    border-radius:15px;
    padding:15px;
    box-shadow:0 8px 20px rgba(0,0,0,.2);
}

#achievements h2{
    margin-bottom:10px;
    font-size:22px;
}

#achievementList{
    padding-left:20px;
}

#achievementList li{
    margin:6px 0;
}
</style>
</head>
<body>

<h1>CHUD toucher</h1>

<div id="score">Score: 0</div>

<div id="blob">

    <div class="eye left">
        <div class="pupil"></div>
        <div class="pupil2"></div>
    </div>

    <div class="eye right">
        <div class="pupil"></div>
        <div class="pupil2"></div>
    </div>

</div>

<div id="achievementPopup"></div>

<div id="achievements">
    <h2>TOUCHES</h2>
    <ul id="achievementList"></ul>
</div>

<script>

let score = 0;

const scoreText = document.getElementById("score");
const blob = document.getElementById("blob");
const popup = document.getElementById("achievementPopup");
const list = document.getElementById("achievementList");

const achievements = [
    {score:1,name:"you've touched your fat lil chud"},
    {score:10,name:"your chud is gettin a lil annoyed from allat touching"},
    {score:25,name:"wait a sec yo lil chud is sayin somthing chud(eda myre thayoli koori mone)"},
    {score:50,name:"chud:pls stop touchin me or im callin cps"},
    {score:100,name:"chud:BRO😭😭😭"},
    {score:200,name:" chud:alr bro js stop touchin me ill giv you my niggas stuff [instagram:shi.yeah,address:8'35'42'23'N'76'52'02'25'E,btw shes lesbian😊😊]"},
    {score:250,name:"chud:BRO I TOLD YO AHH EVERYTHING PLS STOP💔😭"},
    {score:300,name:"chud dies cuz you touched him to much but his soul entered the devs body so sleep with one eye open cuz chud will be waiting to to give you a fate worse than death"}
];

const unlocked = [];

blob.addEventListener("click", () => {

    score++;
    scoreText.textContent = "Score: " + score;

    blob.style.transform = "scale(1.08)";

    setTimeout(()=>{
        blob.style.transform="";
    },70);

    checkAchievements();

});

function checkAchievements(){

    achievements.forEach(a=>{

        if(score>=a.score && !unlocked.includes(a.name)){

            unlocked.push(a.name);

            const li=document.createElement("li");
            li.textContent=a.name;
            list.appendChild(li);

            popup.innerHTML=
                "YUPIEEE Unlocked!<br><br><strong>"+a.name+"</strong>";

            popup.style.transform="translateX(0)";

            setTimeout(()=>{
                popup.style.transform="translateX(350px)";
            },2500);

        }

    });

}

</script>

</body>
</html>
