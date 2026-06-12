---
title: "Safely remove swap partition in a LUKS disk setup?"
date: 2016-07-02
forum: General Help
---

### Post by pandoragami on 2016-07-02
Hello all,

This question is probably not an easy one to explain or to solve so here goes. Basically I installed xubuntu onto a disk automagically and it configure 4 gigs of swap space onto the disk which is coincidentally LUKS encrypted along with the rest of the partition that has all the home folders, etc. What I tried doing so far is looking at ways of deleting the swap using the Gnome Disk Tool, but that only allows me to format the said partition and I'm not sure if formatting would work because then I would have to resize my primary partition an extra 4 gigs to fill the void. I also tried Gparted but that is not working in terms of support for LUKS partitions. 

I've also looked at these to pages but I'm worried about boot problems after deleting the partition. 

[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

[https://www.rootusers.com/how-to-increase-the-size-of-a-linux-lvm-by-adding-a-new-disk/](https://www.rootusers.com/how-to-increase-the-size-of-a-linux-lvm-by-adding-a-new-disk/)


thanks.

---

### Post by TheFu on 2016-07-02
You need to use lvm tools to manage LVs.  I don't know of any GUIs which do that. Doesn't mean there aren't any.
LVs are sorta "like" partitions, but without having to reboot to make live changes.

Also, if you've gone to the effort to use whole disk encryption, please don't break it by putting the swap "partition" outside the encrypted area. Lots of reasons for this.

If you want more detailed help, please post the output from the following tools using "code tags":
```
lsblk
pvs
vgs
lvs
```
Probably need sudo in front of most of those. Depends on your group memberships.

---

### Post by pandoragami on 2016-07-02
> **TheFu said:**
> You need to use lvm tools to manage LVs.  I don't know of any GUIs which do that. Doesn't mean there aren't any.
LVs are sorta "like" partitions, but without having to reboot to make live changes.

Also, if you've gone to the effort to use whole disk encryption, please don't break it by putting the swap "partition" outside the encrypted area. Lots of reasons for this.

If you want more detailed help, please post the output from the following tools using "code tags":
```
lsblk
pvs
vgs
lvs
```
Probably need sudo in front of most of those. Depends on your group memberships.


Alright, here's the output.

```

pandoragami@pandoragami-desktop:~$ sudo lsblk
[sudo] password for pandoragami: 
NAME                    MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sdc                       8:32   1 14.9G  0 disk  
&#9500;&#9472;sdc1                    8:33   1  487M  0 part  /boot
&#9500;&#9472;sdc2                    8:34   1    1K  0 part  
&#9492;&#9472;sdc5                    8:37   1 14.4G  0 part  
  &#9492;&#9472;sdb5_crypt          252:0    0 14.4G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root   252:1    0 10.5G  0 lvm   /
    &#9492;&#9472;ubuntu--vg-swap_1 252:2    0    4G  0 lvm   
      &#9492;&#9472;cryptswap1      252:3    0    4G  0 crypt [SWAP]
sr0                      11:0    1 1024M  0 rom   
pandoragami@pandoragami-desktop:~$ sudo pvs
  PV                     VG        Fmt  Attr PSize  PFree
  /dev/mapper/sdb5_crypt ubuntu-vg lvm2 a--  14.42g    0 
pandoragami@pandoragami-desktop:~$ sudo vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  ubuntu-vg   1   2   0 wz--n- 14.42g    0 
pandoragami@pandoragami-desktop:~$ sudo lvs
  LV     VG        Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   ubuntu-vg -wi-ao---- 10.47g                                                    
  swap_1 ubuntu-vg -wi-ao----  3.95g                                                    
pandoragami@pandoragami-desktop:~$ 

```

I plan on using a second disk as a swap, is that bad? I can also boot into another separate ubuntu disk and operate on my xubuntu if needed. Right now I'm using a 16 gig usb 3 flash drive (for convenience).

thanks so far.

---

### Post by TheFu on 2016-07-03
The easiest answer is to get a 32G USB3 drive (Thought I saw one for $17 earlier today) and mirror the 16G over. Then you can add/extend the PV, the VG and LV for the  / partition - probably can do all of this while running the OS. LVM is convenient in that way. Only need 1 crypt password to enter at boot, unlike other options, which will require another decryption - another prompt to decrypt.

Ok. Facts and opinions provided. Onto the How-To .... in case you still want to do this (or some other lurker finds this later). Only you know the real situation, not me.

First disable the swap - **swapoff** cmd does that.  Would be good to run **swapon -s** first to see what is being used. Before doing the swapoff, run **blkid ** to get the UUID for the swap LV/device. 
Edit the /etc/fstab - comment out the swap line - the UUID found above.
Next remove the swap LV/device.  **lvremove**.  Then use the **lvresize** to make the LV larger for the main OS storage, /.

All of these things should run almost instantaneously - even the resize at the end.  

You could reduce the swap size a little instead of deleting it. That size reduction might change the UUID, I'm not sure. If the UUID chnages, then the fstab entry will need to change too.

Of course, before doing brain surgery like this, a complete backup is needed in case something bad happens. I only do stuff like this about once a year, which is why I didn't list the exact options for every command. I'd have to lookup those, just like you do. Knowing what is possible is most of this battle.

---

### Post by pandoragami on 2016-07-03
> **TheFu said:**
> The easiest answer is to get a 32G USB3 drive (Thought I saw one for $17 earlier today) and mirror the 16G over. Then you can add/extend the PV, the VG and LV for the  / partition - probably can do all of this while running the OS. LVM is convenient in that way. Only need 1 crypt password to enter at boot, unlike other options, which will require another decryption - another prompt to decrypt.

Ok. Facts and opinions provided. Onto the How-To .... in case you still want to do this (or some other lurker finds this later). Only you know the real situation, not me.

First disable the swap - **swapoff** cmd does that.  Would be good to run **swapon -s** first to see what is being used. Before doing the swapoff, run **blkid ** to get the UUID for the swap LV/device. 
Edit the /etc/fstab - comment out the swap line - the UUID found above.
Next remove the swap LV/device.  **lvremove**.  Then use the **lvresize** to make the LV larger for the main OS storage, /.

All of these things should run almost instantaneously - even the resize at the end.  

You could reduce the swap size a little instead of deleting it. That size reduction might change the UUID, I'm not sure. If the UUID chnages, then the fstab entry will need to change too.

Of course, before doing brain surgery like this, a complete backup is needed in case something bad happens. I only do stuff like this about once a year, which is why I didn't list the exact options for every command. I'd have to lookup those, just like you do. Knowing what is possible is most of this battle.


Thanks for your help. I'm not sure if doing this is as important as having a working OS at the moment and while I could backup, somehow I just don't feel like dealing with this as you can probably understand. I guess I'll just reinstall xubuntu or put this off for a fun Saturday night when I'm bored. Again thanks!

---

### Post by TheFu on 2016-07-03
Is a backup that hard?  Lots of easy methods for this small of an install:
a) rsync
b) ddrescue
c) partimage
d) fsarchive
e) or use one of the real backup tools which handles versioned backups too .... rdiff-backup, duplicity, or any of the 50 different rsync-based scripts like rbackup, snapback, .... 

