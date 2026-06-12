---
title: "Black Screen after recovery mode GRUB"
date: 2012-12-05
forum: General Help
---

### Post by gimchicoffee on 2012-12-05
Please help.. I've been using ubuntu 11.10 for a year or more now and have never had a problem this bad. I have tried all day to follow instructions on line but to no avail.

I had a game freeze in wine this morning and manually restarted my computer, when it turned on again it would go to bios screen, then ubuntu purple screen with dots underneath for a split second and go to black.

the black screen stayed, i left it on for 30 minutes once and nothing happened. i thought it was an ATI problem because i was fiddling with that in wine a while ago (but not even the day before the problem) and help for this problem suggested an ATI glfrx issue.

i have used nomodeset and recovery mode finally but it doesn't work. so now i can get to GRUB at least, but honestly dont know what the problem is.

i have important files i dont want to install over... what can the problem be? is there a surefire way to start it up so i can rescue my files? 

sorry this is very long.

---

### Post by gimchicoffee on 2012-12-05
here is the boot-repair output, it says successfully repaired but it is still a black screen with no command line or anything

[http://paste.ubuntu.com/1413058/](http://paste.ubuntu.com/1413058/)

---

### Post by oldfred on 2012-12-05
Boot-Repair is not showing any issues.

But you have a lot of kernels and you show system at 94% used. Time to houseclean once you get back in. 

If you did a hard shutdown, you may need to run fsck to repair file system.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

    
Best to remember the elephants when shutting down.Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
 R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by gimchicoffee on 2012-12-05
Thanks for the advice, I tried it and it didn't work. Yes, I really ought to avoid hard resets, a bad habit of mine...

How can I diagnose the problem? I am not too skilled at ubuntu, but can follow instructions for terminal and can get into livecd

forgot to mention im running a toshiba L655 satellite laptop with an ATI videocard

---

### Post by oldfred on 2012-12-05
If fsck did not work I am not sure what issue is.

It seems like it starts to boot, so can you from LIveCD/DVD/Flash check logs?

Logs are in /var/log and I would look at dmesg.
From liveCD:
       sudo mount /dev/sda1 /mnt
cat /mnt/var/log/dmesg
or 
sudo gedit /mnt/var/log/dmesg

If it is video I do not know ATI/AMD as I have nVidia.

---

### Post by YannBuntu on 2012-12-06
Hello

> **gimchicoffee said:**
> manually restarted my computer, when it turned on again it would go to bios screen, then ubuntu purple screen with dots underneath for a split second and go to black.
(..)
i have used nomodeset and recovery mode finally but it doesn't work. so now i can get to GRUB at least, but honestly dont know what the problem is.

i have important files i dont want to install over... what can the problem be?

Probably broken system files.
I would recommend:
1) first backup your documents on an external disc (or DVDs)
2) fix your system files via an UBuntu disc this way: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

### Post by gimchicoffee on 2012-12-06
thans both of you. oldfred, sorry i didn't get to try the method you recommended so i'm not sure if it would work or not...

i was looking for the possibility of a system repair and the upgrade trick worked thanks!

it said upgrade 11.10 to 11.10. if anyone reads this please note that the upgrade took HOURS however

---

