---
title: "Re: webcam software for timelapse photography reccomendation please"
date: 2019-04-17
forum: General Help
---

### Post by iamtheeggman2 on 2019-04-17
Hi I found this, however i wondered if anyone here had any recommendations that were for better photography softawre with a gui?

[https://www.linuxquestions.org/questions/linux-software-2/webcam-taking-pictures-periodically-4175483704/](https://www.linuxquestions.org/questions/linux-software-2/webcam-taking-pictures-periodically-4175483704/)

Thanks in advance

i'd like to install this but it wont work?? any ideas? thanks in advance

[https://shinobi.video/docs/start](https://shinobi.video/docs/start)

home@home-System-Product-Name:~$ bash <(curl -s [https://gitlab.com/Shinobi-Systems/Shinobi-Installer/raw/master/shinobi-install.sh](https://gitlab.com/Shinobi-Systems/Shinobi-Installer/raw/master/shinobi-install.sh))

Command 'curl' not found, but can be installed with:

sudo apt install curl

---

### Post by HermanAB on 2019-04-18
The DIY method would be to use ffmpeg or gstreamer to take a snapshot and put an entry to a little script in a crontab.

[https://trac.ffmpeg.org/wiki/Capture/Webcam](https://trac.ffmpeg.org/wiki/Capture/Webcam)

The advantage of that is that you then actually learn something also.

---

### Post by iamtheeggman2 on 2019-04-19
Unfortunately I have not been able to complete this task on Linux ubuntu.

I ended up using Windows ten to use the endoscope and then use a screen capture tool to film it with time lapse function. I'll post the names of the software tomorrow and close the thread but thanks again for the help you have given me on the task. I tried running Linux puppy but but it didn't run which is strange because I have used the endoscope on the laptop in the past with the live disc. Maby puppy do not like the motherboard!

The webcam software used was the one which came with the camera, i don't think it has a name, anyway it has settings itself for doing time lapse but for some reason it didn't work, the screen capture software is from hallelujah software, its free version has some limitations
[https://hallelujahsoftware.com/products/](https://hallelujahsoftware.com/products/)

its easy to use, it lets you select various sources for the video whether it be webcam (that didnt work which is strange#0, whole screen or a specific window.

Well I have just learned something very interesting, I don't know what has happened because i haven't done anything in linux today, but when i run cheese out of curiosity it shows the endoscope camera working and it actually has settings in there to take so many pictures with so  many seconds between each picture so essentially i can use cheese to do a timelapse in linux!!!

wow, cheese is actually taking pictures for me with one second intervals! Exactly what I wanted, these can then be glued up to make a film, although to be fair the windows will export straight to video.

I wonder why this didnt work before?

---

