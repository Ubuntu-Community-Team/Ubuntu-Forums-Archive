---
title: "Upgrade Wubi to a dedicated partition"
date: 2008-05-20
forum: General Help
---

### Post by ago on 2008-05-20
Waiting for [LVPM](http://lubi.sourceforge.net/lvpm.html) to support 8.04, I have created this small script to fill the gap. It should do the work anyway and transform a Wubi installation into an installation to a dedicated partition identical to one you would get from a CD installation (or at least this is the plan :) ). The script should be considered alpha quality.

[list=1]
[*] Create 2 empty partitions, one for the operating system (larger than 5GB) and one for swap (larger than your memory size). You can reuse an existing swap partition, or skip it alltogether (the swap partition is optional). You can use gparted or any other tool you fancy to create the partitions.
[*] Download [https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=wubi-move-to-partition](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=wubi-move-to-partition)
[*] Open a terminal, go to the directory where you downloaded the script above and run:

```
sudo sh wubi-move-to-partition /dev/sda9 /dev/sda10
```

Replacing /dev/sda9 with the partition where you would like to migrate the Wubi installation to, and /dev/sda10 with the appropriate swap partition (you can omit the second argument completely, in which case no swap will be setup).[/list] 

Note that since the script is supposed to behave as a real installation it will install grub as main bootloader replacing the existing bootloader in the MBR of the disk where you installed Wubi and in the first HD.

If things do not work as expected you will have to boot from a Live CD and replace/edit the bootloader manually (via install-grub or windows rescue console). 

Known issues: if you have multiple hard-disks, the disk order might have to be adjusted manually in /boot/grub/menu.lst.

---

### Post by sundoulos on 2008-10-16
Does the dedicated partition need to have the boot flag set?

---

### Post by ago on 2008-10-16
> **sundoulos said:**
> Does the dedicated partition need to have the boot flag set?
No the boot flag is only used by windows

---

### Post by Visdev on 2008-12-01
I have tried to use this script, but it is not working for me.  I've created the partition and downloaded the script.  But when I try to run it, I get a message telling me that the partition is in use, even though it is unmounted.  What am I missing here?

Heres how my terminal reads:

visceral@ubuntu:~/Desktop$ sudo sh wubi-move-to-partition /dev/sdb2
Sanity checks...
Volume /dev/sdb2 is in use. Aborting

Thanks for any help you can give me!

---

### Post by Jammanuser on 2008-12-02
is there a way to upgrade ur Wubi installation, even when u can't boot into ubuntu, possibly from a Ubuntu Desktop CD??? i keep getting a stupid crc error every time i try to boot into ubuntu...nothing i've tried so far has worked! and BELIEVE me, i've tried a LOT! :) 

Looking forward to ur reply!

---

### Post by Jammanuser on 2008-12-02
is there a way to upgrade ur Wubi installation, even when u can't boot into ubuntu, possibly from a Ubuntu Desktop CD??? i keep getting a stupid crc error every time i try to boot into ubuntu...nothing i've tried so far has worked! and BELIEVE me, i've tried a LOT! :) 

Looking forward to ur reply! :lolflag:

---

### Post by ago on 2008-12-02
If you cannot boot into wubi, you can do a full installation from CD, from there you can mount the windows partition and /ubuntu/disks/root.disk therein and then copy any required file.

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

---

### Post by Jammanuser on 2008-12-02
> **ago said:**
> If you cannot boot into wubi, you can do a full installation from CD, from there you can mount the windows partition and /ubuntu/disks/root.disk therein and then copy any required file.

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

hmm...ok, good idea! :D what if i can't copy the files in wubi to ubuntu or Windows, due to not having permission to save the file? what then? 

:guitar:

i'm asking because i've already tried mounting wubi and copying my files from ubuntu into Windows, using the Ubuntu Desktop CD, but i got an error message saying that i didn't have permission to save the requested file, and so i couldn't copy it! 

Looking forward to ur reply... :D

---

### Post by Jammanuser on 2008-12-02
> **ago said:**
> If you cannot boot into wubi, you can do a full installation from CD, from there you can mount the windows partition and /ubuntu/disks/root.disk therein and then copy any required file.

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

hmm...ok, good idea! :D but what if i can't copy the files in wubi to ubuntu or Windows, due to not having permission to save the file? what then? 

:guitar:

i'm asking because i've already tried mounting wubi and copying my files from ubuntu into Windows, using the Ubuntu Desktop CD, but i got an error message saying that i didn't have permission to save the requested file, and so i couldn't copy it! 

Looking forward to ur reply... :D

---

### Post by Jammanuser on 2008-12-02
Whoa!!! sorry for the double post...i don't know what happened! when i pushed "submit reply", after typing my message, i got sent to the same page again, and so, thinking that it didn't work, i pushed "submit reply" again! :guitar:

;)

---

### Post by ago on 2008-12-03
> **Jammanuser said:**
> hmm...ok, good idea! :D what if i can't copy the files in wubi to ubuntu or Windows, due to not having permission to save the file? what then? 

:guitar:

i'm asking because i've already tried mounting wubi and copying my files from ubuntu into Windows, using the Ubuntu Desktop CD, but i got an error message saying that i didn't have permission to save the requested file, and so i couldn't copy it! 

Looking forward to ur reply... :D

You can use sudo to copy the file or better assign the current user ownership of the windows device when mounting (-o uid=1000)

---

### Post by Jammanuser on 2008-12-03
> **ago said:**
> You can use sudo to copy the file or better assign the current user ownership of the windows device when mounting (-o uid=1000)

yeah...never mind about that, now, ago! i've copied my files since then, as a root user! i got help for that from a different forum...

Thanks for replying though!

Cheers! :D

---

