---
title: "dpkg = Broken in 7.10 Ubuntu"
date: 2008-04-24
forum: General Help
---

### Post by BazaarMunchkin on 2008-04-24
Hello All,

I am a virtual Ubuntu newb, so please bear with me as I attempt to explain the pickle I've gotten myself into.

After attempting to install a dual-boot Ubuntu system (with XP) I finally got internet access and my devices working correctly.  Excited, yet tired, I connected to the Internet and began to 'update' my system with Synaptic.

My mistake began when I selected all updates to apply rather than taking the time to sift through the updates. This attempted to install hundreds of updates at one time (about 200 or so.)

The updates all downloaded and began to extract. Somewhere in the process things began to fail with error messages. I was able to restart the system and get Gnome running again so I could look at the logs.  Here is where I can begin listing the error messages that come back.

Upon attempting to Launch either Synaptic or Gnome's 'Add/Remove' app I get the following message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

So I switched to a non X terminal and login.  I execute the command above with the following output:

```
ceshigh@Zexsea:/etc/init.d$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-14-generic:
 linux-restricted-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1
```

**My Logic**

In my feeble attempts to parse this output I've figured that either:

a) I need the "linux-restricted-modules-2.6.22-14-generic" package installed somehow w/o the use of dpkg or anything that relies upon it.

b)  I need to find a way to Uninstall the list up updates I originally attempted to apply w/o the use of dpkg.

c)  I need more Filesystem space somewhere that I haven't yet realized as I have Plenty of space left on my Ubuntu partitions.

So where have I completely gotten this wrong?  Any advice as to how I fix my package installation systems?

Any help would be greatly appreciated.

Sincerely,
Toby

---

### Post by chrisccoulson on 2008-04-24
Could you please post the output of
```
df -h
```

Your error message suggests that you are out of space on the filesystem that /boot resides on

---

### Post by Bateluer on 2008-04-24
Not 100% what the problem is, but you can tell how much hard drive space you have left with the command df. 

And since Gutsy has been out for 6 months, it has a few hundred packages to download and install after an initial install, so thats normal.

---

### Post by BazaarMunchkin on 2008-04-24
Thanks for the quick response.  The comment RE: my /boot partition may be valid. I originally created it so small b/c I was following some recommendations regarding the size needed.  

Here is my DF output:

```
aceshigh@Zexsea:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              25G  2.5G   21G  11% /
varrun                189M   88K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
udev                  189M   80K  189M   1% /dev
devshm                189M     0  189M   0% /dev/shm
/dev/sda3              23M   19M  3.2M  86% /boot
/dev/sdc2              13G  2.8G  9.6G  23% /fltsim
/dev/sdb2             3.4G  108M  3.1G   4% /home
/dev/sdb3             6.0G   32M  5.9G   1% /shared
/dev/sda1              50G   11G   40G  21% /windows
```

thanks again!

If it is indeed my /boot partition, then I will have to Resize it.  Should I be able to run my 'dpkg --configure -a' again once I've freed up space on /boot?

---

### Post by chrisccoulson on 2008-04-24
The available space on /boot is definately the problem. You should be able to continue upgrading once you've freed some space, but I'd advise on a larger /boot partition. The size you've got is only good for one kernel, so will always break during an upgrade from one Ubuntu version to the next (when there will be a minimum of 2 kernels installed at some point)

---

### Post by BazaarMunchkin on 2008-04-24
Thanks everyone.  At least I have a more certain path to walk. I appreciate your insight.

---

### Post by unutbu on 2008-04-24
I'm always nervous about resizing partitions because it sometimes requires reconfiguring grub. Is it true that in this case BazaarMunchkin need not worry about grub setup because resizing /boot will (presumably) change only the right-hand side of the partition and not the left?

---

### Post by radar.duse on 2008-04-24
Hi,
I was looking for a solution to a problem with dpkg that occurred today as I was updating some files with update manager. It stopped just before finishing :( ... and had this message:
 [B]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

I did the manual run but to no avail (froze again) with this report:
[B]
root@aureus-desktop:/home/aureus# dpkg --configure -a
Setting up update-manager (1:0.81.2) ...[/B]

...I searched the forum and got here. After running the  **df -h** I got this report:
[B]
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             9.0G  4.6G  4.0G  54% /
varrun                284M  224K  284M   1% /var/run
varlock               284M     0  284M   0% /var/lock
udev                  284M   56K  284M   1% /dev
devshm                284M     0  284M   0% /dev/shm
lrm                   284M   34M  250M  12% /lib/modules/2.6.22-14-generic/volatile[/B]

...is there something there suggesting my boot partition needs resizing?...
...is there something else I can do to revive my broken Synaptic Package Manager?..

Thanks for your time!

Radar.

---

### Post by BazaarMunchkin on 2008-04-25
To answer your question Unutbu......

I didn't have 'free' space after my /boot partition available to resize, as it was the 3rd of 4 primary partitions on that drive.

I used the Gutsy Live CD to boot, allowing the OS to only hold onto my Swap partitions.

I then 1st used GPartEd to shrink my last partition on the drive, creating space after my /boot partition - and Applied the changes. 

Next I used GParted to Grow my /boot partition to my new target size. After applying this change (shrinking takes -way- longer than growing partitions), I was ready to reboot.

After the Reboot, I reran my ***dpkg --configure -a*** and all went well, without error.

Thanks all for the help

This issue is now SOLVED, yet I didn't know how to mark it as so!

---

### Post by unutbu on 2008-04-25
Congratulations and thanks for reporting back on how you did it!

---

### Post by Bdanger on 2008-04-26
> **BazaarMunchkin said:**
> To answer your question Unutbu......

I didn't have 'free' space after my /boot partition available to resize, as it was the 3rd of 4 primary partitions on that drive.

I used the Gutsy Live CD to boot, allowing the OS to only hold onto my Swap partitions.

I then 1st used GPartEd to shrink my last partition on the drive, creating space after my /boot partition - and Applied the changes. 

Next I used GParted to Grow my /boot partition to my new target size. After applying this change (shrinking takes -way- longer than growing partitions), I was ready to reboot.

After the Reboot, I reran my ***dpkg --configure -a*** and all went well, without error.

Thanks all for the help

This issue is now SOLVED, yet I didn't know how to mark it as so!

I'm getting the same dpkg error as you and am trying to resize my boot partition also.  My linux partitions are set up as follows:

>SWAP (800mb)
>/boot (50mb)
>linux (16Gb)

My problem is that when I try to re-size my last partition(linux), Gparted won't let me create space before the partition, only after.  The "space preceeding partition" box is grayed out.  Any ideas??

---

### Post by unutbu on 2008-04-26
I am guessing that you are running gparted while running off your Linux system. You can't resize mounted partitions. So to resize the Linux partition
you need to either boot from the Live CD or equivalent.

---

### Post by Bdanger on 2008-04-26
> **unutbu said:**
> I am guessing that you are running gparted while running off your Linux system. You can't resize mounted partitions. So to resize the Linux partition
you need to either boot from the Live CD or equivalent.

Sorry I should have specified.  I'm running Gparted off knoppix live 5.1.  And I can resize any of the partitions, It just won't let me put the space before the linux partition, only after the partition.

---

### Post by Bdanger on 2008-04-27
...Anyone?

---

