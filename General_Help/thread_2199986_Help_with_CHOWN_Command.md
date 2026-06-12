---
title: "Help with CHOWN Command"
date: 2014-01-17
forum: General Help
---

### Post by jay30 on 2014-01-17
I think I may have really messed something up with the chown command and need advice desperately.  I was installing wordpress on my machine and following some directions online. As per the instructions I downloaded wordpress, created the wordpress db and user and copied the wordpress files to the /var/www directory.  I was then supposed to give ownership of the directory to the apache user.  As per the instructions I executed the following command:

Sudo chown www-data:www-data * -R

unfortunately, I forgot to first change to the /var/www directory.  I therefore executed the command from the root directory.  Well, it took some time to complete and I did get several lines of feedback saying it couldn't perform action on certain directories/files.  However, I assume it must have done something.  I then changed to the /var/www directory and tried to execute the command again an received the message "sudo: /user/lib/sudo/sudoers.so must be owned by uid 0". Also, I am now unable to log into my machine.  What have I done?   Must be a nasty mistake on my part?

---

### Post by Vaphell on 2014-01-17
Yeah, it's pretty bad. 
You took all the system internals away from their owners (mostly root) and gave them to www-data. When your computer boots, the root account that is used to initialize everything has no permissions to run anything, to access/modify required files. It's easy to assume you won't get too far in the bootup process. Then your home dir is also owned by www-data.

I am not too familiar with such disasters and can't say if booting into live usb and switching everything in the system dirs on the harddrive back to root:root will fix things but i suspect it might not work, given there are these other users that are supposed to own subsets of the directory tree so even if your system gets up, you risk having all kinds of instabilities. I'd say backup & reinstall is in order but wait for opinions of more knowledgeable people.

---

### Post by tfrue on 2014-01-17
I agree with Vaphell, I would first back up all of your data, if you can, then simply re-install. This would probably be your best bet, at least in my opinion.

Chris

---

### Post by QIII on 2014-01-17
I usually don't recommend reinstalling as a first course of action -- I call that the "Blast off and nuke 'em from orbit" option -- but this is one case where that may be the best way to go.

Back up everything important, preserve your /home (if you have one) when you reinstall.

We've all done things like this.  If anyone tells you any different, they're lying.

---

### Post by jay30 on 2014-01-18
Thank you for everyone's quick response/advice.  In response to your suggestions I have now created a bootable USB with ubuntu 12.04.  I have confirmed it works as I have tried it on another computer.  When I plug it into the computer I messed up and boot from it I get the expected ubuntu startup screen but then after a while the screen goes gray and then eventually just flashes black/ light almost like it is trying to show the next screen but it can't. Could my previous error with CHOWN have done something to cause a problem with the video?

---

### Post by jay30 on 2014-01-18
When trying to boot from the USB I do get the purple screen, the ubuntu name and the red/white dots that indicate it is starting up. After a while a few text messages come onto the screen saying things like

"stopping CPU interrupts balancing" and "stopping system v run level"

Then the screen essentially goes to black and flashes with a bit of light every few seconds. This goes on forever.

---

### Post by tfrue on 2014-01-18
Is your laptop support UEFI, secure boot, and/or fastboot?

If so, disable them and try and boot to your CD again. Or Disable secure and fast boot and we can install Ubuntu UEFI, but first lets confirm that your computer supports it.

---