About the only way I wouldn't touch for more than 1G of stuff is tar or zip or gz or bzip or arj or ... any of those old-school MS-Dos solutions.
Best to get a good backup working BEFORE you really need it.

---

### Post by pandoragami on 2016-07-03
> **TheFu said:**
> Is a backup that hard?  Lots of easy methods for this small of an install:
a) rsync
b) ddrescue
c) partimage
d) fsarchive
e) or use one of the real backup tools which handles versioned backups too .... rdiff-backup, duplicity, or any of the 50 different rsync-based scripts like rbackup, snapback, .... 

About the only way I wouldn't touch for more than 1G of stuff is tar or zip or gz or bzip or arj or ... any of those old-school MS-Dos solutions.
Best to get a good backup working BEFORE you really need it.


I made a backup of the disk using clonezilla so that's done. So far I've tried this much, but I'm stuck at the part where I delete the swap.

sudo blkid /dev/mapper/cryptswap1
/dev/mapper/cryptswap1: UUID="93f5fba4-9c2f-4e3b-bc01-480cdf976fe2" TYPE="swap"


    sudo swapoff /dev/mapper/cryptswap1


Started:
    sudo mousepad /etc/fstab


Commented out the line.
    /dev/mapper/cryptswap1 none swap sw 0 0

At this point I rebooted and it still ran!


pandoragami@pandoragami-desktop:~$ sudo lvremove /dev/mapper/cryptswap1
  Volume group "cryptswap1" not found
  Cannot process volume group cryptswap1
