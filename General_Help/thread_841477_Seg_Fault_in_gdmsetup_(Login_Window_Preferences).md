---
title: "Seg Fault in gdmsetup (Login Window Preferences)"
date: 2008-06-26
forum: General Help
---

### Post by SendDerek on 2008-06-26
Hey There,

Just installed latest updates as of today and restarted.  I'm not sure, but somewhere along the line gdmsetup stopped working.  So, going to System->Administration->Login Window will result in a quick splash of the GUI and then nothing.  Typing "gdmsetup" into the terminal will result again in a quick splash of the GUI followed by "Segmentation Fault" in the terminal.

Quick research shows that /etc/gdm/gdm.conf-custom may be significant to the problem.  Also in question are some things that deal with enabling/disabling Compiz and also the xorg configuration?  Disabling desktop effects has no effect on the issue.  Possibly related to [Bug #42712](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/42712).

Help would be appreciated.

Thanks,
Derek

---

### Post by shivans on 2008-06-27
I have exactly the same problem, was a resolution found for this?

---

### Post by shivans on 2008-06-28
bump

---

### Post by hickninja on 2008-06-28
I also just started getting this in Hardy. I tried everything from that bug, but no dice.

---

### Post by shivans on 2008-06-29
Here is the output from SystemLog:

kernel: [26539.277812] gdmsetup[12555]: segfault at 00000000 eip 00000000 esp bfbdec7c error 4

Can anyone provide any advice for this?

---

### Post by shivans on 2008-06-30
Anyone? Has a bug been submitted for this error, or can anyone offer a fix?

---

### Post by PhutterMan on 2008-07-10
Bump.  Same problem.

In older versions it had to do with having deleted gdm.conf-custom; mine, however, is intact and present.  I've never modified it, nor does anything in it look suspicious or problematic.

Any news?

---

### Post by harmonyMyth on 2008-07-13
another bump.

does anyone know if this is harmless unless you open the 
Login Window application?  i'm setting up this computer 
for a noob friend who i doubt would ever open that anyway 
and am wondering if i have to start over (maybe install 
ubuntu then add the mythtv package) or just leave it as is...

you may be able to reproduce this bug by:

install mythbuntu v8.04
open mcc (the mythbuntu control centre), 
   select "System Roles" 
   and under "Desktop Role" check "Ubuntu Desktop" and Apply.
Reboot (and see that you still don't have Gnome).
open applications->settings->loginWindow
   under general->defaultSession 
      change from mythbuntu to gnome and exit.
Reboot (and see that you still don't have Gnome).
open applications->settings->loginWindow
  and enter your admin password when prompted

and x crashes.

---

### Post by arqbrulo on 2008-07-13
It seems that gdmsetup is not the only program affected by this "bug". I'm also having trouble with my startup-manager. At first it would exit promptly, but now everything starts fine, but one I try to add a new usplash theme it crashes with the "segmentation fault" error. Also, in Wine, a program that I have (only one) was running fine, but now it also crashes unexpectedly. That one, however, does not give me any error messages, besides the usual fixme's.  Is anybody else having problems with other programs besides the gdmsetup?

EDIT: I decided to start my computer in recovery mode, one I was logged in as root, I started the gdm. I logged in using my user name/password, and I was able to run gdmsetup and startup-manager without any problems.

---

### Post by shivans on 2008-07-16
I was able to solve the problem I had by purging all nvidia based drivers from Adept and reinstalling them.

It solved all the seg faults I was getting.

---

### Post by jerome1232 on 2008-07-16
> **shivans said:**
> I was able to solve the problem I had by purging all nvidia based drivers from Adept and reinstalling them.

It solved all the seg faults I was getting.

Same here, I use the utility found on NVIDIA's website to compile mine, recompiling the driver fixed this issue for me as well.

---

### Post by arqbrulo on 2008-07-17
> **jerome1232 said:**
> Same here, I use the utility found on NVIDIA's website to compile mine, recompiling the driver fixed this issue for me as well.
Hmmmmm, maybe that's what I did wrong. I'll have to try it once I get home.

I did "sudo apt-get purge nvidia-*" and it also removed the linux restricted modules. I rebooted my system and installed the nvidia-glx-new but the modules were not re-installed. I spent another 10 minutes trying to figure out why my system was not accepting my nvidia card. Anyways, after having everything back to normal I launched gdmsetup again, and nothing. I'll try your suggestion, though.

---

