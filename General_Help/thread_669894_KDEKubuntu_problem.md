---
title: "KDE/Kubuntu problem"
date: 2008-01-16
forum: General Help
---

### Post by Jorgel on 2008-01-16
Hello everybody. I have a problem here. First off this is my first experience with any Linux distro of any kind so please bear with me.

I installed KDE last night and everything was great!! Come back home tonite turn on my computer and Grub takes me to the Kubuntu boot up screen. Here's where it gets irritating. The bar starts loading and then... it goes into a command line mode instead of the regular login. It asks for my user name.. done, asks for password...done and then..... it remains on the command mode and thats where I'm at.

What do I do to have it work properly again? I'm just an Ubuntu newb so many aspects of commads and such are still over my Linux knowledge.

---

### Post by SOULRiDER on 2008-01-16
When GRUB appears press 'e'e to edit the entry. Then delete the words 'quiet' and 'splash' , press enter and then press 'b' to boot. See if you get any errors.

---

### Post by Jorgel on 2008-01-16
TY for your reply soulrider. Unfortunately I tried your suggestion, but other tahn taking a little longer it did the same.  At the end I was asked for my username and password. Punched both in and I got the command entry line, but that was it :(  Any other suggestions?

---

### Post by Sami_Sdata on 2008-01-16
This is a longshot but do you have a kvm switch connected between you and the monitor?  I've had problems with older ones blocking the plug and play info from the monitor.  Everything would work great until the first time I powered the computer off then X would crash when I turned it back on.

---

### Post by Jorgel on 2008-01-17
Actually I forgot to post that it's a laptop dualbooting XP & of course Ubuntu. I installed Ubuntu 7.10 on Monday after giving the OS a spin on Live CD it worked flawlessly while on Live cd, 

After installing I started having problems with Ubuntu and my graphics chipset driver which I still haven't been able to resolve it (keeps backtracing to a generic driver) even when in the Live CD session it works just fine and with the correct driver, but that should be another thread. I installed KDE since I like the eye candy and wanted to check the other apps. 

Is there anyway to uninstall KDE from this terminal screen I'm getting, maybe that could help. Or even can I uninstall the OS altogether and reinstall to try and fix it? I have no documents or anything important that I might lose by doing this.

Thanks for your suggestion **Sami_Sdata **but it doesn't apply to my system and thanks to anybody else that might reply. I really like Ubuntu and want to start working and learning it.

---

### Post by Sami_Sdata on 2008-01-17
Login and try running "startx".  If it crashes send the errors you get.  If it doesn't you'll end up in a blank gray screen.  ctl-alt-backspace will drop back to the prompt.  Also, looking at the file /var/log/Xorg.0.log might help.  That should log any errors that happened when your system tried to start X.

---

### Post by Jorgel on 2008-01-19
Ok I tried what you asked... and this is what I got :(

[IMG]http://i75.photobucket.com/albums/i303/ReefPR/Screenkdeerror.jpg[/IMG]

---

### Post by Jorgel on 2008-01-21
Can somebody else help, please!!!

---

### Post by Sami_Sdata on 2008-01-23
This link has some info on intel cards that might help.  Also, what does your xorg.conf look like?  It sound like you don't have any modes configured that work with you hardware combination.

[http://www.kubuntu.org/doc/7.10/hardware/C/video.html#intel](http://www.kubuntu.org/doc/7.10/hardware/C/video.html#intel)

---

