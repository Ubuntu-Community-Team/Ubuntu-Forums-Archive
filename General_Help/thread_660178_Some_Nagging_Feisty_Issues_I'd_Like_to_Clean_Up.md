---
title: "Some Nagging Feisty Issues I'd Like to Clean Up"
date: 2008-01-06
forum: General Help
---

### Post by Hopworks on 2008-01-06
I'm hoping the magic that solves my issues after I post for help works here. Always seems to...

I solved my nagging MySQL update issue, now I'm hoping to solve a couple more problems without having to reinstall.

Is it OK to put multiple problems in a post? I don't want to flood the general help forum with multiple posts.

1: Mouse left side button - Can't use it to "back up" in Firefox. I'd like to click that button to go back a page in my browser. This problem leads to issue #2 because I put in specific info into xorg.conf for my Logitech G5, and then realized I couldn't boot unless that mouse was plugged in. Even with that problem, all the 'fixes' I used still didn't allow me to use that left side button to back up in Firefox.

2: How can I configure xorg.conf to allow for more than one mouse type? I move around my mice regularly, since I have a laptop I'd like to use my Logitech G5 with, I often unplug it and plug in an Intellimouse. Every time I do that, my Feisty can't boot and goes into the screen with all the weird boarder characters, and I get the options to see the log files to figure what went wrong.

3: When I boot, it takes a long time, and I see the nVidia splash screen several times. I must confess... I moved my installed Ubuntu Feisty Server hard drive to drastically new hardware, and although it boots, and works, I wonder if there are references to all that old AMD hardware. How can I clean that up, or should I reinstall after all? I would LOVE to get rid of that nVidia splash screen appearing over and over, and shorten my boot time. I love nVidia, but SHEESH! :)

4: I gotta get rid of HellaNZB 1.2 to make way for a clean install of 1.3 via the repositories. I have no idea where I go to get rid of the old install.

Sorry for all the multiple issues. I'm getting better at Linux, but still a 1337 on the basics. I read up on that everyday, and try to learn something basic everyday so I don't have to ask such stupid questions.

EDIT: I researched all these issues, and tried some fixes, and they are still issues. I'm not just asking for the heck of it. FYI.

Thanks for your time!

Hop

---

### Post by Hopworks on 2008-01-06
Solved issue #4. I think I got HellaNZB .13 working. Now just the other 3 issues...

Hop

---

### Post by JohnPhys on 2008-01-07
I'm not sure exactly how the packaged ubuntu linux kernel handles the hardware change (I think most drivers are compiled as modules, and loaded dynamically as needed), but if you want to reconfigure your xorg.conf file, you should be able to run 

```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```

as stated in the initial comments of /etc/X11/xorg.conf.  I highly recommend making a backup of your current one in case things get messed up somehow.

If it were me, I would just try removing the nvidia driver, either manually or through the restricted driver manager, reconfiguring xorg as above, telling it to use the free "nv" video driver, and then re-enabling support for your nvidia card, either through the restricted hardware manager or by reinstalling nvidia-glx.  If everything goes to hell, just restore your backup xorg.conf .

---

### Post by Hopworks on 2008-01-08
> **JohnPhys said:**
> I'm not sure exactly how the packaged ubuntu linux kernel handles the hardware change (I think most drivers are compiled as modules, and loaded dynamically as needed), but if you want to reconfigure your xorg.conf file, you should be able to run 

```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```

as stated in the initial comments of /etc/X11/xorg.conf.  I highly recommend making a backup of your current one in case things get messed up somehow.

If it were me, I would just try removing the nvidia driver, either manually or through the restricted driver manager, reconfiguring xorg as above, telling it to use the free "nv" video driver, and then re-enabling support for your nvidia card, either through the restricted hardware manager or by reinstalling nvidia-glx.  If everything goes to hell, just restore your backup xorg.conf .

Thank you! I didn't know there was a free "nv" video driver alternative to using the latest driver from nVidia's site, that's if I read that correctly. I don't know what nvidia-glx is I'll admit, or how to re-enable nvidia support, but I'll research it.

And I ALWAYS backup the xorg.conf prior to making changes, and it has saved me a few times. That's good advice for sure. =)

---

