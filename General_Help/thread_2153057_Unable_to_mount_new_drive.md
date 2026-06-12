---
title: "Unable to mount new drive"
date: 2013-06-10
forum: General Help
---

### Post by defaria on 2013-06-10
I'm desperate here as my main root drive is failing. I have an older system which is my main server. The root drive is on it's last legs so I got a new terabyte drive and installed it. I'm trying to copy my backup drive (500G) to the new terabyte drive and want to transfer my root drive (160G) to my backup drive (500G) later. 

I've used ddrescue to copy all of the data from my backup drive (500G) -> the new terabyte drive - or at least I thought I did. I did a "ddrescue -f /dev/sdc /dev/sdb". It took a long time but eventually finished. Now I want to mount the /dev/sdb drive which should be my new terabyte drive but it fails to mount stating:

```

$ mount -t ext4 /dev/sdb /mnt/terabyte
[18687.070485] EXT4-fs (sdb): VSF: Can't find ext filesystem
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
           missing codepage or helper program, or other error
           In some cases useful info is found in syslog - try
           dmesg | tail   or so

```

Of course dmesg gives me little other than "can't find an ext4 filesystem". What did ddrescue take 3 hours copying too if not to the new drive?

An fdisk -l shows me

```

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
DIsk identifier: 0x25ee25ed

```

So it seems to me that the system sees the drive but I just can't mount it!

How do I properly mount this terabyte drive and/or transfer all of the stuff from my backup 500G drive to it?

Also, how do I make an exact copy of my currently failing 160G root drive -> 500G old backup drive so I can then boot from it?

Thanks.

---

### Post by ahallubuntu on 2013-06-10
~

---

### Post by defaria on 2013-06-10
Here's the full output:

```

$ fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x874a874a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312078689   156039313+  8e  Linux LVM
/dev/sda2       312078690   312576704      249007+   5  Extended
/dev/sda5       312078753   312576704      248976   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x25ee25ed

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x25ee25ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *          63   976768064   488384001    5  Extended
/dev/sdc5             126   976768064   488383969+  83  Linux

Disk /dev/mapper/jupiter-root: 155.3 GB, 155344437248 bytes
255 heads, 63 sectors/track, 18886 cylinders, total 303407104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/jupiter-root doesn't contain a valid partition table

Disk /dev/mapper/jupiter-swap_1: 4437 MB, 4437573632 bytes
255 heads, 63 sectors/track, 539 cylinders, total 8667136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/jupiter-swap_1 doesn't contain a valid partition table

Disk /dev/sdd: 8166 MB, 8166703104 bytes
256 heads, 63 sectors/track, 989 cylinders, total 15950592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005a71f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          56    15950591     7975268    c  W95 FAT32 (LBA)

```

My system is old and uses PATA. The 1TB drive is a SATA so I have a SATA -> PATA adapter for it. I didn't think that I could mount both the 500G backup drive and the 1tb drive on the same cable but it appears to be working. So I decided to use ddrescue to copy the 500G -> 1TB as [http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk) was talking about. I figured that later I'd do a ddrescue from my failing 160G root drive -> 500G drive then reboot. The 1TB drive would become my new backup drive and the 500G drive would become my new root drive.

I've switched to be using gparted to create an unallocated partition on the 1TB drive. I tried to right click on the 500G drive in gparted and select Copy but Copy is grayed out. Now what?

Note I tried umount but it says the 500G drive is busy. I tried umounted it from the cmdline which also says it's busy. Of course lsof and fuser are of no use (they never work for me). Again, now what?

---

### Post by defaria on 2013-06-10
OK, realized I needed to umount that partition so I rebooted and umounted it. Now I can copy and paste the partition. Nicely I can also size it with gparted at the same time. The copy is happening now (or actually it's just doing fsck right now... Ah it's copying now... 6 hours! Damn, servers down for at least 6 hours...). Assuming this works without a problem, can I use gparted copy/paste to copy my root drive -> 500G drive and end up with a 500G drive that I can boot off of? I see a couple of problems with this. First, I doubt that the fsck will be successful on the root drive. As I said it's dying and every time I boot I SMART tells me this and requires I hit F2 to continue anyway. Will gparted allow me to go forward if fsck errors are present.

