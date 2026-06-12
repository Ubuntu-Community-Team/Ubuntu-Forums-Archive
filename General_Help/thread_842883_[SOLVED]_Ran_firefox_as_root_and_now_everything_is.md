---
title: "[SOLVED] Ran firefox as root and now everything is messed up!!!"
date: 2008-06-27
forum: General Help
---

### Post by linuxisevolution on 2008-06-27
Ok first off, i updated. Then i had problems with sound so i installed a linux modules-generic. then i ran firefox as root to further access the problem. ( sudo firfox ) i know that was stupid but all i did was google. Then i had sound and everything was fine. The first problem is that when i re-opened firefox it asked me my forcast fox info to be put in. then i had to re-enter all my personal settings. But after doing that the settings are not saved. I tried restarting and then some "loading modules" thing came up and flashed like 6 times. then the "low graphics mode" windows poped up. i was told that that can mess up your .conf so i just hit crtl+alt+F1. i tried chowning my /home/example directory. then i restarted and decided just to click continue. then i used "screens and graphics" to fix my screen resolution. but now 3d acceleration wont work. ( no compiz/3d games ).i dont have sound either. i cant even change the sound level! i had a similar problem before and i had to reinstall. if this is not fixable:

[SIZE="5"]How do i reinstall without changing anything?[/SIZE]

I am not a noob to linux i have been using it for 3 years now and have had several problems i fixed. HELP!!!!

---

### Post by Rainstride on 2008-06-27
maybe you best bet is to back up all your files and do a clean install?

---

### Post by linuxisevolution on 2008-06-27
> **Rainstride said:**
> maybe you best bet is to back up all your files and do a clean install?
thanks but i rather not reinstall........ again....

any other thoughts?

---

### Post by Journeyman on 2008-06-27
check your /etc/X11 and look for xorg.conf, many times if it creates a new one it will make a backup xorg.conf.date I belive.  so try replacing it with one of those that you know is good.

---

### Post by Rainstride on 2008-06-27
im not even sure where to start... im not sure how it works but there is a rescue disk option on the alt install cd (live to?) i dont know exactly how it "rescues" but it might have some way of restoring your setup in some way without having to do a clean install. other than that im not sure what to tell you.

---

### Post by linuxisevolution on 2008-06-27
thanks i'll try it. i will write back if it works or not

---

### Post by aysiu on 2008-06-27
I don't know what's going on with your /etc/X11/xorg.conf, but you should **never** run the command *sudo firefox*. If you use the Ubuntu version of Firefox, you should update through the Update Manager. If you use the Mozilla version of Firefox, you should update with the command ```
gksudo firefox
``` More details here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

In the meantime, you can fix your Firefox (not xorg.conf) problems by typing this in the terminal: ```
sudo chown -R *username:username* /home/*username*/.mozilla
``` where *username* is your actual username.

---

### Post by linuxisevolution on 2008-06-27
thanks that fixed firefox!!! :) one down ;)

---

### Post by linuxisevolution on 2008-06-27
well there was no xorg.conf.backup.date.... but there was a xorg.conf.backup... so i copied the files from the backup to the current xorg and now it tells me my nvidia drivers are screwy! """ Problem installing Nvidia Drivers."""

thats what i saw when i typed "sudo startx"... i also saw that it couldnt lock the  xauthority file in my /home/user... so i tried sudo chown winrid:winrid /home/user... but that didnt help! if i try to install nvidia drivers it either says that they r installed or they r disabled upon reboot! i still have no sound! i dont know... im gonna search sypnatic and see what the last update did to my system! i had a bad feelling about "glx-new update"... and i think thats what cuased this. beware of the new nvidia updates! DO.NOT.INSTALL!!!!

i miss sound :(

---

### Post by linuxisevolution on 2008-06-27
> **Journeyman said:**
> check your /etc/X11 and look for xorg.conf, many times if it creates a new one it will make a backup xorg.conf.date I belive.  so try replacing it with one of those that you know is good.


help!!! how do i fix me graphics? im installing ubuntu-studio through synaptic...... i wonder if that will fix the problem-o by providing drivers. who knows... i cant reinstall... is it possible to reinstall ubuntu-desktop without changing anything????

---

### Post by Journeyman on 2008-06-28
ok here is what you can do, manually reconfigure it:
```
 sudo -dpkg-reconfigure xserver-xorg 
```

or boot up using the live CD, copy the /etc/X11/xorg.conf onto a thumb or mount your harddrive and copy it over.  That should fix it up all good except for the nvidia drivers.

---

### Post by cariboo on 2008-06-28
The only way you can reinstall Ubuntu without changing anything is if you have a separate home partition. 

The main thing to do not panic! Oops, I see it's to late.:) Just work on one thing at a time.

If you have recently upgraded, try starting in recovery mode, a menu will come up asking you what you want to do, there is an option to fix X.

---

### Post by ByteJuggler on 2008-06-28
> **linuxisevolution said:**
> Ok first off, i updated. Then i had problems with sound so i installed a linux modules-generic. then i ran firefox as root to further access the problem. ( sudo firfox ) i know that was stupid but all i did was google. Then i had sound and everything was fine. The first problem is that when i re-opened firefox it asked me my forcast fox info to be put in. then i had to re-enter all my personal settings. But after doing that the settings are not saved. I tried restarting and then some "loading modules" thing came up and flashed like 6 times. then the "low graphics mode" windows poped up. i was told that that can mess up your .conf so i just hit crtl+alt+F1. i tried chowning my /home/example directory. then i restarted and decided just to click continue. then i used "screens and graphics" to fix my screen resolution. but now 3d acceleration wont work. ( no compiz/3d games ).i dont have sound either. i cant even change the sound level! i had a similar problem before and i had to reinstall. if this is not fixable:

[SIZE="5"]How do i reinstall without changing anything?[/SIZE]

I am not a noob to linux i have been using it for 3 years now and have had several problems i fixed. HELP!!!!

I'm guessing you still have files owned by root in your home folder. 

So try:

```
sudo chown -R $(whoami).$(whoami) ~/.*
```

and

```
sudo chown -R $(whoami).$(whoami) ~/*
```

---