pandoragami@pandoragami-desktop:~$ sudo lvremove /dev/ubuntu-vg/swap_1
  Logical volume ubuntu-vg/swap_1 is used by another device.


Here's an image of my gnome disk tool, both of the 4.2 gig block devices are **inactive**, but both are actually the _same thing_, **dev/ubuntu-vg/swap_1** and **dev/mapper/cryptswap1**. Why are there two of these by the way?

I[ATTACH=CONFIG]269937[/ATTACH]

---

### Post by TheFu on 2016-07-03
You can't use disk tools to deal with LVM.  It just doesn't work that way.  I don't use and have never used any GUI tools for disk management. Wouldn't trust them myself. There may be different opinions around. I dunno.

PVs, VGs, and LVs are **not** the same thing, regardless of whether they appear to be the same thing.  LVM is extremely flexible at a price of slightly greater complexity.  I avoided LVM for about 10 yrs because I simply wasn't ready to use it. These days, I use if for all physical disks and savor the flexibility provided, but can completely understand wanting to avoid it.  Again, logically, an LV can be thought of as a partition, but it is NOT a partition and no tools will treat it as one.

Encryption is happening at the partition level, below the PV level of LVM.  This is why both the / and swap are inside the same partition, but in different LVs.  The single VG is purely for simplicity. 

Sorry if this isn't clear.  A primer on LVM might be helpful ... or not. Depends on how much understanding you need.   Think of LVM as an egg within an egg within an egg withing an egg. For simple setups like this, that is close enough to how it works (though not truly accurate for non-trivial situations). Each egg can be exactly the size of the egg outside it or it can leave 99% of that egg unused.  There can be 1 or 500 eggs (LVs) inside the VG "egg". Flexibility.  Eggs can be resized.  To have flexibility, I tend to leave some room inside the VG unused for later needs where necessary.  1G of space available to be added to one of the other LVs later can make a difficult issue into a trivial problem needing 3 min of work to fix.

As you change things in LVM, use the pvs, vgs and lvs tools to see those changes.  The encryption is a separate thing to everything "lvm".  Also, verify with the **swapon -s** cmd that no swap is being used.

Hope this clarifies things some. Not sure I have. Sorry if not.

---

### Post by pandoragami on 2016-07-03
> **TheFu said:**
> You can't use disk tools to deal with LVM.  It just doesn't work that way.  I don't use and have never used any GUI tools for disk management. Wouldn't trust them myself. There may be different opinions around. I dunno.

PVs, VGs, and LVs are **not** the same thing, regardless of whether they appear to be the same thing.  LVM is extremely flexible at a price of slightly greater complexity.  I avoided LVM for about 10 yrs because I simply wasn't ready to use it. These days, I use if for all physical disks and savor the flexibility provided, but can completely understand wanting to avoid it.  Again, logically, an LV can be thought of as a partition, but it is NOT a partition and no tools will treat it as one.

Encryption is happening at the partition level, below the PV level of LVM.  This is why both the / and swap are inside the same partition, but in different LVs.  The single VG is purely for simplicity. 

Sorry if this isn't clear.  A primer on LVM might be helpful ... or not. Depends on how much understanding you need.   Think of LVM as an egg within an egg within an egg withing an egg. For simple setups like this, that is close enough to how it works (though not truly accurate for non-trivial situations). Each egg can be exactly the size of the egg outside it or it can leave 99% of that egg unused.  There can be 1 or 500 eggs (LVs) inside the VG "egg". Flexibility.  Eggs can be resized.  To have flexibility, I tend to leave some room inside the VG unused for later needs where necessary.  1G of space available to be added to one of the other LVs later can make a difficult issue into a trivial problem needing 3 min of work to fix.

As you change things in LVM, use the pvs, vgs and lvs tools to see those changes.  The encryption is a separate thing to everything "lvm".  Also, verify with the **swapon -s** cmd that no swap is being used.

Hope this clarifies things some. Not sure I have. Sorry if not.


Tried the swapon -s cmd and nothing else comes up, what could be using an inactive swap. Is it because the partition is within another encrypted partition that is being used. I can try to boot into another linux environment  and operate on the current disk to remove the encrypted swap except that I had trouble decrypting the volume due to the disk name being wrong. I guess I would use that UUID name?

---

