---
title: "Gutsy Freezing -- Caps Lock Flash"
date: 2008-01-31
forum: General Help
---

### Post by PlatoDan on 2008-01-31
Hello, 

I have been having some issues recently with Gutsy freezing on me. This can happen after a few seconds or after a few hours. Everything freezes up and nothing affects the computer at all, from Control+Alt+Backspace to the REISUB trick. The only thing that happens is the caps lock light flashes. (Please note that this is a laptop that does not have a scroll lock so I do not know if that would flash as well. But some posts with similar issues mention both caps and scroll lock flashing.)

I've looked around the web for an answer to this but I haven't found any exactly like it. I kind of gave up for a bit and hoped that an update would fix it, but so far no love. So the other night I decide to just reinstall Gutsy but when I booted to the live CD it froze in the same way. Then I thought it could be something on my computer, like my memory, but after two days of the memory test and no errors I gave up. 

The computer can run Windows with no problem, so I really don't understand where the problem could be. 

Some threads here have mentioned it might be a video card driver issue, and so I updated to the newest version, but it seems not to really make a difference as the problem happened on the live CD. I have tried using different levels of visual effects, but that also doesn't seem to make a difference. 

One thing about the freezing is that it happens faster if I have several programs open. If I just use firefox then it is stable for a while before crashing, but if I open up VirtualBox or Wine then it usually crashes right away. 

I have noticed in some of those same threads that it could be network card related--and I have been having a really minor issue with my wireless network card. Basically it will randomly drop the connection to my wireless network but still say it is connected and I either have to restart my computer or flick the laptops wireless radio switch off then back on for it to reacquire the signal. (This could be completely unrelated but just in case I wanted to mention it.) 

I have a Toshiba Satellite A200 with and Intel Core 2 T5300 processor. My Video card is a NVIDIA GeForce Go 7300. My wireless card is a Intel Wireless WiFi Link 4965AGN.

Sorry for being so long winded and let me know if you need more information to diagnose the problem.

Thanks! 

Dan :)

---

### Post by nadi on 2008-02-15
Hei Dan, did the problem go away, or did you find a solution? 
I am experiencing exactly the same problem. I am using a 3-4 month old laptop, X61s with a similar wireless card as your, which makes me think... maybe the wireless driver (iwl4965) causes the problem. 
Moreover, I only started to experience this problem after a kernel upgraded (of these automatic upgrades) to the recent, 2.6.22.14.21 and headers 2.6.22-14.52. I did not experienced this before!!

I would like to roll back to an older kernel version, but I dont know how in Ubuntu. Funny, I could really hack into the kernel in Gentoo, install different variants etc, but I really dont understand this Ubuntu method. 

Does anyone show us directions?
Thanks,
Nadi

---

### Post by PlatoDan on 2008-02-16
I'm still having the same problem Nadi. I've just been staying in Windows most of the time. 

If you think you can help, please do. Windows has been reminding me why I switched to Ubuntu in the first place. Thanks!

---

### Post by modomojo on 2008-02-26
My new (less than a week old) Toshiba A205-S5803 is experiencing the same issue.  

Please advise should you discover any solution.

---

### Post by nadi on 2008-03-03
Hei, my problem just dissapeared couple of days ago. I found out that XEMACS (yes, xemacs!) was the source of the problem. I removed it and reinstalled it. However, I did not had time to check whether the machine got stable, before the updates notification popped up, telling me about new versions of several liberaries. And it did the trick! So it was either xemacs or one of the libraries that triggered this serious failure. 

Anyway, now the problem is gone. It came when installing one of the and the kernel liberaries, and went away by updating, probably the same liberary, but I cannot tell which one.
Now everything is working perfectly for almost a week:)

---

### Post by lanzen on 2008-03-04
Dual Core + nVidia card should have a solution in driver 169.09. I've just noticed there's a new one, 169.12 but I haven't tried it yet.

Chech these:
[http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905)
[http://ubuntuforums.org/showthread.php?t=585714](http://ubuntuforums.org/showthread.php?t=585714)

---

### Post by Fran89 on 2008-04-28
Same bug but with Hardy let me explain.. i have a Toshiba Satellite and the Wireless had a problem, but i managed to find a patch, after the patch everything worked.. but when i connected a USB Internet afterward it would delete files in etc/network that are needed for the patch to work, when i replace them they just get deleted upon reboot, it detects my wireless but without the files it would crash rendering it useless(Screen totally freezed, Caps Lock & Scroll Lock lights flash)... i was even going to reformat but i decided to check here first any ideas?:confused:

solved... (driver problem)

---

### Post by marksmarks on 2008-04-29
Ubuntu 7.10 was running on my P3 with no problems.


Did a fresh install of Hardy 8.04.  Warm reboot. 
8.04 ran fine with no issues.


Did cold reboot.  Got blank screen with Caps & Scroll leds flashing.
(I had left a USB flash drive plugged in... cause of problem?)

Removed USB flash drive and Cold booted again.  8.04 booted normally and ran fine with no issues.

Next day, turned on the computer.  Got only desktop background color, beep, and message "HAL failed to initialize"


Cold booted again.  8.04 ran fine, no issues.

---

