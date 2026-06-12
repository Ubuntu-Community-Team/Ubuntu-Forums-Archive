---
title: "Bash script to play sound files for 30 seconds each"
date: 2023-11-25
forum: General Help
---

### Post by raleigh3 on 2023-11-25
Could someone help me. I need a bash script to play a short sound file, wait for 30 seconds, play another sound file, wait for another 30 seconds.

(I will use it as a reminder to spend 30 seconds on each quadrant of my teeth when using a electric toothbrush.)

mpg123123 /usr/share/sounds/My_Sounds/Alarm_Clock_Sound.mp3 

sleep 30

mpg123 /usr/share/sounds/My_Sounds/Alarm-sound-buzzer.mp3 

sleep 30 

mpg123 /usr/share/sounds/My_Sounds/facility-alarm.mp3 

But it only plays the first sound file. ??

---

### Post by raleigh3 on 2023-11-25
[QUOTE=raleigh3;14166766]Could someone help me. I need a bash script to play a short sound file, wait for 30 seconds, play another sound file, wait for another 30 seconds.

(I will use it as a reminder to spend 30 seconds on each quadrant of my teeth when using a electric toothbrush.)

mpg123123 /usr/share/sounds/My_Sounds/Alarm_Clock_Sound.mp3 

sleep 30

mpg123 /usr/share/sounds/My_Sounds/Alarm-sound-buzzer.mp3 

sleep 30 mpg123123 /usr/share/sounds/My_Sounds/Alarm_Clock_Sound.mp3 

sleep 30

mpg123 /usr/share/sounds/My_Sounds/Alarm-sound-buzzer.mp3 

mpg123 /usr/share/sounds/My_Sounds/facility-alarm.mp3 

But it only plays the first sound file. ??

---

### Post by Doug S on 2023-11-25
What is wrong with the answer to this [same question over on ask]("https://askubuntu.com/questions/1493871/timer-program-that-plays-4-sounds-one-after-another-for-30-seconds-each") using "timeout"?

EDIT: I see you liked an recent edit to the answer over on ask, that kills the play process after 30 seconds.

---

