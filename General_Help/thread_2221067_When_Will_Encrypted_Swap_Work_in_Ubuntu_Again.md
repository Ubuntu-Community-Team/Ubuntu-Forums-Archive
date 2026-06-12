---
title: "When Will Encrypted Swap Work in Ubuntu Again?"
date: 2014-04-30
forum: General Help
---

### Post by taytaybongsong on 2014-04-30
Encrypted swap does not work in Ubuntu Trusty, or apparently, any of the Ubuntu flavors. I had an encrypted swap partition under Xubuntu 13.10, and when I upgraded to 14.04, it was no longer recognized or utilized (luckily I made backups with deja-dup, Timeshift and Aptik, so I just rolled back to 13.10). I thought maybe I should revert to using an unencrypted swap partition, so I carefully followed the instructions to 'decrypt' one's swap partition here; [http://www.logilab.org/blogentry/29155](http://www.logilab.org/blogentry/29155) and then proceeded to upgrade again. All went well, but when I tried to manually encrypt my swap partition after the upgrade (using "sudo ecryptfs-setup-swap"), it was no longer recognized or utilized just like before, so I rolled back to 13.10 again, and re-encrypted my swap partition (which works perfectly under 13.10). Then I got to thinking that maybe I should start fresh. I de-encrypted my swap partition again, and did a fresh install of Xubuntu 14.04, choosing to erase my previous installation and start from scratch. Everything went well, until I attempted to encrypt my swap partition and reboot. Again, it was not recognized or utilized by Xubuntu. I thought maybe it was a Xubuntu-specific issue, so I de-encrypted my non-working swap partition, made sure it was working as regular swap space, and did a fresh install of plain Ubuntu 14.04, ending up back where I started. Even plain ol' Ubuntu could not recognize or utilize encrypted swap space, only normal swap space. I tried with Kubuntu 14.04 and experienced the same. One of the aforementioned installs was done with 'Encrypt My Home Folder' selected, which also encrypts your swap partition. Even this didn't work (well, my home folder was encrypted, but again, my encrypted swap partition was unusable).

So, now I'm back on Xubuntu 13.10 again, with a working encrypted swap partition, but I know I'll eventually have to upgrade If I want to continue getting updates. Can anyone tell me if this bug will be fixed? Has anyone else realized that Ubuntu Trusty is incapable of utilizing an encrypted swap partition? This is a serious security issue and I can't believe it has not beed fixed yet.

TLDR: Encrypted swap partitions are not recognized/utilized by Ubuntu 14.04 and its derivatives, but they work perfectly under 13.10. Whether one chooses to manually encrypt their swap partition after install with ecryptfs, or during install by way of opting to have their home folder encrypted, makes no difference.

---

### Post by taytaybongsong on 2014-04-30
It seems that there are at-least a few bug reports about this issue here:
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1301383](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1301383)
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1313230](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1313230)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1303002](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1303002)

Yet all the ones effecting Trusty are not marked as being of High importance. Encrypted swap is important to a lot of security-minded users like myself, and is arguably more crucial than encrypted home, in that the contents of encrypted files (in password management applications and the like) can be leaked to disk in human-readable format, if one's swap is unencrypted. Basically, having unencrypted swap space, greatly reduces the effectiveness of having an encrypted home folder. I am not posting this to bump my thread, but simply because this is an issue anyone concerned about privacy and security should be aware of. As it currently stands, if you want or need a swap partition on the latest Ubuntu release, you have but one choice; an unencrypted one.

---

### Post by AlbertP on 2014-05-23
If I change the UUID into a /dev/sdXY in /etc/crypttab, the swap is again working as it did on 13.10. It looks like the system fails to read the encrypted swap's UUID on boot with 14.04.

---

### Post by AlbertP on 2014-05-23
At [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058) comment #3 is a possible fix. Would be nice if users could test his fix. I hope to do so tomorrow.

---

### Post by obake2 on 2014-07-15
[Ubuntu 14.04.**1** ]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule")is coming soon yet there doesn't seem to be any progress in fixing this bug. I hope with all my might that this bug gets fixed on time. 

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

That bug should be marked "CRITICAL" not "High".


I hope that, just maybe, by bumping this thread someone knowledgeable will be see that there is a great need to fix this bug ASAP.

---

### Post by sudodus on 2014-07-15
Developers seldom read threads at the Ubuntu Forums. But they read bug reports at ***Launchpad***, and they are often logged in at **IRC**. You can also make them notice your issue by engaging in iso testing at

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

---

### Post by thatsmyboy on 2014-07-28
I just returned to Ubuntu after a long time in the mostly windows world. I had the option to pursue encryption for /home and full disk and decided to give it a try. It seems like this issue is also plagueing me on Ubuntu-Gnome 14.04.1 Looking forward to a resolution.

---

### Post by obake2 on 2014-08-07
Hi myboy. Here is a solution to that bug:

