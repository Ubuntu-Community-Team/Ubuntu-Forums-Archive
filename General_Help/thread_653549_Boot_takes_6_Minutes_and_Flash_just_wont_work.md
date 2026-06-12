---
title: "Boot takes 6 Minutes and Flash just wont work"
date: 2007-12-30
forum: General Help
---

### Post by Dad1985 on 2007-12-30
So I am now running XUbuntu but in the past 2 days I have tried the current versions of  Ubuntu, Fluxubuntu, Kubuntu, and Mint.  All except mint give me the exact same to problems, so I am sure if I can fix it in one, the problem will be resolvable on the other's.  I have 2 problems.


Problem 1 :When I boot any variation above except mint, after grub comes up and I choose Ubuntu, it seems that the time from my choice to the login screen takes around 5-6 Minutes.  It just sits at a Black screen.  Then after about 5-6 minutes my login screen will show up.  My system info is below the second question.


problem 2:  Flash on all Distro's but Mint will not work.  Ihave tried to install the macromedia version, and gnash-gtk and then after attempts for the flash-nonfree.  All have failed, even though my system knows it is installed.  Whenever I go to a flash site, such as youtube, it still says I need the flash plug-in.  But it just doesn't work.  My main way of installing flash was via the Ubuntu restricted extra's, though even when this is installed.  I still get no flash.  


My system.

IBM Thinkpad T40
Pentium M 1.3 Dothan
512mb of ram
I dual boot on a seagate 7200 rpm hdd with windows xp.

Thanks in advance.

---

### Post by Sef on 2007-12-30
1) What is your video card?  Likely could be a problem with the driver.

2) Have you opened Universe and Multiverse repositories?

---

### Post by Dad1985 on 2007-12-30
> **Sef said:**
> 1) What is your video card?  Likely could be a problem with the driver.

2) Have you opened Universe and Multiverse repositories?



I solved the boot problem by resetting my splash screen to a smaller res.  I then set grub to look for the different vga code of 791;




As for the flash, yes I have al repositories open.

---

### Post by mayonaise15 on 2007-12-30
I think i was having the same problem with my grandpa's computer the other day.  I finally looked at the console message from installing flashplugin-nonfree and it was complaining that the MD5 of the downloaded file did not match the expected, so it wouldn't install it.  I would think Synaptic would raise a flag saying there was an error, but it just kept saying it installed properly.  Here is what I had to do step-by-step:

```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -zxvf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
./flashplayer-installer
```

It will then guide you through the install process.  I think the only strange thing in install process was I had to tell it where firefox was installed:
```
/usr/lib/firefox
```

Best of luck to you and let us know how that works for you.

---

### Post by ugm6hr on 2007-12-30
Does this help with the flash issue?
[http://ubuntuforums.org/showthread.php?t=648356](http://ubuntuforums.org/showthread.php?t=648356)

How did you install flash the first time?  I just went to a webste - was prompted to install flashplugin nonfree, and agreed. Worked for me, but I gather the link above is more stable.

I would suggest you remove all your existing flash / gnash installations before trying again.

---

