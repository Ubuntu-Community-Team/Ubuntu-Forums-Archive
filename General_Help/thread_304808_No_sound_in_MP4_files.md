---
title: "No sound in MP4 files"
date: 2006-11-22
forum: General Help
---

### Post by BeNi.G on 2006-11-22
Hello !

Has I wrote in the title I can't hear sound in MP4 video files .
I can see the video but no sound .

I hope that somebody can help me here. Thanks

Sorry for my bad English

---

### Post by BeNi.G on 2006-11-22
Please ?

---

### Post by BeNi.G on 2006-11-23
bump

please I need your help  , I already searched and I couldn't find anything

---

### Post by anaconda on 2006-11-23
Have you got any sounds working at all? eg. is your soundcard working?

which sound codec does those mp4 files use? mp4 can have almost ANY encoding for sound eg. mp3, ogg, acc etc..

Check that you have all the required codecs installed. eg. automatix or easyubuntu could help you with this.

---

### Post by ColinG on 2006-11-23
gstreamwer plugin bad (or something like that) works on Rhythmbox

---

### Post by BeNi.G on 2006-11-23
I have the required codecs installed, and it still don't work

---

### Post by depele on 2008-06-20
Hello, 
I have the same problem!

somebody able to fix it?

grtz

---

### Post by Nikitas350 on 2008-06-20
Try play them with vlc. (run sudo apt-get install vlc)

---

### Post by Bigtime_Scrub on 2008-06-20
I had a similar problem with mp4's when I wanted to transfer them to my ipod (I dont know if thats what you are trying to do or not but this might still work for you). 

I was using avidemux to convert avi and mpeg into mp4. they would all play with no sound. 





Since there is a problem with the iPod accepting this encoded mp4 you will have to run it through a re-container to make it a fully working mp4. Now I know what your thinking, what exactly is the difference between the mp4 from avidux and the one that come out of the re-container? Well, to tell you the truth I don’t realy know, but I do know that if you put the mp4 from avidemux straight on to the iPod it won’t work, it will show on the screen but won’t play all you’ll get is a black screen for about 10 seconds and then it will take you back the the movies menu, or it will simply play but with no sound.

So I got a program:

sudo apt-get install gpac

This is a terminal based program that re-pacages the mp4 and will fix the mp4 produced by avidemux. Once you have the completed mp4 from avidemux pull up a terminal window and type:

MP4Box -add ‘original.mp4&#8242; ‘fixed.mp4&#8242;

* when typing in the original you also have to add its directory, and when putting in the name of the new fixed mp4 you need to also give the program a directory to put the fix in, for example:

scully@Laptop:~$ MP4Box -add ‘/home/scully/26.mp4&#8242; ‘/home/scully/ghost26.mp4&#8242;
Or in other words just type the “MP4Box -add” then space, then drag the original file into the terminal (if there is a space in the file name it will be put in ‘ ‘ ) follow this with a space and then type the name of the new file to be created. (I usually use a simple file name e.g. 001.mp4, as long as you remember which one is which if your doing several in one batch, cause you can always go back and rename it later)

---

### Post by depele on 2008-06-21
Thanks a lot. 

I'll check it out.

grtz..

Arne

---