### Post by TheFu on 2016-07-04
The swap area is not a partition. It is an LV - logical volume. lvremove has to be used, correctly to delete it. logical volumes have "names" and device paths. The "name" is shown in the 1st column of the **lvs** command output.  In theory, according to the lvremove manpage, either of these things can be used to delete an LV. I've only used the name before, never the path.

**sudo lvremove swap_1** should be the command, assuming the output provided above is still correct. Would really be helpful if you posted the exact commands and relevant output here, if there are issues.

---

### Post by pandoragami on 2016-07-04
> **TheFu said:**
> The swap area is not a partition. It is an LV - logical volume. lvremove has to be used, correctly to delete it. logical volumes have "names" and device paths. The "name" is shown in the 1st column of the **lvs** command output.  In theory, according to the lvremove manpage, either of these things can be used to delete an LV. I've only used the name before, never the path.

**sudo lvremove swap_1** should be the command, assuming the output provided above is still correct. Would really be helpful if you posted the exact commands and relevant output here, if there are issues.


No problem, what exact commands would you like to see output. I've posted the ones I've tried but if there are other ones, let me know.

---

### Post by pandoragami on 2016-07-04
I tried the lvremove command for swap_1, no luck, here.


```
pandoragami@pandoragami-desktop:~$ sudo lvremove swap_1 
[sudo] password for pandoragami: 
  Volume group "swap_1" not found
  Cannot process volume group swap_1
pandoragami@pandoragami-desktop:~$ sudo lsblk
NAME                    MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sdb                       8:16   1 14.9G  0 disk  
&#9500;&#9472;sdb1                    8:17   1  487M  0 part  /boot
&#9500;&#9472;sdb2                    8:18   1    1K  0 part  
&#9492;&#9472;sdb5                    8:21   1 14.4G  0 part  
  &#9492;&#9472;sdb5_crypt          252:0    0 14.4G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root   252:1    0 10.5G  0 lvm   /
    &#9492;&#9472;ubuntu--vg-swap_1 252:2    0    4G  0 lvm   
      &#9492;&#9472;cryptswap1      252:3    0    4G  0 crypt 
sr0                      11:0    1 1024M  0 rom   



```

---

### Post by TheFu on 2016-07-05
I checked the manpage.

**sudo lvremove ubuntu-vg/swap_1** looks like what the command examples are showing.

I'm also a little confused by the cryptswap1 being _inside_ ubuntu--vg-swap_1.  I don't see that here.

---

### Post by pandoragami on 2016-07-05
> **TheFu said:**
> I checked the manpage.

**sudo lvremove ubuntu-vg/swap_1** looks like what the command examples are showing.

I'm also a little confused by the cryptswap1 being _inside_ ubuntu--vg-swap_1.  I don't see that here.

Tried that one too. Same result. Would it be easier to just use another linux drive and decrypt and delete the swap instead, any suggestions on that route?

```
sudo lvremove ubuntu-vg/swap_1


  Logical volume ubuntu-vg/swap_1 is used by another device.

```

---

### Post by TheFu on 2016-07-05
I think the easiest answer is to clone the existing flash drive to a larger one, then us LVM to increase the size of / and leave the swap alone.  This was mentioned in #4 post above.

The 
> 
  Logical volume ubuntu-vg/swap_1 is used by another device. is confusing to me. Did you really disable the swap with swapoff and remove it from the fstab?

---

### Post by pandoragami on 2016-07-05
> **TheFu said:**
> I think the easiest answer is to clone the existing flash drive to a larger one, then us LVM to increase the size of / and leave the swap alone.  This was mentioned in #4 post above.

The 
 is confusing to me. Did you really disable the swap with swapoff and remove it from the fstab?


Definitely so, I disabled the swap using the **swapoff **and then I edited out the line for the swap in the fstab file with a # in front of it. I then rebooted and the swap is not running. I even checked the System Monitor to see if I have a swap and it's [U]**zero**!


[/U]I'd like to solve the swap problem for the sake of knowing how to do it, but if there's no solution I could just.
 
A. Get a bigger drive.
B. Delete the OS and reinstall with manual partition creation, instead of letting the installer do what's best for a 250 gig hard drive.

---

### Post by TheFu on 2016-07-06
Thanks for the clarification. I believe you 100%.

