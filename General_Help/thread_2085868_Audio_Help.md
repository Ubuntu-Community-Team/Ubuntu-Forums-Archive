---
title: "Audio Help"
date: 2012-11-19
forum: General Help
---

### Post by kchaosrei on 2012-11-19
So i have recently installed the latest version of ubuntu and i need some help here.

I pretty much got everything set-up but the audio part. Currently I hear audio and my mic works. But i can not figure out how to make the mic capture audio and not play through my own speakers. 

To clarify I want the mic to work with mumble but i do not want to have to listen to my self. In windows there is just a box i have to press. But that doesnt seem to be a simple option here.

Someone please help.

---

### Post by kchaosrei on 2012-11-23
so i had to ask all my friends for help to find one that knew anything about linux. Was so easy i don't understand why someone didn’t just point me in the right direction. This thread did have over 100 views after all.

Anyways the answer to my problem is the alsamixer.(what is it? not sure but it seems to be a better version of audio control than what is built in to the GUI)

So here is a guide in-case others are having this issue. or want to cause the problem i was having. 

run terminal
Sudo alsamixer(it will ask for password as usual
press f6 and select your audio hardware.
Press f5(all) for capture and playback devices(though u could press just f4 for capture only
Assuming you pressed f5 you will have 2 mic sections. one will be labelled capture. Don’t touch that one. 
Lower the value of the other one to 0(arrow keys)
Incase of wanting to hear your own voice(increass to 50 to 100 depending on desired sound lvl.
(these changes are done in real time so if you change something and you dont have the desired effect undo them and try another slider)
close alsamixer once done.

Its actually pretty simple once someone gives you a place to start. Hopes this helps someone else

---

