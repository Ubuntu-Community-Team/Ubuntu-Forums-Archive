---
title: "sudo dpkg-reconfigure xserver-xorg Not Working"
date: 2008-05-19
forum: General Help
---

### Post by CC440 on 2008-05-19
I need to reser my display setting as I set them to something either to high for my monitor to read or it just cant refresh fast enough. sudo dpkg-reconfigure xserver-xorg only gives me the option to reconfigure my keyboard and won't give me any options relating to the display. What happened that is keeping this command form letting me access my display settings?

Also when I boot my computer the xubuntu logon and load screens work perfectly but then it goes blank when I try an load the desktop after login. Is my problem even with my display settings?

---

### Post by ibuclaw on 2008-05-19
Can you boot into Recovery Mode?

Ubuntu should come with an option call "Fix X-Screen Server".
Run that and then continue to Normal Mode.

And, to answer your other question, the xserver-xorg package no longer controls the Xscreen... at least, you can no longer configure the Xscreen with it.

The Ubuntu team have felt that autoconfiguration is the best route to go down  for the sake of user friendliness.

Regards
Iain

---

### Post by kthxbai2u on 2009-03-08
IMO this is not user friendly. Now X wont load, and I cannot fix it with "fix x server". It finishes "fixing" the x server, and then i select boot normally. I just get a blank screen, all services seem to have crashed, machine not responding to pings... Whether i install the ubuntu-desktop or the xubuntu-desktop package... I think i just remove them from the server for now so that it can run its services... It's coincidentally as soon as GDM is started... Maybe an apt-get remove --purge gdm and reinstalling may work...

Off to get beer

btw, what command you run to reconfigure the screen from console? I need to force 640x480 as I don't think the "auto config" is picking up the monitor correctly?

[EDIT]O.k..... So now I have completley removed ubuntu-desktop and xubuntu-desktop and then removed S30gdm from /etc/rc3.d and now it still does this... Looks like theres another copy of S30gdm in rc2.d ... I thought 3 was default runlevel... Meh. I got my console back :D I go try "startx" ok that crashes too... Whats up with this?[/EDIT]

---

### Post by darco on 2009-03-08
> **kthxbai2u said:**
> 

Off to get beer



ahh...the solution to all problems :D

darco

---

### Post by kthxbai2u on 2009-03-08
> **darco said:**
> ahh...the solution to all problems :D

darco

ahhaha yeahh :D

---

### Post by gjoellee on 2009-03-08
back to the topic.... reboot Ubuntu. When GRUB loads hit "ESC" and do a recovery boot. Then when the text based interface loads up, select "xfix". When xfix is finished select "continue normal boot".

---

### Post by darco on 2009-03-08
Are you logging in as root to run the  dpkg-reconfigure xserver-xorg command? I know you are typing sudo but boot into recovery then log in as root...

 
darco

---

### Post by kthxbai2u on 2009-03-08
> **tinivole said:**
> Can you boot into Recovery Mode?

Ubuntu should come with an option call "Fix X-Screen Server".
Run that and then continue to Normal Mode.

And, to answer your other question, the xserver-xorg package no longer controls the Xscreen... at least, you can no longer configure the Xscreen with it.

The Ubuntu team have felt that autoconfiguration is the best route to go down  for the sake of user friendliness.

Regards
Iain


> **darco said:**
> Are you logging in as root to run the  dpkg-reconfigure xserver-xorg command? I know you are typing sudo but boot into recovery then log in as root...

 
darco
lol... that idea was blasted out of the waters already lol....

---

### Post by dcstar on 2009-03-08
> **CC440 said:**
> I need to reser my display setting as I set them to something either to high for my monitor to read or it just cant refresh fast enough. sudo dpkg-reconfigure xserver-xorg only gives me the option to reconfigure my keyboard and won't give me any options relating to the display. What happened that is keeping this command form letting me access my display settings?

Also when I boot my computer the xubuntu logon and load screens work perfectly but then it goes blank when I try an load the desktop after login. Is my problem even with my display settings?

There are no settings to change any more, it is all autodetected now.

Some of the video driver packages have tools to set these things now (like nvidia).

---