The cryptswap on your system is different from mine.
```
$ !lsb
lsblk 
NAME                          MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda                             8:0    0 55.9G  0 disk  
ââsda1                          8:1    0  487M  0 part  /boot
ââsda2                          8:2    0    1K  0 part  
ââsda5                          8:5    0 55.4G  0 part  
  ââsda5_crypt                252:0    0 55.4G  0 crypt 
    ââubuntu--mate--vg-root   252:1    0 51.5G  0 lvm   /
    ââubuntu--mate--vg-swap_1 252:2    0    4G  0 lvm   [SWAP]

``` Sorry about the odd characters ... been working with multi-language support and don't have the final solution nailed yet.

I'm out of ideas, except to start from the deepest level (cryptswap?) and work out to LV.

I've never found a way to have encrypted storage with the OS and manually created partitioning. It isn't for lack of trying either.  The only way I've ever found to have whole disk encryption (except /boot) with Ubuntu is with the automatic installer.  Probably tried over 50 different installs, not once did it work.  I do know how to manually mount encrypted partitions, but getting the setup correct for booting has eluded me.  I've tried GPT and MBR, with LVM and without.  The only thing left to try is ZFS.  Hummmmm. Now that 16.04 supports ZFS ... something new to attempt.  Need to test this out inside a VM first.

Good luck to you. Think I've imparted all I can here.  Did just see a fairly advance ZFS boot how-to with encryption, which provided some step-by-step info on using dm-crypt which might shed some light on doing it manually. It was a bootstrap install (minimal) in that guide. Not certain I'm willing to go to that effort (about 3 hrs they claim) to work through all the steps.

---

### Post by pandoragami on 2016-07-06
> **TheFu said:**
> Thanks for the clarification. I believe you 100%.

The cryptswap on your system is different from mine.
```
$ !lsb
lsblk 
NAME                          MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda                             8:0    0 55.9G  0 disk  
ââsda1                          8:1    0  487M  0 part  /boot
ââsda2                          8:2    0    1K  0 part  
ââsda5                          8:5    0 55.4G  0 part  
  ââsda5_crypt                252:0    0 55.4G  0 crypt 
    ââubuntu--mate--vg-root   252:1    0 51.5G  0 lvm   /
    ââubuntu--mate--vg-swap_1 252:2    0    4G  0 lvm   [SWAP]

``` Sorry about the odd characters ... been working with multi-language support and don't have the final solution nailed yet.

I'm out of ideas, except to start from the deepest level (cryptswap?) and work out to LV.

I've never found a way to have encrypted storage with the OS and manually created partitioning. It isn't for lack of trying either.  The only way I've ever found to have whole disk encryption (except /boot) with Ubuntu is with the automatic installer.  Probably tried over 50 different installs, not once did it work.  I do know how to manually mount encrypted partitions, but getting the setup correct for booting has eluded me.  I've tried GPT and MBR, with LVM and without.  The only thing left to try is ZFS.  Hummmmm. Now that 16.04 supports ZFS ... something new to attempt.  Need to test this out inside a VM first.

Good luck to you. Think I've imparted all I can here.  Did just see a fairly advance ZFS boot how-to with encryption, which provided some step-by-step info on using dm-crypt which might shed some light on doing it manually. It was a bootstrap install (minimal) in that guide. Not certain I'm willing to go to that effort (about 3 hrs they claim) to work through all the steps.


I somehow managed to get Ubuntu 14 LTS to install an encrypted LUKS with only a boot and a primary partition, I still have it working as of today. The problems I had however were weird, such as having to deal with grub settings (the splash and nomodeset switches) and really funky booting into Unity which is why I went over to Xubuntu. I also got some kernel panic problems later on but I think that might be a voltage undersupply to my USB drive while running 6 USB disks on the same motherboard.

I guess unless someone else comes around to try this issue I'm guessing that it's case closed for now. But thanks for the help!

---

### Post by pandoragami on 2016-07-11
I managed to easily fix the problem by using a second linux system to log into and open the LUKS encrypted folder on the USB disk. I then installed Logical Volume Manager using 


```
add-apt-repository "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) $(lsb_release -sc) universe"
apt-get update
apt-get install system-config-lvm
```

And selected the logical drive available. I deleted the ubuntu-vg/swap_1 and then I resized the root partition to fully use the disk space. 

Note that this software wasn't able to delete the said swap partition for the same reason as before, because it was in use so a second live system must be used on the unmounted LUKS
root and swap partitions in order to fix the problem.

---

### Post by pandoragami on 2016-07-11
Here's another thread on the subject [http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume)

---

