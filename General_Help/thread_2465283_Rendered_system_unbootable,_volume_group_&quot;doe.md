---
title: "Rendered system unbootable, volume group &quot;does not exist&quot;, drops into shell"
date: 2021-07-28
forum: General Help
---

### Post by Ranbunta_Bantubunt on 2021-07-28
Hello all,

I have gotten myself into a pickle, wondering if someone can help me get up and running again.

I set up my laptop with ubuntu 20.04 according to these instructions for whole disk encryption:

[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

I was booted into ubuntu, everything working properly, when I wanted to set up a new encrypted external drive for backups. I set up the drive according to similar instructions as given in the full disk encryption how to link above, then I wanted to set the drive up to auto-mount on system boot. To do this, I was again following the instructions in the above Howto URL, and was at the step where one makes a keyfile and stores the keyfile to /etc/luks. I copied the following command, intending to edit it in the terminal, but foolishly just pasted it in, not realizing there was a carriage return in the copied text, so the command executed, overwriting my existing boot_os.keyfile file:

```
# dd if=/dev/urandom of=/etc/luks/boot_os.keyfile bs=512 count=1
```

However, I don't think this is the problem - I assume I recovered from this blunder, as I had a copy of the correct boot_os.keyfile on another backup drive, and I'm confident it is the correct file. So hopefully that part is ok. I just copied the backup into /etc/luks so should be ok. 

I then made a keyfile for the new backup drive, and added it to crypttab and then added it manually to fstab. 

Then, I ran

```
update-initramfs -u -k all

```

This command gave a number of errors, indicating that various drives "used a keyfile". I can't recall :( the exact error message, but I don't usually see that message when I run update-initramfs.

Then, on rebooting the computer, I was prompted to enter my passphrase for the boot partition, which I did enter and the boot process seemed to start OK. I got the menu about whether I wanted to boot into Ubuntu or Ubuntu-recovery mode, etc. 

When I boot into Ubuntu, it drops me into a shell unfortunately. booting into recovery mode, I get this error (typing in from a picture I took of the screen, so if the format is off that's why)

```

Begin: waiting for suspend/resume device ... Begin : Running /scripts/local-block ... Volume group "ubuntu-vg" not found
Cannot process volume group ubuntu-vg
done.
done.
Gave up waiting for suspend/resume device
done.

```

I booted into a live USB (which I'm using now to post this post), and ran gparted... 

It is saying that the 2 MB GRUB partition does not have a recognized file system:

```

Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/nvme1n1p2 is missing
```

but I'm not sure this is the problem, since I did get as far as you can see above. So it seems the grub partition must be ok. 

I would like to try mounting the root and boot drives manually, as I have passphrase access to them in addition to the keyfile access, but I'm not quite sure how to do that. 

Anyway I'm a little stuck at this point... any ideas about what I can do next? I have a full backup of the system taken by rsync-backup (which is where I got the boot_os.keyfile file from). If somehow I didnt successfully restore the boot_os.keyfile, eg, if I need to change permissions or something like that, I would need to mount the file system to gain access to the /etc/luks directory. In the shell I was dropped into, I did not recognize any directories and /dev/mapper had nothing but "control" in it. 

Thanks for any help. 

Rabu

---

### Post by Ranbunta_Bantubunt on 2021-07-28
I tried to see if it was an issue with a "bad superblock" and did the following, doesnt seem fruitful:

```
root@ubuntu:~# fsck.ext4 -v /dev/nvme1n1p2
e2fsck 1.45.5 (07-Jan-2020)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/nvme1n1p2

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

root@ubuntu:~# e2fsck -b 8193 /dev/nvmen1p2
e2fsck 1.45.5 (07-Jan-2020)
e2fsck: No such file or directory while trying to open /dev/nvmen1p2
Possibly non-existent device?
root@ubuntu:~# e2fsck -b 8193 /dev/nvme1n1p2
e2fsck 1.45.5 (07-Jan-2020)
e2fsck: Invalid argument while trying to open /dev/nvme1n1p2

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

root@ubuntu:~# e2fsck -b 32768 /dev/nvme1n1p2
e2fsck 1.45.5 (07-Jan-2020)
e2fsck: Invalid argument while trying to open /dev/nvme1n1p2

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

---

### Post by Ranbunta_Bantubunt on 2021-07-28
Ok I was able to use cryptsetup open to mount the boot and root drives manually, and I can see my files, including the boot_os.keyfile file that I overwrote initially. 

I think I will go ahead and re-add the boot_os.keyfile as an authorized keyfile to decrypt the root volume, just in case there is a problem with that file. I do think it is the correct keyfile/data but just in case it is corrupt. I could also go ahead and redo all the steps involved in setting up the root volume and swap to decrypt on boot as well, if that doesnt work. Here goes nothing....

---

### Post by Ranbunta_Bantubunt on 2021-07-28
Ok! Just following up for posterity... I managed to fix the system :) 

Thought struck me that I mangled the initrd.img file, so I could restore that from backup. After mounting the /boot volume through the live USB, I copied a version of the initrd from prior to my running update-initrd into the /boot volume, and it worked ! :) 

Now that I am back in, I think I actually didnt need to run the update-initramfs in the first place as I wasn't making any changes to the boot environment, that was dumb. 

Just posting my solution, in case it helps someone in the future in a similar situation.

Cheers!

Rabu

---

### Post by oldfred on 2021-07-28
Do not know LVM nor encryption.

But you have a bios_grub and an ESP.
The bios_grub is required for BIOS boot of a system on gpt partitioned drive. It must be unformatted so gparted will also show it as an error.
You also show an ESP, but FAT16. While originally allowed, it now is normally FAT32.

You typically cannot use gparted on LVM, just on the underlying partition(s).
You need to use LVM tools for LMV volumes.

And with encryption must have good backups.

---

### Post by Ranbunta_Bantubunt on 2021-07-28
Thanks for the info oldfred. The explanation about the grub volume makes sense. 

I was just using gparted to look at the volumes and see what's there, not to make changes.

I'm a backup fanatic so totally agree with your comments about needing good backups. As noted in my above post, the backups saved me as I restored a previous initrd image and was able to rescue the system that way.

Re: fat16, it's what had been recommended in the tutorial from 2019 that I linked to.... thanks for the update.

---

