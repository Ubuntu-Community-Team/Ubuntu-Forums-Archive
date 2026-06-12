---
title: "edgy - fsck / dosfsck on every boot (tune2fs does nothing)"
date: 2006-11-29
forum: General Help
---

### Post by crash369 on 2006-11-29
Hello all

I have been searching the forums and web and it seems I'm not the only one who has the problem of Edgy running fsck on every boot.  I have done everything suggested (basically running tune2fs), but the fsck's continue.

Here's the pertinent info:

/etc/fstab
```
# /dev/hdb1
UUID=5e923e47-e037-46cd-881f-6ad2db3fe036 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb2
UUID=2fa36361-2e16-4984-8506-d83bec130cde /var            ext3    defaults        0       2
# /dev/hdb3
UUID=ab0c63bf-6d10-4fcf-ad74-fc1375949414 /home           ext3    defaults        0       2
```

I do not want to set the check-drive bits to 0, because I _do_ want fsck to run occasionally.  I also have a couple vfat/ntfs drives that had 1s and 2s, but I changed those to 0, because the dosfsck was also running on every boot, and it's painfully slow.  Ideally, I would like to put those back to 1s and 2s, so that those drives also get checked periodically.

here is some tune2fs output:

```
crash@asylum:~$ sudo tune2fs -l /dev/hdb1
...
Last mount time:          Wed Nov 29 22:31:23 2006
Mount count:              8
Maximum mount count:      30
...

```

the other ext3 drives are also set to 30.

The fstab trick and tune2fs were the only solutions to this problem that I have found, and they do not work.  Any other ideas?

Thanks in advance
~crash

---

### Post by dubrict on 2006-11-30
I just want to let you know you're not alone, I'm having the same problem.  If I run fsck on each of the drives manually there's no errors.  But how do I set it not to check automatically like you talk about?  I don't mind just doing it myself from time to time...

---

### Post by crash369 on 2006-11-30
> **dubrict said:**
> But how do I set it not to check automatically like you talk about?

dubrict, edit your /etc/fstab file.  Set the digit in the last column to 0 for every drive you do NOT want checked.

This is what my fstab would look like (compare with one above)

```
# /dev/hdb1
UUID=5e923e47-e037-46cd-881f-6ad2db3fe036 /               ext3    defaults,errors=remount-ro 0       **0**
# /dev/hdb2
UUID=2fa36361-2e16-4984-8506-d83bec130cde /var            ext3    defaults        0       **0**
# /dev/hdb3
UUID=ab0c63bf-6d10-4fcf-ad74-fc1375949414 /home           ext3    defaults        0       **0**
```

---

