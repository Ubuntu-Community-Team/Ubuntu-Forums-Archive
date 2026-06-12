---
title: "Boot Loop after 140.4 to 1604 upgrade - Everything tried"
date: 2016-12-18
forum: General Help
---

### Post by codfishcatfish on 2016-12-18
Dear Group,
               a few days ago I crashed because Sbin had a problem with Splash but resolced using a Live disc and renamed Sbin and copied it from the live disc.

Now I thought it would be a good time to update and upgrade. but now  get a constant loop. I just get my username and a login button. It has a Black screen for a split second then back to login

I am using Xubuntu 16.4 now and here is a short list of what I have tried.... its not the fact I have not looked for every solution its none have worked.

renamed Xauthority,   sudo mv .Xauthority .XauthorityBak
Rebuilt the desktop even running Gnome
Deleted NVidia Drivers, rebuilt Nvidia drivers
Changed video card to AMD one.
Unity reset
dpkg repair
sudo chown username:username -R /home/username
sudo mokutil --disable-validation

I can't remember half the stuff I tried that is not listed here but quite a bit more. The one thing that is different is my username is spencer however at login it is Spencer with a capital S. So I made a new use called test but that didn't work.

Please any help is really appreciated. Still a bit of a noob but I learn quick.

Regards Spence

In fact everything you can imagine but nothing has worked.

---

### Post by ac2334 on 2016-12-21
Hi,

I'm having very similar problems and have tried most of the troubleshooting steps that you described. I prefer using Ubuntu and have tried with both 16.04 and 16.10.

Have you tried adding the line noapic to the boot sequence (grub menu)? I was going to try that next. What kind of computer do you have?

Some have suggested that simply closing and opening the lid or adjusting the brightness can kick the screen into working, but it doesn't work for me.

I get the login loop when I try Nvidia legacy driver 304 from Additional Drivers. Everything else gives me a black screen. The login loop happens exactly as you described - something about the way that Ubuntu/Xubuntu is trying to interface with the graphics card isn't working correctly.

Post here if you find any solution - thanks

---

