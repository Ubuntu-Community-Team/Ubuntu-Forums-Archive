---
title: "What happened? Ubuntu won't load up now - help please!"
date: 2007-12-31
forum: General Help
---

### Post by BigSilly on 2007-12-31
Well, I don't know what's happened.

I've been using Ubuntu just fine for ages. A couple of days ago I used Start Up Manager to put a new usplash theme on it, but that's all I've done as far as making any changes goes, and it's been fine until now.

Tried to boot into my Ubuntu Gutsy about 20 minutes ago, and it won't go. I get GRUB just fine, select the OS, and it goes to the boot splash screen and the loading bar. It gets only a short way up this bar, before the screen goes black and there's a cursor in the top left of the screen. There it stays and won't go anywhere else.

Luckily I'm dual booting with another OS so I can at least get on the net to post for help. What happened, and can anyone here help me? I don't know why, but I have a sneaking suspicion that it may be something to do with the regular fsck checks that it's perhaps trying to perform but for for whatever reason cannot. If this is the case, what can I do?

Help.....

---

### Post by markharding557 on 2007-12-31
have you tried to boot in recovery mode that takes you to a cmd line,if this works you can type startx to a gui

---

### Post by BigSilly on 2007-12-31
Thanks, I hadn't tried this but have now, and you're right - it did indeed go straight into Ubuntu just fine. But what I noticed was that as soon as it started to boot in recovery mode, it went straight into its scheduled fsck check. I did get the feeling as I say that it was this that was causing the problem, and I'm now thinking it has something to do with my recent changes to the usplash theme via StartUpManager. I've reset these changes back to their original defaults, and removed the usplash theme that I had installed. Hopefully this will make everything OK from now on. Fingers crossed! 

Happy New Year anyway!

---

### Post by BigSilly on 2008-01-01
Gah! Looks like it is the fsck check that can't perform it's task. Today I forced an fsck check to test my theory, rebooted, and sure enough it did the same as before. Had to switch off the PC by holding in the button, and then used recovery mode whereupon it finished the task and went into the Ubuntu desktop.

But, this is going to happen again when the next scheduled fsck test comes around (every 27 times on my PC), and it's going to be a pain for the family. What can I do to fix this, and also, how did this happen in the first place? Could it be something to do with using the SUM to change the usplash theme?

Your help is much appreciated.

---

### Post by logos34 on 2008-01-01
You could try simply deleting the 'splash' option at the end of the 'kernel' line in /boot/grub/menu.lst

Or try this method of fixing splash:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown)

---

