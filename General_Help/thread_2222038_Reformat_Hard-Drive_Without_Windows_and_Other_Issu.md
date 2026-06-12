---
title: "Reformat Hard-Drive Without Windows and Other Issues"
date: 2014-05-04
forum: General Help
---

### Post by will37 on 2014-05-04
[SIZE=2][FONT=arial]First of all, if this is the wrong forum for the questions I'm asking please let me know where I should be asking, I am not familiar with tech-help sites and communities.

Perhaps reformat is the wrong term, but essentially I got a black screen of death and am looking for a way to remove windows in hope that I can re-install it, and if not just install Ubuntu over what was partitioned to windows. I used GParted to delete the windows partition, but it couldn't actually read the data. It didn't display any error, but I don't think it worked.

About the Black Screen:
 [COLOR=#000000]It seems a lot of people have encountered the black screen with no all encompassing solution from what I have seen online. But maybe someone here might have some insight into possible causes for my specific situation.[/COLOR][/FONT][/SIZE][COLOR=#000000][FONT=verdana][SIZE=2][FONT=arial]The Problem: Computer freezes a couple weeks ago, I turn it off by holding power, get to error recover screen and when I try to start windows, computer shuts back down.When I try Windows recover Computer loads to black screen. Safe mode also shuts down the computer. So I used a linux program on a USB to recover the data I needed and installed Ubuntu in addition to Windows with a USB. Ubuntu seems to work fine, but I still cant re-install Windows , if trying to boot from disk the computer shuts down, and if I try to run the setup.exe in Ubuntu it says an error occurred while loading the archive, figured this is simply because it can't run Windows programs, but I'm not sure how to get the disk to boot.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][SIZE=2][FONT=arial]
Computer specs: I'm not sure what is useful, I generated the entire spec sheet but that's too long so here are basics.
[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][SIZE=2][FONT=arial]Computer Processor 8x Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz Memory 8118MB (1657MB used) Operating System Ubuntu 14.04 LTS User Name will (Will ) Date/Time Tue 22 Apr 2014 04:52:33 PM EDT Display Resolution 2390x768 pixels OpenGL Renderer Unknown X11 Vendor The X.Org Foundation[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][SIZE=2][FONT=arial]
Please let me know if you have any ideas, suggestions, websites, need more information, or even if your just as confused as I am. Could it be a hardware failure? Again, sorry if I'm not posting the right questions for this forum as the main problem is with windows, but I'm running Ubuntu now and I'm lost in this problem.[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by mörgæs on 2014-05-05
Hi, welcome to the fora.

You don't need to reformat in order to get rid of Windows. During the Buntu install you will have the option to use the entire disk for the new install. Choose this one, Windows gone.

---

### Post by Mark Phelps on 2014-05-05
> and if I try to run the setup.exe in Ubuntu it says an error occurred while loading the archive, figured this is simply because it can't run Windows programs, but I'm not sure how to get the disk to boot.

You can't install Windows from inside Ubuntu; you have to boot from the install media, instead.

Also, the general Windows failure is the Blue Screen of Death (BSOD) so named because it is a blue background with white text on it.  If you got a black screen with no lettering, that is a very different, most likely hardware, problem, especially if it came on you suddenly and you had not installed anything in Windows just prior to that.

You said safe mode also shuts the computer down but you didn't say if anything displays on the screen prior to that, or if it just immediately shuts down after you go into safe mode.

If you want to get Windows working again, you need to tell us that because, while there are some very good Windows experts on this forum, we primarily support getting Ubuntu working, not Windows.

There are excellent Windows forums that can help you diagnose your Windows problems -- if that is your priority concern.

---

