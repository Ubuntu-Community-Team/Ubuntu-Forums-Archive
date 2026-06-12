---
title: "Loading and Boot problems"
date: 2013-03-26
forum: General Help
---

### Post by throese on 2013-03-26
1st start up: OS loaded up slowly and was sluggish when it finished. Used the power button to shut it off.

2nd start up: OS didn't load at all, stayed at the blinking line and I couldn't do ANYTHING because no matter what key combo I did, it would make weird characters.

3rd start up: Currently running memtest.

This is the first time EVER that it's done this.

Intel Core i5-2430 CPU @ 2.40GHz and 8099 MB of RAM, so, I SHOULDN'T be having these problems. =/

---

### Post by oldfred on 2013-03-26
You may have video issues.
       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

But forcing shutdown may have damaged file system. Always remember the elephants.
      
 Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by throese on 2013-03-26
I'll keep that REISUB method in mind, but my laptop is fixed now, since I did the memtest thing. Do you know what the command is to make the system do a system check?

---

### Post by Bashing-om on 2013-03-26
throese; Hi

 Glad you are up and running
To do a fs check on the next re-boot.
```
sudo touch /forcefsck
sudo shutdown -r now
```[INDENT]no subbing for experience !


[/INDENT]

---

### Post by oldfred on 2013-03-26
Bashing-om command sets system to run the same fsck that it typically runs every 40 or 60 reboots. It depends on the last parameter in fstab on what it runs.

A full e2fsck can be run from a liveCD also.

 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by throese on 2013-03-27
Thanks a lot everyone. It works fine now. =)

---

### Post by Bashing-om on 2013-03-28
throese;

All is good. Please exercise your consideration and mark this thread as "solved" :
interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
Problem still ? -> graphical instruction:==>[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)[INDENT=2]
ain't ubuntu wonderful

[/INDENT]

---

