---
title: "Lost X config.......3 distros all same time?!?!"
date: 2008-04-30
forum: General Help
---

### Post by jeffsa12 on 2008-04-30
I currently have 6 os's on this computer. Three Windows os's on a common hd and 3 Linux distros on 2 different hd's. I have Windows set up so that to boot, I select the 3rd hd during boot in bios for 1st to boot. This allows me to use Vista's boot controller completly seperate from grub, and allows me to boot into the different win os's. Grub is set up normally for my Linux booting.

I lost X config in my Ubuntu 8.04.....When booting, I got monitor out of range.

So I just attempted to boot into Ubuntu 7.10 to fix it.....same problem.

Then I tried to boot into my Mint 4.0 and got in, but my xorg config was all screwed up. Monitor settings were off and my ATI fglrx driver was disabled. Tried to re-enable it, but that resulted in totally screwing up Mint and not able to boot into it now!!! I get to a log in, and when I enter UN and PW, it freezes and sends an intermittent static-hissing sound through the speakers!!!

I tried both the reconfigure X in Ubuntu 8.04 that comes up automatically, and tried to reconfigure X in Mint using the sudo dpkg-reconfigure xserver-xorg command. No luck restoring a workable Linux distro.

This all seems VERY strange. I have had X lose it's configuration in a distro before, but was usually a result of me messing around with it, and I could always get into a different distro to straighten it out if need be.

I'm having NO luck....so how do I get into a shell now if my monitor comes up out of range before I can get into anything???

Sad windoz user by default!!!............

---

### Post by tom66 on 2008-04-30
Can you get into a terminal? Or recovery mode?

If so, get in to the root shell, and execute the following commands. Be very careful though because they mean editing the Xorg.conf file which controls all the display settings and other important stuff. 

```

cd /etc/X11
ls

```

With the list of files in front of you, copy the Xorg.conf.1 file to Xorg.conf. This will replace the current version with the last backup. If that fails, try copying the Xorg.conf.2 file to Xorg.conf, (and then keep going up to 6 if it doesn't work). Reboot every time.

Oh, and the command to copy:

```

cp <source> <destination>

```

---

### Post by jeffsa12 on 2008-04-30
Thanks Tom66,

Ok....could not get into terninal any way I tried so.....

I used my live Ubuntu 8.04 CD to boot....
created a root passwd, enabled root login, switched to root user.

I tried using all the previous versions of the xorg.conf.(all) versions without restoring to a usable system.

Used Nautilus to look at the /etc/X11/ xorg.conf of the live CD file system. The file has no info regarding video device driver, just "configured video device" with no other info.

I replaced Ubuntu 8.04's xorg.conf file with live CD's and could not boot Ubuntu 8.04.

I replace the entire Ubuntu 8.04 X11 folder with live CD's after that, and I could boot, but monitor 1440x900 still not correct, and tried to enable fglrx driver, resulted in unable to boot again......

By now I'm thinking hardware problem, so I boot into Vista and f###ed up monitor resolution!!!

Now I recall when I purchased the computer, an emachine el cheapo with Win Xp, I had monitor resolution and video driver problems intermittently. I thought it was from win updates screwing things up. That with other issues eventually led me into the world of Linux....but now I'm thinking the computer has hardware problems!!!

Is it possible my on board ATI Radeon 200 Xpress (rc410)hardware is somehow creating this problem since it's causing problems both Linux, Windows, various versions of both???

Any ideas on how to start trouble shooting??

I have Ubuntu 8.04 running again, using the live CD's version of the complete /etc/X11 folder, subfolders and all files.

I cannot even boot the Ubuntu 7.10 live CD any longer. It used to boot and run just fine in the past.

---

### Post by tom66 on 2008-05-02
Yes. Does your computer have a diagnostics utility built in? My Dell laptop has a simple utility which, on F12, will pop up and run some basic tests. If not, does it work on the live CD? 

Do you have a spare graphics card in an older computer. Slot it in, see if that works. If it does, then you probably, although not definitively, have a hardware problem. You might want to talk to your PC maker (E-machines) about this.

---

