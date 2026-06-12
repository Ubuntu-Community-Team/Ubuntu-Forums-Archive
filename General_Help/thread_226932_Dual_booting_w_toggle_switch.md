---
title: "Dual booting w/ toggle switch"
date: 2006-07-31
forum: General Help
---

### Post by ductapensuperglu on 2006-07-31
I've been playing around with xubuntu on an old system and I want to put full blown ubuntu on my main rig. I tried dual booting with grub a long time ago it ended in a big mess. So I want to install ubuntu on an old 30GB HDD I have laying around and leave windows xp on my new 80GB alone......%100 alone. My system has 2 7200rpm 80GB WD drives and a DVD-R/RW. One for XP, programs, Docs and the other is back-up and bulk storage. I want to put my back-up/storage drive as a slave under my DVD. Then I want to install the 30GB ubuntu drive as a slave to my 80GB XP drive. Then I will remove the jumper from the xp and set up the ubuntu with a jumper and toggle switch. So it works like this:

Switch on = ubuntu master / XP slave (so Ubuntu boots)
Switch off = ubuntu slave / XP master (so XP boots)

During the actual install I will completly disconnect xp so ubuntu or grub doesnt know about it until ubuntu is installed and running. 

I have three questions about this setup.

With a setup like this will ubuntu or xp conflict with each other?
Would I have to go out of my way to hurt XP with ubuntu?
Will ubuntu be able to read from my back up/storage drive?

Thank you very much in advance.

---

### Post by VonBraun on 2006-08-01
[LIST=1]
[*]That should work if the boot order is determined by the drives' master/slave status on the IDE bus.  It is however a very duct tape and super glue way to do this ;).
[*]The only time you can really hurt XP with ubuntu is with the drive partitioner during setup, but your suggested way of installing should prevent that.
[*]Ubuntu can mount the backup drive as read only if it's NTFS and read/write if it's FAT. IT should automatically do this as long as you leave it connected during setup.
[/LIST]

If you feel comfortable with the partioning tool in the Ubuntu setup, I'd suggest giving grub another try.  As long as you don't overwrite the XP partition you can always get your machine back by running the XP install CD and chosing the repair option.

During install, Ubuntu should automatically recognize XP and add it to the grub menu.  It's easy to see the XP partition because it should be an NTFS type partition.

---

### Post by confused57 on 2006-08-01
Here's an option that doesn't install grub to Windows mbr:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by ductapensuperglu on 2006-08-01
Thank you for helping me out. 

"During install, Ubuntu should automatically recognize XP and add it to the grub menu."

I'm never letting Grub anywhere near my precious XP drive again :) I like this ductape method better since I dont have to install any boot loaders or edit any files on my new drive. I have been thru master boot record hell and I ain't going back. I tried fixmbr, fresh install of either OS, or WD HD tools nothing will give me back my mbr on my storage/back-up drive. To this day if I unplug my XP drive and hook of the slave as a master I will get "GRUB Error 17".

If it comes down to it I'll physically remove the xp drive when i want to use ubuntu lol. (not really I'd just unplug the power and ide)

********************************
EDIT
*********************************
> **confused57 said:**
> Here's an option that doesn't install grub to Windows mbr:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

That scares me :(

---

### Post by confused57 on 2006-08-01
I have 2 computers set up the way I described and it scared me too at first, I wasn't comfortable using the CLI in terminal.
If you set up your Ubuntu as master and Windows as slave on the same IDE channel, all you would have to do is add the Windows entry for booting grub to Ubuntu(again, as described in the thread).
Unless you mounted the Windows drive in Ubuntu, there's practically no way you would affect the Windows install in any way experimenting with getting Windows to boot...worst that could happen(not likely though) is render Ubuntu unbootable, which would require reinstalling Ubuntu(do it with the Windows drive disconnected and your Windows would be safe).  Using this method, it would probably be necessary to install Ubuntu on your drive connected as master drive(may be the reason for the grub 17 error).
It's your system and decision, but it works really well for me.

I don't want to recommend anything to anyone they're not comfortable with, sounds like your toggle method works well.  After you get more proficient with Ubuntu, you may want to try something else, such as installing grub to a floppy...without floppy you'd boot to Windows, with floppy in during bootup, you boot to Ubuntu.

---

### Post by ductapensuperglu on 2006-08-01
Thank you guys for your help. I really like the idea of using a floppy to boot into ubuntu. But I aready installed ubuntu :), infact I'm typing this on ubuntu! 

EDIT* I saw this thread so i deleted my question. Thank you guys again!

[http://www.ubuntuforums.org/showthread.php?t=22561](http://www.ubuntuforums.org/showthread.php?t=22561)

---

