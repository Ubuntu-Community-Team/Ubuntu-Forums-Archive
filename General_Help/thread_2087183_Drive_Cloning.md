---
title: "Drive Cloning"
date: 2012-11-23
forum: General Help
---

### Post by iowabeakster on 2012-11-23
I am going to be moving to a larger drive shortly.  I have read plenty about how to do this (simple enough use dd).

I understand that after the cloning process is done, I will need to disconnect the old drive or grub is going to get confused with identical UUIDs.

But if right after the cloning process is done...

If I were to run the program "boot repair", would it recognize the issue and change the UUIDs in /etc/fstab and /boot/grub/grub.cfg so that both drives could be still be installed at the same time?

---

### Post by ibjsb4 on 2012-11-23
Wouldn't that be sweet.

Not that hard to manually change uuid, but click and go.  I love the idea.

Why don't you post the idea in his thread and see what happens?

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Also, nothing wrong with DD but have you checked out clonezilla?

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by iowabeakster on 2012-11-23
Thanks for the response.

Yes, as I have been reading up on the process of disk cloning, I have seen Clonezilla in numerous discussions.  

But it didn't seem to do anything other than what dd does (at least for what I was doing).  Since I would be doing all this cloning business from a "live usb" drive, and I want to change UUIDs afterward, I should probably do it from an Ubuntu Live usb.  I only have 1 usb thumb drive.  An ubuntu live usb would allow me the use of dd, gparted, and hopefully boot-repair also, all from the same usb drive at the same time.

I would use Clonezilla... if it had the option to change UUIDs after the cloning is complete.

I will post my question on the boot-repair thread... right now...

---

### Post by oldfred on 2012-11-23
I posted a response in the Boot-Repair thread, wish I posted here. But will not move it now unless you want it moved.

 I also am not a fan of dd.

       Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

   from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)
[http://www.anti-forensics.com/disk-wiping-with-dcfldd](http://www.anti-forensics.com/disk-wiping-with-dcfldd)

---

### Post by iowabeakster on 2012-11-25
Yep, I read your comments in the boot-repair thread, also.

Thanks guys.  I really appreciate the advice.

I am now reconsidering my options.

---

