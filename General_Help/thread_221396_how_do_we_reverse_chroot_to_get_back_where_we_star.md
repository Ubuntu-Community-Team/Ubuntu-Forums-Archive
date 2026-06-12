---
title: "how do we reverse chroot to get back where we started?"
date: 2006-07-23
forum: General Help
---

### Post by Herman on 2006-07-23
I'm trying to find a way to install LiLo to the first sector of a Ubuntu partition as a secondary way of booting for those who have some problem with GRUB that can't easily be solved right away. (So Lilo an be chainloaded from GAG Boot Manager until the grub problem is solved, if it can be.)
I already know how to install Lilo to a partition with the 'Alternate' CD, now I want to learn how to do this from the Live CD.
So far, I have done this:```
ubuntu@ubuntu:~$ sudo parted /dev/hda
Password:
parted> print
parted> set
parted> boot
parted> on
parted> quit
ubuntu@ubuntu:~$ exit
``` That's to set the boot flag first.
Next, I did this,
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
Password:
ubuntu@ubuntu:~$ sudo mount /dev/hda2 /mnt/ubuntu/
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/ubuntu/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev/ /mnt/ubuntu/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/ubuntu /bin/bash
root@ubuntu:/# apt-get install lilo #only if lilo has never been installed in the system before

root@ubuntu:/# lilo -b /dev/hda2
Ignoring entry 'boot'
Warning: '/proc/partitions' does not match '/dev' directory structure.
        Name change: '/dev/dm-0' -> 'dev/ems/hda1'
Warning: Partition 2 on /dev/hda is not marked Active.
Warning: boot record relocation beyond BPB is necessary: /dev/hda2
Warning: Unable to determine video adapter in use in the present system.
Warning: Video adapter does not support VESA BIOS extensions need for
      display of 256 colocrs. Boot loader will fall back to TEXT only operation.
Added Lin_2.6.15img0 *
Added Lin_2.6.15img1
Added Memory_Test+
root@ubuntu:/#
``` 
Now, the problem is, how to 'un-chroot' back to just a regular terminal again, so I can umount the stuff I have mounted and exit elegantly and gracefully.
Actually, what I did was open another terminal and umount the second two things I had mounted, but I got 'device busy' and couldn't umount the partition I was chrooted in.
All I did was close the terminal and re-boot, everything worked fine, Lilo was installed where I want it. It doesn't seem to me like the correct way to close out and exit though.
Is there a way to reverse the chroot command so I can get back to a regular terminal before umounting and exiting?

Should I worry about it or am I just being too fussy?

Many thanks, Herman :D

---

### Post by SkyNet2029 on 2006-07-23
On my Debian chroot install, what I did was 
```
#exit
```
OR
```
logout
```
and it dumped me back to the initial terminal, allowng a graceful umount of my working chroot environment, since I was no longer actively using it. I ended up doing that out of not knowing or finding another method. (Other than just nuking the terminal I mean.) Either way I didn't see a real difference when rebooting, although I am sure (hoping I suppose) that just crashing a terminal is not the preffered way to go.
Is this what you were meaning?
edit: from what I have read on this, you do need to exit gracefully from chroot so as to avoid fsck barfing up a plethora of errors at reboot into new system.

---

### Post by Herman on 2006-07-23
> Is this what you were meaning?
 edit: from what I have read on this, you do need to exit gracefully from chroot so as to avoid fsck barfing up a plethora of errors at reboot into new system
Yes, SkyNet2029, that is exactly  what I mean. Thanks for your help. I'm pretty sure I tried 'exit' and 'quit', but I didn't think of 'logout'. I'll try 'logout' and the other two again as well just to make sure.
I didn't get any errors with fsck this time, but next time I might not be so lucky. I'd like to learn how to do this this right way.
I've been doing some searching, funny thing I've seen lots of advice telling people to chroot for various reasons, but not one how-to I have seen so far mentions anything about how to exit it. Thanks again. I will try those. Thanks very much for your reply.
All the best, Regards, Herman :D

---

### Post by Herman on 2006-07-23
SkyNet2029, many thanks again, 'exit' works! I sure appreciate your help, I thought I tried that too, well now that that's solved I'll be able to sleep a lot better! :D 
All the best, Regards, Herman :D

---

### Post by steve.horsley on 2006-07-23
You can install GRUB on your Ubuntu partition if you want. That's what I have started doing. E.g. **sudo grub-install /dev/hda5**, after which hda5 can be chainloaded by any old make of master bootloader.

---

### Post by Herman on 2006-07-24
Hello , steve.horsley, Thank you. I agree with you, that suggestion is easier and better. :D
I still want to learn this method to install Lilo to an (unbootable) operating system form a Live CD anyway though. There's a method to my madness. I'm trying to find more ways to recover operating systems that are having a lot of trouble booting with GRUB. After someone has already tried quite a few possible solutions for fixing Grub, and have still not had any success, maybe the operating system is just not bootable. Maybe it is a GRUB problem that is still being overlooked. If they can boot by an alternative bootloader, that might help to sort out where the problem is. 
Actually, it's easier to install Lilo from the 'Alternate' CD 'Rescue a Broken System' mode, but not everyone has a copy of the 'Alternate' CD, they might only have the 'Desktop' one.
All the best, Regards, herman :D

---