Secondly, since this is the root drive I need to boot into Ubuntu Live CD (well USB) so that the root drive is not active. I've been having problems with that too. When I boot up I get into Unity but the machine is doggedly slow. By slow I mean clicking on the Dash takes upwards of 5 minutes to to render! Not sure what that is so I am a little leary about getting gparted up at all! I can dump into the IDE using Ctrl-Alt-F1 and become root. I have managed to copy ddrescue to my backup drive and plan on attempting to use that to copy the failing root drive -> 500G drive then attempt a boot. Any advice for this part would be welcomed...

---

### Post by oldfred on 2013-06-10
I do not know about LVM and what issues that may cause.

You cannot use dd and have both drives installed when rebooting. A dd image is an exact image, so it copies UUIDs and you cannot have duplicate UUIDs. DD is really intended for same size to same size copy.

I prefer when wanting your install on an new drive to just install Ubuntu to new drive and copy all of /home over. You may need some settings from /etc if you hand edited any hardware settings and would have to reinstall all software. But that often avoids all the issues of copy and duplicate UUID, changing UUID, editing fstab and reinstalling grub2 to get a copy to work correctly. 
Rsync or cp (with parameters to preserve ownership & permissions) will be a lot faster than a dd as dd also copies all empty space.

---

### Post by defaria on 2013-06-10
The issue is this is not a desktop - this is my server. So I have installed and configured many things. To reinstall is risky and I'd much rather copy my know to be working existing system from the current root drive to a new drive.

I've managed to copy my backup 500G drive -> 1TB drive and is all looks OK. I've now deleted the partition on the 500G drive as I can mount the 1TB drive and run my server. My problem is still that the root drive is about to die and I need to transfer the OS from the dying root drive to the now empty 500G. I had hopes that I could use gparted to do this so I created a Gparted Live USB and booted to that. This should leave my root drive unmounted and in theory I should be able to do the same thing using Gparted by copying the partitions from the dying root to the 500G. Alas however when I right click on the root partition Copy is greyed out! In the past I got past this by umounting the drive but I cannot umount the root drive as AFAICT it's not mounted when I'm booted into Gparted Live. How do you copy the partition when copy is greyed out!!!

I notice that gparted has a "Deactivate" selection on the right click menu. I think that only sets it to bootable or not. Or perhaps that's some LVM thing. I'm not sure how this LVM thing works nor do I remember why or how I set up an LVM some 6 or 7 years ago. In any event, how do I copy this disk to the 500G drive? I don't think the UUID would be a problem because gparted allows me to generate a new one. I guess I'll look into dd but any advice would be appreciated.

---

### Post by oldfred on 2013-06-10
I do not know LVM, but I think this says gparted does not work with LVM. See disadvantages in Post #9.

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by defaria on 2013-06-10
I think I agree with you that LVM makes this more difficult. Oh why did I set up LVM I'll never know. Meantime [http://clonezilla.org/](http://clonezilla.org/) seems to say it should be able to handle this. Alas whenever I try to use Startup Disk Creator I get:

An uncaught exception was raised:
unorderable types; NoneType() <= str()

in a dialog box labeled "Installation failed". Note to developers... Frigging English please! WTF is NoneType() <= str() supposed to mean to an end user?!? WTF did this fail? Can you simply put out an English statement explaining why this did not work - geeze! Sorry but I've hit so many of these unexplainable, for who knows why this frigging thing just fails lately that it's really tiresome! As I always say, you are the best person in the whole wide world to explain at this moment why the software failed and I'm sorry you really blew it! And functionality?!? Excuse me but could dd including a -verbose option or a -progress parm?!?

