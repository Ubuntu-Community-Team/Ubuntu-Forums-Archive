---
title: "How can one install Xubuntu on top of Ubuntu?"
date: 2008-04-16
forum: General Help
---

### Post by jcr1 on 2008-04-16
> **aysiu said:**
> This will give you a relatively clean Xubuntu. It's worth a try, since you're planning to reinstall anyway.

Step 1: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)
Step 2: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Would performing these procedures effectively make your system the same as if you had put a xbuntu cd in and done a fresh install?

Or...would doing this reverse any mess you have made in the ubuntu install?

Cheers,

Jon

---

### Post by aysiu on 2008-04-16
In theory, it would be the same as doing a fresh Xubuntu install, but in practice, it may be slightly different.

In terms of reversing mess... probably not. It just removes system-wide-installed packages. It does not change personal configuration files.

If you made a mess of Ubuntu (Gnome), then you can try renaming the Gnome configuration folders: ```
mv ~/.nautilus ~/.nautilus.old
mv ~/.gconfd ~/.gconfd.old
mv ~/.gconf ~/.gconf.old
mv ~/.metacity ~/.metacity.old
``` and then log out and log back in again.

---

### Post by jcr1 on 2008-04-16
> **aysiu said:**
> In theory, it would be the same as doing a fresh Xubuntu install, but in practice, it may be slightly different.

In terms of reversing mess... probably not. It just removes system-wide-installed packages. It does not change personal configuration files.

If you made a mess of Ubuntu (Gnome), then you can try renaming the Gnome configuration folders: ```
mv ~/.nautilus ~/.nautilus.old
mv ~/.gconfd ~/.gconfd.old
mv ~/.gconf ~/.gconf.old
mv ~/.metacity ~/.metacity.old
``` and then log out and log back in again.

This sounds useful...what do each of those do? I know nautilus is the file manager and metacity is something to do with appearance?

A problem I am having came about trying to do something with either xorg, fglrx or something like that to do with gfx drivers...since then if I log out, i can only log back in through the failsafe option!

Cheers,

Jon

---

### Post by aysiu on 2008-04-16
Oh, you changed /etc/X11/xorg.conf? That's a different story. If that's the case, it won't matter if you rename your Gnome configuration folders or install Xubuntu.

Do you have a backup of your old /etc/X11/xorg.conf file?

---

### Post by jcr1 on 2008-04-16
I honestly am not 100% sure what I did.... I believe if I look in the right place (xorg?) that my gfx driver is just ati not fglrx. but since messing with it trying to get compiz to work I can now only login in failsafe mode...

It says logging in without startup scripts, so I assume something in there is broken.

---

### Post by PmDematagoda on 2008-04-16
Just thought I might help out a little by moving the posts to a new threads since you are necessarily necromantic by replying to the old one.:)

---

### Post by jesusfreak107 on 2008-04-16
> **jcr1 said:**
> I honestly am not 100% sure what I did.... I believe if I look in the right place (xorg?) that my gfx driver is just ati not fglrx. but since messing with it trying to get compiz to work I can now only login in failsafe mode...

It says logging in without startup scripts, so I assume something in there is broken.
Ooh!  Ooh!  One of these!!!  
I know what to do, as I am an aspiring Linux Geek Teenager, and my entire life revolves around pressing big, red, buttons.  Therefore, I have screwed up my visuals *plenty* of times.  This little bit of code has come in handy a TON of times.  It will cause you to go through the original Xorg setup process, where it will rescan all of your hardware, and you can select all of your drivers again.  
> dpkg-reconfigure -phigh xserver-xorg
Don't ask me what it means, I pride myself on my Tech skills, but I am 15, so I just do not have much *knowledge* yet.  I found this string of code somewhere, and, as I said, it has come in handy many times.  Note:  I am not sure, but, if you are using any advanced graphical configurations, this *might* reset them.  I have not had the need to use this since I got my new computer, and my old one that I used this on had no special graphics whatsoever.

---

### Post by jesusfreak107 on 2008-04-16
> **PmDematagoda said:**
> Just thought I might help out a little by moving the posts to a new threads since you are necessarily necromantic by replying to the old one.:)
Thank you, I was just about to point out that this post should either be moved, or started again in a different section, but you, being one of the many wonderful and *brilliant* admins on this forum, fixed the problem before the problem even presented itself!

---

### Post by jcr1 on 2008-04-16
Thanks for the move.

Thanks for the code jesusfreak107, although I am pretty sure I have tried this. I will try again when I get home.

Question still remains, If i follow the instruction in o.p., will this be like a fresh install and get rid of these problems...will it reset startup scripts, drivers etc...anything I may have hurt when trying to play with compiz?

Although reading back it has been answered really... hmm...this is where I get stuck!

---

### Post by PmDematagoda on 2008-04-16
> **jesusfreak107 said:**
> Don't ask me what it means, I pride myself on my Tech skills, but I am 15, so I just do not have much *knowledge* yet.  I found this string of code somewhere, and, as I said, it has come in handy many times.  Note:  I am not sure, but, if you are using any advanced graphical configurations, this *might* reset them.  I have not had the need to use this since I got my new computer, and my old one that I used this on had no special graphics whatsoever.

While I admire your willingness to help I must advice you to please be careful about the code you post and make sure you know something about it before you do, that can help prevent any problems:).

About the code you provided, it is not harmful, what it does is that it necessarily resets the X-Server settings(or sets) to the settings of highest priority in the "eyes" of X-org, which in many cases means the "vesa" graphics driver and any other options that X-org believes to be fail-proof.

---

### Post by jesusfreak107 on 2008-04-16
> **PmDematagoda said:**
> While I admire your willingness to help I must advice you to please be careful about the code you post and make sure you know something about it before you do, that can help prevent any problems:).

About the code you provided, it is not harmful, what it does is that it necessarily resets the X-Server settings(or sets) to the settings of highest priority in the "eyes" of X-org, which in many cases means the "vesa" graphics driver and any other options that X-org believes to be fail-proof.
Yes, I fully realize the danger of sharing code, and I WILL NOT post any code on here, unless I KNOW FOR SURE that it works.   Yes, that sets it to Vesa, but it also brings up the setup screen, and during that, you can choose a different driver.  Also, in this case, Vesa would most likely work, enough that he could boot into his account, and correct the driver problem.  But thanks for reminding me, one can never be too carefull, and reminding someone of danger never gets old.  :)

---

