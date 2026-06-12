---
title: "Some audio problems with Ubuntu"
date: 2006-12-12
forum: General Help
---

### Post by PyroMessiah on 2006-12-12
Hey everyone.  I'm a complete newbie to Linux but I'm off the MS teet!!  So far I'm thrilled but I do have a couple of issues, both involving audio.

The first is that just strange things happen.  For instance, if I open a folder that contains some flac files or mp3s, sometimes one of them will just randomly start playing on its own without any media player starting and then a few seconds later it will stop.  Also sometimes when I am listening to a song it will just cut off out of the blue.

The second has to do with a project I'm doing.  My father in law has a bunch of tapes of his old professor giving speeches, teaching classes and so forth.   Some are as old as 25 years.  Anyway, he wants them all as mp3s.  While I was on windows I was using a program called lprecorder with simply a cord going from the headphone jack to the front panel input from the sound card on my computer.  The audio would play over my speaker and I could record it.  Now, the audio doesn't come through.  The only way I hear it when the tape is playing is if I go to system/preferences/sound then test the sound capture.  It will play then, but only while the test is being run.  So, I need to know how I can get the sound to play and also what program to use to record it.  

Any help would be greatly appreciated.  Thank you!!  And ubuntu rocks!

---

### Post by broekskw on 2006-12-12
morning.i think you have to go into a terminal mode and type in this command
" alsamixer " from there a new screen will pop up, use the arrow keys on your keyboard to get around.set all the bars to the correct levels(using the up arrows) and also unmute using the " m " key to unmute. this sould get you going i hope. also this is a good guide to look at if you are having sound problems

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

good luck:cool:

---

### Post by PyroMessiah on 2006-12-12
Okay I'm in the alsamixer thing.  I'm using the arrows but PCM and PC Speaker are the only ones that allow me to change the volume setting.  The others just do nothing when I hit the arrows.  Gah!!

Will read that link, thank you. :-D

---

### Post by cward002 on 2006-12-12
In response to your first question, I have found that music files will play a preview if you simply mouse over them. I guess its sorta like the thumbnail preview that shows up when you mouse over pictures in Windows but if I'm wrong I'm sure someone with more knowledge will correct me (this is encouraged.)

Colin

---

### Post by PyroMessiah on 2006-12-12
Okay that makes sense.  I just tried that and you're right.  That solves one thing then.  Thanks! :p

---

### Post by broekskw on 2006-12-12
ok go to one that you can not adjust and hit your leter m key on your key board, this soud unmute it and then use your up arrow key to ajust:D

---

### Post by PyroMessiah on 2006-12-12
Yeah I've already unmuted them but the up arrow still does nothing.  They just stay on 00.  ](*,) :confused:

---

### Post by broekskw on 2006-12-12
so after you get everything adjusted ,in a terminal mode input this command 
" sudo alsactl store 0  " this saves your alsamixer setting so the system remembers it all the time:mrgreen:

---

### Post by broekskw on 2006-12-12
ok so take a look at the sound guide that i put a link to, follow the directions there and you should find your solution. took me 6 times reinstalling ubuntu before i got my sound card going.hope that helps:mrgreen:

---

### Post by PyroMessiah on 2006-12-12
Oh geez I hope it's not that hard :-D 

I just installed realplayer a while ago for music files and now that's acting whacky too.  The songs skip and stall.  Ack!! 

Anyway I'm reading it now, thank you. :)

---

### Post by broekskw on 2006-12-12
this my sound a little off but what keyboard layout are you on. i did a canadian layout and the @ key would not come up for me had to go into systems>preferences>keyboard and select usa keyboar layout and save just to get the correct keyboard setup.

---

### Post by broekskw on 2006-12-12
that guide is really good so start from the beginning and follow all the instructions,at each step you should see a success or failure solution :D

---

### Post by PyroMessiah on 2006-12-12
I'm on the normal American layout I guess.  The arrows do work for a couple of the things (PCM, PC Speaker) but not the others.  I changed the input to front mic but I still hear nothing.

That page seems to be more about not getting sound at all.  I do have sound but just not for the input sound capture.

---

### Post by broekskw on 2006-12-12
ok sorry but the guide does have some good points on how to save and to see if your sound card is listed in your system correctly.hope someone else here can help you then as this is all that i can do(just a beginner also)off to 8 hours of work, good luck and keep trying over and over and keep searching you will find the solution :mrgreen: :mrgreen:

---

### Post by PyroMessiah on 2006-12-12
Thanks man!!  It's definitely a big help and I appreciate your assistance.  Have a great day!

---

### Post by broekskw on 2006-12-12
PyroMessiah did you get your sound card working :D

---

### Post by njoubert on 2006-12-19
Thanks a lot this helped me sort out all my sound problems!

---

