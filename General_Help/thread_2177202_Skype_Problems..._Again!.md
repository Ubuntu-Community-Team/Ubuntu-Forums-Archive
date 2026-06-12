---
title: "Skype Problems... Again!"
date: 2013-09-27
forum: General Help
---

### Post by IL TRIVELLA on 2013-09-27
Hi everyone, 

I just came back on Ubuntu after few years using a  MacBook Pro, I always liked Ubuntu, but the reason why I changed with an  Apple product was the lack of good programs, and the compatibility  problems with some of them, as example I remember I had one big problem  that were always so annoying for me, a problem with Skype, and it's so  disappointing for me to see that almost three years later, is always the  same...

I literally install Ubuntu again this afternoon, and  then I tried to find on the Ubuntu Software Center Skype, because I do  work abrod and I need it so much to keep in touch with family, friends  and girlfriend, but wasn't there, so I google it, and I found it on this  link [http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/) and then from the small menu for choose the distrubuition I  choose Ubuntu 12.04 (multiarch) even if is not the OS I got, because  today I have downloaded and installed ubuntu-13.04-desktop-amd64, the  latest version on the website, but on the small menu for download Skype  there isn't this option, so I choose the one that was in my opinion the  most close to the one I have.

But already during the installation  there was some small issues, but at the end I installed it, and on the  dock on the left suddenly appeared a blue icon with a question mark in  it, and when I was passing with my mouse indicator on it, were telling  me Skype, so I delete that icon, I found the real Skype icon from my  applications menu and I drag it on the dock.

Once I did that I opened Skype and I tried to call my girlfriend, and here starts the nightmare...

Everytime  she was calling me and I was picking up the call, Skype crashed,  everytime someone from my contact were going online and offline Skype  crashed, everytime she was trying to send me a picture, anyway a file,  Skype crashed, whatever I were doing, ignore it, accept it, or refuse  it, then after many time that Skype were keeping crashing and I had  everytime to start it again, suddenly the sound stops at all, I tried  many times closing it and opening it again but nothing, and then without  any motivation after few times the sound came back, and also in the  first times Skype were crashing it was asking me to send the report, but  when I was doing that it was telling me that because Skype is not  present in Ubuntu Software Center the program couldn't send it, we tried  to make a call from her phone first and then also from her laptop, but  was the same, after all this because I was desperate I wanted to make a  videocall with Facebook but apparently there isn't the option to do it  with Ubuntu.

The version of this Skype if is usefull to know is  the 4.2 for Linux, can anyone help me please, because I really need  Skype, and I can't believe that still, one of the most famous programs  on the world for communicate, is having such big issues to work  properly, I really can't believe it...

Thanks in advance for anyone will help me.

---

### Post by Habitual on 2013-09-28
I suggest that you mv the ~/.Skype directory to ~/.Skype.bak and start fresh.

Quit Skype altogether...
In terminal>
```
mv ~/.Skype ~/.Skype.bak
```
Start Skype. configure your preferences, etc... Just prefs. ;)
Your "userlist" will remain as it's stored on Skype Servers.

If you wish to keep your call and chat "history" as I needed to then...

Quit it altogether again. (Exiting fully) and
in terminal >
```

cp ~/.Skype.bak/<identity>/main.db ~/.Skype/<identity>/
```

Hope this helps you.

---

