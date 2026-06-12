---
title: "MP4 video repair ? - FFmpeg?"
date: 2014-07-19
forum: General Help
---

### Post by sarahfoxnz on 2014-07-19
Hello.

I've used FFmpeg in the past to reduce the MB size  of a few MP4 files.

I've now got a situation where a MP4 video (over an hour) works perfectly fine on my Ubuntu machine. but if i transfer it to my WIN machine, it breaks.

transfer process:

- Apache server active on my Ubuntu machine
- using [http://192.168](http://192.168)... ...  I can download files from my linux machine  to my WIN machine over wifi.


on my win machine, i can play all my videos fine (2-3 dozen files). however this one file plays fine on my ubuntu machine but  only plays 10 mins or so on my win machine & stops.


is there a process i can use on ubuntu to 'verify" the integrity of my MP4 file or repair it ? so it plays Ok on my other machine ? 
(i'm just backing up my files on both machines)

---

### Post by SeijiSensei on 2014-07-20
Did you copy the file to the Windows hard drive and play it from there?  Don't try to stream it from Apache.

What are you using to play the file in Windows?  I recommend [SMPlayer]("http://smplayer.sourceforge.net/"), the same excellent mplayer-based program that is available for Ubuntu.

---

### Post by zteam2 on 2014-07-22
Try to resave them with openshot, that solved a similair issue for me, a while ago.

---

