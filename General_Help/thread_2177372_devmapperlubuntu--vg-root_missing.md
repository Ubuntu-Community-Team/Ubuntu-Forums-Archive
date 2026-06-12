---
title: "/dev/mapper/lubuntu--vg-root missing"
date: 2013-09-28
forum: General Help
---

### Post by marcelo6 on 2013-09-28
Hi,

Hopefully I'm posting in the right place. First post here. I'm fairly new to Linux overall so please bear with me. 

I've been using Lubuntu for a few months now. When setting up my machine, I pretty much did an auto install and used the encryption it provides (LVM, LUKS whatever). I recently updated and when I restarted, it failed to find /dev/mapper/lubuntu--vg-root and then dropped into a shell. I tried looking this problem up but there wasn't much on it, and I wasn't able to figure it out (hence me posting here). I booted from a live cd and was able to access the drive and it seems like /dev/mapper/lubuntu--vg-root is there when I look at it thru accessory>disks but when I look into the file system, only a file named 'control' is in that folder. I don't know. Is it failing to mount on startup? Was reading about UUID's and blah blah blah and didn't really get anywhere. It seems like it would be a simple fix tho. I have my home directory backed up so I guess if all else fails, I can just reinstall but would prefer not to. Any help would be very much appreciated!

---

### Post by oldfred on 2013-09-28
I do not know LVM. It adds a level of complexity as logical partitions over the physical partitions on the drive.

But Boot-Repair knows LVM better than I do and often works. You can just install it into your live version.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by marcelo6 on 2013-09-28
Ok...ran boot repair and first clicked on repair...said it resolved the issue but didn't. So here is the report...

[http://paste.ubuntu.com/6168149](http://paste.ubuntu.com/6168149)

Thanks for the help!

---

### Post by oldfred on 2013-09-28
Did you check separate /boot as you have sda1 as /boot partition.
And it was not able to mount encrypted partition. You have to give pass phase somewhere, but I do not know encryption.

---

### Post by marcelo6 on 2013-09-28
Not sure what you're asking. However, the system always worked before with sda1 being the boot partition and sda5 being the storage for everything else. Normally upon boot, it would show lubuntu logo with pass phrase prompt. Now, it just shows lubuntu logo loading and not prompting the pass phrase and then seconds later dropping into the shell. So yah, it seems to be not mounting the encrypted partition on startup. Thoughts?

---

### Post by oldfred on 2013-09-28
When running boot-Repair it may not know the LVM is encrypted. You may have to manually mount it, so it asks for passphase? And Boot-Repair has a separate check box for separate /boot that you must check off.

---

### Post by marcelo6 on 2013-09-28
Interestingly, it didn't have those options the first few times of running boot-repair. But after your post, it did show up as a RAID volume and provided those options. It asked to decrypt the volume before proceeding, which I do not know how to do and was unable to figure out. I saw in another post that you had replied to that you had never decrypted a volume ([http://ubuntuforums.org/showthread.php?t=2144910](http://ubuntuforums.org/showthread.php?t=2144910)) ...I tried proceeding anyway just to see if it could but it was unsuccessful. As much as I love problem solving and really wanted to solve this without taking the easy way out, I just don't have the time to do this... as a spec. ed teacher, I really should be working on so many other things right now :-(  ....I don't even know why I encrypted the volume in the first place. On my other lubuntu machine, I set up the volumes manually and did not use encryption and it's still working just fine. So I guess I'll just reinstall on that other machine. Thanks so much for your time and sorry if I'm being impatient...before I was a teacher, I would have spent weeks (if I had to) figuring out a problem like this. And really not sure why the problem occurred in the first place....very weird. Anyway, thanks again!

---

### Post by marcelo6 on 2013-09-28
Actually..... If you have more ideas, I will try them out. Not like I'm in a hurry to fix that machine. lol.

---

### Post by oldfred on 2013-09-28
When it asks about encryption does it not give you a chance to enter passphase? 
I think Boot-Repair has trouble telling RAID from LVM as both are mounted as /dev/mapper, so it may need a bit of help?

I wonder if grub installed with LVM may not always be configured to correctly reinstall? May be a bug?

---

### Post by marcelo6 on 2013-09-29
No, boot repair does not prompt for the passphrase...
Like I said, I'm pretty much a beginner to linux and you might as well assume I know nothing as I've never had a boot issue like this before.

---

### Post by oldfred on 2013-09-29
Do not know enough about encryption nor LVM to really be able to help. Hope someone who does comes along.

---

### Post by marcelo6 on 2013-09-29
Thanks for trying! At least I learned about boot repair and maybe that will help me to solve another issue in the future.

---

### Post by steeldriver on 2013-09-29
Are you being dropped to a grub prompt (like > ) or a root shell prompt (like # )? it sounds like your system is booting OK (thanks to the separate /boot presumably) but just can't mount / so is stuck in the initial ramfs. I have a little bit of experience with LVM but none with encrypted setups unfortunately - but I noticed that boot-repair attempts to fsck the encrypted LVM and fails

```

=================== Recommended repair
Recommended-Repair
This setting will not act on the MBR.
Additional repair will be performed:  repair-filesystems


Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

fsck -fyM /dev/sda1
fsck from util-linux 2.20.1

fsck -fyM /dev/sda5
fsck from util-linux 2.20.1
fsck: fsck.crypto_LUKS: not found
fsck: error 2 while executing fsck.crypto_LUKS for /dev/sda5
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/sda5 : Error code 32

```

so you might want to try doing that manually DISCLAIMER: I HAVE NEVER TRIED THIS  --> [http://ubuntuforums.org/showthread.php?t=708291&p=4524774#post4524774](http://ubuntuforums.org/showthread.php?t=708291&p=4524774#post4524774)

---

### Post by marcelo6 on 2013-09-29
Thanks for the reply steeldriver... Initially, grub starts up with two options (ubuntu and advanced options for ubuntu). When I select the first, it boots up and yes...is unable to mount the encrypted drive containing / ...then it drops into busybox (initramfs). Following your link, I followed those directions but nothing has changed.

---

