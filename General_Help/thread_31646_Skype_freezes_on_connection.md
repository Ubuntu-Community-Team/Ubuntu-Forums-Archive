---
title: "Skype freezes on connection"
date: 2005-05-04
forum: General Help
---

### Post by olf on 2005-05-04
I am using the .deb referred to on ubuntuguide.org and it installs perfectly. I also can search and add contacts without any problem.

The trouble is when I either receive a call or try to call any of my contacts. The application just freezes and has to be shut down by killing the process. It seems that it has something to do with my audio chip since i can make calls when using a usb headset and not the sound card's in and outputs. There is still no way to receive calls since the ringing preference is locked to the soundcard.

Does anybody know how to fix or work around this?

I am using a HP nw8000 laptop and have no problem with sound in other applications.

.olf

---

### Post by oohazard on 2005-05-13
I have  the same problem as you.

skype freeze when i try to call.
on more , other people see me offline.

If you find a solution can you post here.

I will do the same.

Thanks

oohazard

---

### Post by Leif on 2005-05-16
This has been posted on other threads so maybe you've already seen it, but I had the same problem, and the solution is to edit /etc/esound/esd.conf
 and set auto_spawn=1.

---

### Post by robert114 on 2005-05-16
I had the same problem too, I just disabeled all the sound system notifications (in the Control Center).
this solved my problem (maybe Skype crashes when the sound card is in use by an other app)

what does auto_spawn=1. do??

---

### Post by Mystery47 on 2005-08-21
Try This:

Type in terminal: killall esd

And start program....

And when finished:

Type in terminal: esd  "This put sound back again"

This was solution to mine problem....=)

---

### Post by robert114 on 2005-08-22
I'm not having this problem any more since i've re-installed ubuntu but thanx anyway!

---

### Post by ekravche on 2005-08-28
I got this advice from [http://forum.skype.com/viewtopic.php?p=148934](http://forum.skype.com/viewtopic.php?p=148934) and it worked for me.

> just try : killall esd
and apt-get remove esound,
reboot, everything will be ok.

---

### Post by foxy123 on 2005-09-01
[QUOTE=ekravche]I got this advice from [http://forum.skype.com/viewtopic.php?p=148934](http://forum.skype.com/viewtopic.php?p=148934) and it worked for me.[/QUOTE]

I've got the same problem and this solution does not help. Strange enough when I installed Skype few weeks agoand tried it, everything workedjust fine. Then I tried it again few days after and got freeze every time I try to call anyone. Any help?

---

### Post by foxy123 on 2005-09-01
Another thing, it happens only in XFCE, whichis my default manager. It works fine in Gnome.

---

### Post by foxy123 on 2005-09-03
anyone to help? at xfce forum also no luck, skype forum is silent about that...

any debugging suggestions?

---

