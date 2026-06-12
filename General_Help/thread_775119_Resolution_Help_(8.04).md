---
title: "Resolution Help (8.04)"
date: 2008-04-29
forum: General Help
---

### Post by ChomZ on 2008-04-29
hey, I'll admit I'm a complete newb at Ubuntu. I've just installed Hardy and for some reason the max resolution I can get is 1024 by 768. I've got an NVIDEA video card with the drivers running, but for some reason I can't increase the res.

Just so you know I am absolutely useless in the terminal and please don't assume I can do anything in it.

Any help would be awesome

---

### Post by bguebert on 2008-04-29
You may have already tried this but does Preferences->Screen Resolution have any other options?

---

### Post by ChomZ on 2008-04-29
that was the first thing (and the only thing) I tried.. the only options are smaller resolutions.. I want more numbers =P

edited for clarity

---

### Post by bguebert on 2008-04-29
Then I think you may have to edit something in your /etc/X11 folder. it used to be xorg.conf but it doesn't look like it used to. I had this same problem in an older version but it looks different now. I fixed it by adding a new screen type.

---

### Post by ChomZ on 2008-04-29
haha, okay you've lost me.. but I'll try some keyword searches and see what I can figure out.

thanks!

---

### Post by bguebert on 2008-04-29
a few things to try are "man xorg.conf" or "gedit /etc/X11/xorg.conf" entered at the command line
I'm not really an expert, but I remember this same problem giving me headaches and hopefully some of these terms will lead to a fix in a search somewhere.

---

### Post by Reg Editor on 2008-04-29
This article helped me to eventually increase the number of resolution options

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)


If I remember rightly,the command that I used was: sudo nvidia-settings

and this article came in handy

[https://answers.launchpad.net/ubuntu/+source/gedit/+question/3434](https://answers.launchpad.net/ubuntu/+source/gedit/+question/3434)

and specially


QUOTE

If you want to avoid using the terminal then do this instead:-

ALT+F2 (in Gnome)
Type the following command

gksudo gedit

And you will then be prompted for your password, and can use gedit to edit "system" files.

QUOTE

---

### Post by ChomZ on 2008-04-29
thanks a bunch, with all that I should be able to figure it out!

---

### Post by Reg Editor on 2008-04-30
You're welcome.I've only been using Linux/Ubuntu for a month and am slowly trying to figure it out.

---

### Post by ChomZ on 2008-04-30
well thanks everyone for you're help.. I was about to figure it out last night. Then this morning I went out and got a new screen and now the res is fine ;)

---

### Post by gcracker on 2009-01-15
> **ChomZ said:**
> well thanks everyone for you're help.. I was about to figure it out last night. Then this morning I went out and got a new screen and now the res is fine ;)

Since this fix is more of an escape, I thought I would tell you all what I (a 4-hour veteran of Ubuntu 8.10) figured out with the help of this forum. My problem is this: I installed linux on my Toshiba laptop with an ATI mobility HD-3650 and a 17" LCD maxed at 1440x900@60Hz. On install, Ubuntu only gave me resolutions up to 1024x768. I found ATI's catalyst drivers for Linux, and eventually found a way to make the installer work. I already forget how I made that part work, but I was getting the "must run as super-user" message. Anyway, the problem was not remedied until I came here and found....

Like Regedit said in post #7 ( [http://ubuntuforums.org/showthread.php?t=775119](http://ubuntuforums.org/showthread.php?t=775119) )

I used **Alt-F2** and typed *[COLOR="Blue"]gksudo gedit[/COLOR]*

and entered my pword

and then opened [I][COLOR="Blue"]xorg.conf[/COLOR] 
[/I]
I added [COLOR="DarkOrange"]"1440x900@60"[/COLOR] (with quotes) to the **modes** line of the **screen** section before all of the other modes listed there, rebooted and tada!

All fixed!!

I didn't even have to set it... it was automatic.

Now I am a 20/year veteran of Microsoft OS's, and there is a steep learning curve that I'm climbing here. I was great with the DOS-Shell, but bash is quite different to me. I'm sure some of you are reading this and saying, duh... or but why did you do it in XORG.CONF instead of an easier way?

It worked and I did it after only a few hours of popping my linux cherry..

I'm proud, and i hope it helps someone else too.

-Gcracker

P.S. I'm taking a class on Linux that covers Ubuntu, Mandriva, Blag, Yoper and more.. whee!

---