[http://ubuntuforums.org/showthread.php?t=2224129](http://ubuntuforums.org/showthread.php?t=2224129)

---

### Post by StewartM on 2014-08-24
> Hi myboy. Here is a solution to that bug:

[http://ubuntuforums.org/showthread.php?t=2224129](http://ubuntuforums.org/showthread.php?t=2224129)

Didn't work for me. After:

umount /dev/sda2 #(my swap partition)

I get the error that it's not mounted.

Then after:

mkswap /dev/sda2 

I get the error that it's busy. 

So how can my swap partition be unmounted and yet busy at the same time?? :confused:

I did find out that during the install even though sda2 was recognized as swap during the install, it wasn't recognized as such when I rebooted from a live CD. I then reformatted it in GRUB then and tried the steps in your link. Still same error message.

---

### Post by StewartM on 2014-08-24
> TLDR: Encrypted swap partitions are not recognized/utilized by Ubuntu 14.04 and its derivatives, but they work perfectly under 13.10. Whether one chooses to manually encrypt their swap partition after install with ecryptfs, or during install by way of opting to have their home folder encrypted, makes no difference. 

Luckily, for me, I have enough RAM so that losing swap is a better option than having an unencrypted swap. The latter of course defeats the purpose of having an encrypted /home directory to begin with. After trying the fix that didn't fix it, I guess I'll await 14.04.2, but it's frustrating that this something that once again this is a feature that used to upgrade flawlessly in Ubuntu that no longer does.

---

### Post by sudodus on 2015-03-06
> **AlbertP said:**
> At [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058) comment #3 is a possible fix. Would be nice if users could test his fix. I hope to do so tomorrow.

This works for me (comment #3 in that bug report), when fixed before creating the cryptswap

***If it is used for repair, some other steps are necessary*** - 

1. re-make the swap partition into a regular swap partition with ***mkswap***
2. match its UUID with **/etc/fstab**,
3. and then run ***ecryptfs-setup-swap***.

After that cryptswap survives reboots.

[HR][/HR]Anyway, everybody who is affected by the bug, please browse to it and click on [[COLOR=#006400]This bug affects around 100 people. Does this bug affect you?[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058/+affectsmetoo") :-) Every new user (who is affected by it) increases the chance that the bug will get priority and get squashed.

You can also ***write a comment*** (tell them if you could use a work-around). It will also make a difference, probably bigger than only clicking 'that it affects you'.

[HR][/HR]
**Warning: the following method is neither convenient nor safe** - long  commands must be typed into a text screen, and those commands will  overwrite the partition table. But if you really want both kinds of  encryption it might be worth the effort, and if you have only one drive  in the computer (except the installer on CD/DVD/USB) you can relax [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG][I][B]

Lubuntu alternate installer - with some tweaks is it possible to install a system with 'encrypted disk' and 'encrypted home'[/B][/I]

When the alternate installer has started, at the screen 'Set up users and passwords', it is time to modify the partition table.
[B][I]
ctrl+alt+F2[/I][/B]

Check drives and partitions:

```
blkid
df
```

***Unmount*** if a partition in the target drive is mounted:

```
[SIZE=3]umount /dev/sdxy[/SIZE]
```

where x is a for the first drive and y is 1 for the first partition, typically /dev/sda1

***Change*** the partition table:

```
[SIZE=3]wget http://phillw.net/isos/linux-tools/small-images/msdos-part-tbl.img

dd if=/dev/zero of=/dev/sdx bs=1024 count=1024  # wipe first Mibibyte

dd if=msdos-part-tbl.img of=/dev/sdx  # MSDOS partition table, no partition

blkid -c /dev/null  # check that it was successful[/SIZE]
```

***ctrl+alt+F1***

and continue with the installer!
...
...
...
Install the bootloader ... answer ***No***
and select it manually

**/dev/sdx**

where x is the drive letter, where you want to install the bootloader, often the same drive as you installed Lubuntu, typically a (/dev/sda)

and continue. It is close to the finish now.
...

[HR][/HR]
With the additional commands above, encryption works including encrypted disk with LVM and encrypted home with cryptswap. But it seems encrypted swap works only during the first session of the installed system. After only a simple reboot cryptswap does not survive, but it is possible to create a 'normal' swap system using the LVM-mapped swap, and it survives update/upgrade and reboots. This swap is subject to disk encryption so reasonably safe except for other users with their own user ID in the same computer.


[HR][/HR][I][B]
This creates 'normal swap inside the encrypted disk'[/B][/I]

Identify the swap mapper and use it with mkswap. I used the computer name altLubuCrypt, which is part of the swap mapper device name.
```
sudo blkid
sudo mkswap /dev/mapper/altLubuCrypt--vg-swap_1
```

and point to it by swapping the comment marks in /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/altLubuCrypt--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=dc48c7d3-53fe-4d73-b1e2-ac9e99f923ad /boot           ext2    defaults        0       2
/dev/mapper/altLubuCrypt--vg-swap_1 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
```

[HR][/HR]
***This creates encrypted swap*** and protects against other users with their own user ID in the same computer.

There is a fix, that can make the installed cryptswap survive. You must [COLOR=#ff0000]***do it the first time you start the installed system***[/COLOR], that is while cryptswap is still alive.

Add the option offset=8 to the file /etc/crypttab:


```
[SIZE=3]sudo sed -i s/,cipher=/,offset=8,cipher=/ /etc/crypttab[/SIZE]
```

---

### Post by sudodus on 2015-03-07
Don't get me wrong. I read the bug report [https://bugs.launchpad.net/ubuntu/+s...s/+bug/1310058]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058"), and I see that there are many comments that point forward to squashing the bug.

The previous post describes a work-around method that works today with Lubuntu Vivid. It does not contain what will be used to squash the bug.

---

