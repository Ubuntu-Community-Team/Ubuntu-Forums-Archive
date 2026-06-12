---
title: "How to fix flash problems on web browsers such as firefox and chrome?!"
date: 2013-05-05
forum: General Help
---

### Post by pavelexpertov on 2013-05-05
After upgrading my computer to xubuntu 13.04, I have encountered a problem where two web browsers were unable to play youtube videos properly. Even if I did reinstall it from scratch, problem stays.
PS. Also for weird reasons, each time i click on a window, a black square appears and captures around window's border. Did anyone manage to fix that?

---

### Post by pqwoerituytrueiwoq on 2013-05-05
from the xorg edgers ppa:> == New features ==

 June 29th, 2012: SNA is now on by  default on intel. If you have  problems (such as screen corruption, parts  of the screen not updating,  or crashes with intel_drv.so in the  Xorg.0.log backtrace), save this as  /etc/X11/xorg.conf
 ```
Section "Device"
        Identifier      "intel"
        Driver          "intel"
        Option          "AccelMethod"   "uxa"
EndSection
```


This note does apply to the 13.04

---

### Post by pavelexpertov on 2013-05-05
> **pqwoerituytrueiwoq said:**
> from the xorg edgers ppa:
This note does apply to the 13.04

Am i supposed to create a new file called xorg.conf or add a line of code?

---

### Post by pqwoerituytrueiwoq on 2013-05-05
if you have that file already merge it, most like you don't have that file so create it  and restart (you can just restart lightdm if you want)

---

### Post by OmgItsPixelated on 2013-05-06
If you only use flash for youtube you could consider switching to html5 which would eliminate the need for flash to play youtube videos. youtube.com/html5
but that simply avoids the problem instead of fixing it.

---

### Post by pavelexpertov on 2013-05-07
I don't have this xorg file, but when I tried to create it by entering code into text editor(Mousepad), it gives me an error "Permission denied" when I try to save it.
@[**[COLOR=#000000]OmgItsPixelated[/COLOR]**]("http://ubuntuforums.org/member.php?u=1483585") I'll give it a try in a sec.

---

### Post by Merrattic on 2013-05-09
You will need to sudo mousepad to save to /etc/...

---

### Post by pavelexpertov on 2013-05-09
merratic, but how am i supposed to sudo mousepad? By typing this: ```
sudo mousepad
```

or am i supposed to go to the actual directory of the file and do that?

---

### Post by Bashing-om on 2013-05-09
pavelexpertov; Hi !

There are a number of ways to invoke the editor in Super User DO mode; The most direct, in my opinion, is :
```
 sudo mousepad /etc/X11/xorg.conf
```note "X11" is upper case x. linux is case sensitive, x!=X  ..

will activate the editor "mousepad" and opens the file "xorg.conf" in the path "/etc/X11" with elevated privileges.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by pavelexpertov on 2013-05-10
Guys, thanx for help!!!!!!! It damn worked, no more flash problems and black boxes surrounding windows!! Enjoying xubuntu now!!!

---