Not sure if this clonezilla will even boot anything. Currently I'm doing a straight dd from the failing root drive to the 500G. It's slow, real slow, probably because it's hitting a lot of errors on the failing root drive. However I have no idea of whether or not this will work, whether or not I'll have a bootable LVM drive on the 500G after the dd finishes (in like 1 and 1/2 hours I've managed to copy 21 gig...), whether I have a UUID conflict (planning on unpluging the failing root drive and plugging the 500G copy into the same cable when and if this finishes), and I'm not sure, failing that, whether or not I can boot this clonezilla USB stick to have another go at it if the former fails. Ugh - no fun...

---

### Post by defaria on 2013-06-11
Well I tried the straight dd and after some 24 hours I disconnected the failing root drive and plugged the newly copied 500G drive in it's place after setting the jumper back to master. Result? Unable to boot from drive! :-(

Meantime I had tried to create that clonezilla boot USB and it complained as noted above. Well time to try that. It booted, even though it complained about mod.probe, etc. Clonezilla goes through a prompted session about where to copy from and to and I did not see my dying root drive on the list! Turns out I think I didn't have it plugged back in properly. Rebooted with clonezilla and it dropped into busybox this time. Ugh! Rebooted again and got it going. Chose the expert mode. Saw some options for cloning the boot partition and MBR. This is looking hopeful. Started the cloning process and it had this nice progress screen... that is until I started hitting the errors on my dying root drive. The process doesn't think it'll hit errors and now the screen is just a total mess! A refresh option guys? Ugh. So now it's like 20 hours of waiting, hoping this is gonna work...

---

### Post by oldfred on 2013-06-11
The poor horse is already dead, so I hate to beat it even more.

But I do a full install in about 10 minutes, updates another 10 minutes depending on how old install version is. Then copy /home over is quick as it is less than 2GB with most of that my .wine.
Then I have to spend another 20 to 30 minutes downloading and installing the list of installed apps using dpkg.
I then have a new install, with all settings from /home, all applications and it is totally housecleaned - no old logs nor history, nor caches etc.
The only issue would be in your server case is software installed from outside repository or software like databases that may have separate files not in /home.

---

### Post by defaria on 2013-06-12
You don't understand. This is a server! This is a highly customized server! It's not simply a matter of reinstall, copy home and tweak here and there and you're set. There's much more involved at least in *my* server than you think. I had to, after all, do a reinstall as I cannot boot from my dying root drive anymore. I'm finding all kinds of things wrong that I had customized and need to reinstall, reconfigure and refigure out from some 10 years of customizing this server. You may not customize a server as much as I do but I surely do. Luckily I did have some time to store things away to my backup drive and I'm in the process of rebuilding my server and figuring out problems I've long since solved in the 90's. This is a *PAINFUL* process for me so don't belittle it. You have no idea.

Linux, and Ubuntu could have been a lot more helpful in this process and it's attitudes like yours (well all you have to do is reinstall because obviously you didn't modify that much right) that makes this a PITA.

Right now I'm wrestling with mysql user/password issues. My email's still not up (which involves a custom written set of spam filters in Perl that, for example, need some CPAN modules and need mysql to be working as well as Apache, etc just so I can get email!).

As it is I know I lost at least one of my configurations as I forget that it existed in my $HOME directory on the server and forgot to copy it off before the drive died.

---

### Post by oldfred on 2013-06-12
The more customized an install is, then the more important a good backup plan is. And servers usually have better backup plans than most desktop users. Server Admins understand the importance where the average user has not run into most issues of drive failure or system crashes.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by defaria on 2013-06-13
You speak as if I had no backup. I have a backup. However for the last few weeks I've been seeing FS errors in my backup log as backup is one of those processes that touches all files. And it is exactly how I knew this drive was on its last legs and exactly why I took action before it wouldn't boot anymore (which eventual it wouldn't boot anymore). However would you trust such a backup? I wouldn't. Meantime, while I had a chance, I copied a lot of the data I thought I'd need if I had to piece this thing back together onto my backup drive. Good thing too as I needed it. I was able to recover all of my web site files and I had squirreled away a copy of /etc which has been quite useful.

That said, I've gotten a number of different files I didn't anticipate I'd need like crontabs things in my home directory, etc. from this backup. I just didn't trust it enough to say "just restore everything from here" when it was obvious that the backup log stated there were many read errors when doing the backup.

I'm almost 100% back up. The parts still missing are surprising as it may have been a tweak I've done many years ago or stuff I've added since. For example, I have my own spam filters. One part of my system is called MAPSDeliver and it's a Perl script whose job it is to dump and email into /var/mail/$username. As such it was setgid to mail to allow it to do that. However Perl decided to stop supporting setgid (and setuid) Perl scripts ~5.12 or so. I hadn't noticed as I hadn't updated Perl on my server for quite some time. So now I'm stuck with no way to do this until I re-write it in C. Other things are things that just didn't come in with an install of Ubuntu Server like synaptic and a few other things. Backups are helpful. But they are not the be all, end all - especially when you know a head of time that they are corrupted and suspect.

---

