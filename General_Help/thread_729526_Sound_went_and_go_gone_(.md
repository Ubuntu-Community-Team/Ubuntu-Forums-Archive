---
title: "Sound went and go gone :("
date: 2008-03-19
forum: General Help
---

### Post by ThatGuyThere on 2008-03-19
Hey everybody... My sound was working fine RIGHT before I installed flashplayer and went to youtube. Sound didn't work there, and it doesn't work in Amarok either (The error message from Amarok : 

Audio output unavailable; the device is busy.
xine parameters: 

)
I think it's something with flash, because I had the same problem right after installing it on a Kubuntu install (running xubuntu at the moment). When I go to apps->Settings->Mixer settings, all I see under Device is default, and no sound options for it.

EDIT: After having the same problem in kUbuntu, I had to reinstsall. I'm pretty sure that it's the flash doing this.

---

### Post by ThatGuyThere on 2008-03-20
Bump...

---

### Post by RJ Hythloday on 2008-03-20
I've been having similar trouble, I'll follow your thread see if it gets any further than mine.
 
[You tube and mp3 troubles](http://ubuntuforums.org/showthread.php?t=728962)

---

### Post by ThatGuyThere on 2008-03-20
I checked out your thread, and we have the exact same problem. Do you get no audio output at all?

---

### Post by RJ Hythloday on 2008-03-20
nope, not any more, not even .flac now.

---

### Post by rakydude on 2008-03-20
I did some googleing for you and found this:
[http://ubuntuforums.org/showthread.php?t=672846](http://ubuntuforums.org/showthread.php?t=672846)
[http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)

I hope it can help you :)

---

### Post by Arthur Archnix on 2008-03-20
Go into your system sound preferences, >system >preferences >sound

Under sound events, it's probably on autodetect, but there's bunch hidden under there. Change it to each one and hit test. Do any of them work?

---

### Post by ThatGuyThere on 2008-03-20
I'm in xUbuntu, I don't have a  system Preferences -> sound. I went to apps-Preferences-system settings, and hit the sound button, but that brought up the mixer, which stays at default.

EDIT: I went to check out /dev/sda in the graphical interface, but I have nothing but /dev . Is that a problem?

---

### Post by jdb2 on 2008-04-05
You might want to try what I suggested in this post : 
[URL="http://ubuntuforums.org/showpost.php?p=4659226&postcount=4"]
http://ubuntuforums.org/showpost.php?p=4659226&postcount=4[/URL]

In my case, for some reason, Wine was causing problems. 

jdb2

---