### Post by dubrict on 2006-11-30
great, thanks!
As for what the problem is, I think it has to do with fsck trying to check the vfat filesystems with the wrong utility.  I also have a partition formatted as fat32.  From the output in the log /var/log/fsck/checkfs, it looked like it was checking the vfat filesystem as if it was an ext3.  Normally, if you run fsck /dev/*the_vfat_drive,* it will automatically detect the filesystem and use ckfs.vfat to check it.

The only problem with this theory is that if you try running "ckfs.ext3 /dev/*fat32drive,* it will give you a warning about checking the wrong filesystem and ask if you'd like to continue.

---

### Post by crash369 on 2006-11-30
That does not sound right to me.  Before I turned fsck off in /etc/fstab, it would check my vfat/ntfs drives with dosfsck.  It's definitely only checking ext3 drives now.

---

### Post by handaxe on 2006-12-07
A known bug it seems, but not assigned or officially acknowledged yet.

[https://launchpad.net/distros/ubuntu/+source/e2fsprogs/+bug/63175](https://launchpad.net/distros/ubuntu/+source/e2fsprogs/+bug/63175)

Try this perhaps?

[http://ubuntuforums.org/showthread.php?t=295262](http://ubuntuforums.org/showthread.php?t=295262)

HA

---

### Post by kapilg_it on 2006-12-07
> **crash369 said:**
> Hello all

I have been searching the forums and web and it seems I'm not the only one who has the problem of Edgy running fsck on every boot.  I have done everything suggested (basically running tune2fs), but the fsck's continue.

Here's the pertinent info:

/etc/fstab
```
# /dev/hdb1
UUID=5e923e47-e037-46cd-881f-6ad2db3fe036 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb2
UUID=2fa36361-2e16-4984-8506-d83bec130cde /var            ext3    defaults        0       2
# /dev/hdb3
UUID=ab0c63bf-6d10-4fcf-ad74-fc1375949414 /home           ext3    defaults        0       2
```

I do not want to set the check-drive bits to 0, because I _do_ want fsck to run occasionally.  I also have a couple vfat/ntfs drives that had 1s and 2s, but I changed those to 0, because the dosfsck was also running on every boot, and it's painfully slow.  Ideally, I would like to put those back to 1s and 2s, so that those drives also get checked periodically.

here is some tune2fs output:

```
crash@asylum:~$ sudo tune2fs -l /dev/hdb1
...
Last mount time:          Wed Nov 29 22:31:23 2006
Mount count:              8
Maximum mount count:      30
...

```

the other ext3 drives are also set to 30.

The fstab trick and tune2fs were the only solutions to this problem that I have found, and they do not work.  Any other ideas?

Thanks in advance
~crash

if you are not using a laptop then read:rolleyes: 
I make out a way for me that worked fine till now , Here it is:

go to /usr/bin
make backup $ cp on_ac_power on_ac_power.bak
then edit the last line which says exit 255 
change it to exit 1

reason
/etc/init.d/chechroot.sh checks this exit status of this file to determine id machine is on battery power ( intelligent).
you can revert the changes for checking to follow next time you boot:p :-D

---

### Post by crash369 on 2006-12-13
Tried bonager... it doesn't do anything -- fsck still runs every boot.
oh well, i guess i'll wait for a fix =/


> **handaxe said:**
> A known bug it seems, but not assigned or officially acknowledged yet.

[https://launchpad.net/distros/ubuntu/+source/e2fsprogs/+bug/63175](https://launchpad.net/distros/ubuntu/+source/e2fsprogs/+bug/63175)

Try this perhaps?

[http://ubuntuforums.org/showthread.php?t=295262](http://ubuntuforums.org/showthread.php?t=295262)

HA

---

### Post by kapilg_it on 2006-12-13
try changing exit status of /usr/bin/on_ac_power
just write "exit 1" uncommented in the first line to avoid disk checking
remove this line when you want to force check it;)

---

### Post by dubrict on 2006-12-13
in my /etc/fstab file, I had to change all those "UUID" numbers to the /dev/sda# of the hard drives they all represented.  I had a problem where I guess the UUID number was wrong and it didn't like it, so it checked the disk everytime it started.

---

### Post by crash369 on 2006-12-13
i think editing /etc/fstab is a much easier way to stop fsck altogether.  however, i want it on and checking at intervals =/

thanks for the idea though

~D

> **kapilg_it said:**
> try changing exit status of /usr/bin/on_ac_power
just write "exit 1" uncommented in the first line to avoid disk checking
remove this line when you want to force check it;)

---

### Post by ciscosurfer on 2006-12-13
Not sure if this has already been addressed, but you should boot into Windows (fully), and then reboot (as gracefully as XP does)...then boot into Ubuntu to see if that works.

---

### Post by crash369 on 2006-12-13
tried that too... no go =/

> **dubrict said:**
> in my /etc/fstab file, I had to change all those "UUID" numbers to the /dev/sda# of the hard drives they all represented.  I had a problem where I guess the UUID number was wrong and it didn't like it, so it checked the disk everytime it started.

---

### Post by crash369 on 2006-12-13
nope, done that a few times (just booting in and out of winblows) -- doesn't help


> **ciscosurfer said:**
> Not sure if this has already been addressed, but you should boot into Windows (fully), and then reboot (as gracefully as XP does)...then boot into Ubuntu to see if that works.

---

### Post by kapilg_it on 2006-12-14
[SIZE=4]perhaps this will help you [/SIZE]
[http://ubuntuforums.org/showthread.php?t=295262](http://ubuntuforums.org/showthread.php?t=295262)

---

### Post by RyanGT on 2007-03-06
I was having the same problem.  Getting rid of the UUID's and replacing them with /dev/sda# didn't help and neither did booting into Windows and back.  Changing the last column of fstab to 0 for all fat partitions did help, but is there another solution?  I would like fsck to run on my dos partitions occasionally.  Can this be done with cron or something?  Does it have to be done during boot up or can dosfsck do its thing after the partition is mounted?  (I guess the cron job could unmount the partition, maybe.)

Thanks,

Ryan

---

### Post by Malac on 2007-03-06
The file that does the check is checkfs.sh in /etc/init.d/ just move it somewhere safe and set a cron job to copy it back to /etc/init.d/ every x days and delete it one day after.

---

