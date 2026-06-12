---
title: "Swap partition/file in new install"
date: 2021-09-12
forum: General Help
---

### Post by pslacker on 2021-09-12
[First of all, for anyone who saw my recent thread about putting Xubuntu onto my laptop, I did it and all seems to be going well (I ended up formatting the drive, and making Xubuntu the sole OS).]

When I was installing, there was no mention of any swap partition or file until the final confirmation screen, which read: 
[I]
[COLOR="#0000FF"]If you continue, the changes listed below will be written to the disks. Otherwise, you will be able to make further changes manually. 

WARNING: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted. 

The following partitions are going to be formatted: 
LVM VG vgxubuntu, LV root as ext4 
LVM VG vgxubuntu, LV swap_1 as swap partition #1 of SCSI1 (0,0,0) (sda) as[/COLOR][/I]

(Curiously, the last line cut off right after "as", though I don't know why...) 

So it appears that a swap partition was automatically created, even though I didn't specify one. That's okay — I want to be able to hibernate — but I have read that these days a swap file is preferred to a partition, thus was a bit surprised that the only option was simply to accept the partition the installer said it was going to make! 

So my questions are:
1) should I create a swap *file* and get rid of the swap *partition*? 
1a) how would I do that? (Yes, I fully intend to Google it, but a starting suggestion is always welcome) 
2) how do I determine the size of the swap partition the installer made? If I wanted to adjust it, is that something I'd use gparted for?
3) come to think of it, would I simply use gparted to find the swap partitions's size? (I'm in bed now or I'd try it myself!) 

BTW if this makes a difference, Xubuntu was installed on a 500 GB drive that has nothing else on it. 

Many thanks for any guidance.

---

### Post by deadflowr on 2021-09-13
No need to mess around and make more swap on a system that already has swap setup.
You can use the free command to see how much you have and how much is currently in use.
You can run it with the human-readable option -h for easier to understand output:
```
free -h 
```

If you want to learn more on swap on Ubuntu see:
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by Impavidus on 2021-09-13
A swap file is easier to resize later, a swap partition is easier to share with a different OS install. Further, I think a swap partition is required if you want to use hibernation.

Now it appears you use LVM, basically a more advanced layer of partitioning on your hard drive. That makes your swap partition easy to resize as well, but you need LVM tools for that. gparted doesn't handle LVM.

---

### Post by TheFu on 2021-09-13
I'd bet there is a swap_1 LV, but don't know the size. I don't know what the default LVM setup under lubuntu is either. If you'd like some help, a little information would be good.

```
sudo pvs
sudo vgs
sudo lvs
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
With those commands, we should know nearly everything about the disk layout.

For example, 
```
~$ sudo pvs
  PV         VG   Fmt  Attr PSize   PFree
  /dev/vda5  vg00 lvm2 a--  <29.50g    0
  /dev/vdb1  vg00 lvm2 a--  <10.00g 4.39g

~$ sudo vgs
  VG   #PV #LV #SN Attr   VSize  VFree
  vg00   2   3   0 wz--n- 39.49g 4.39g

~$ sudo lvs
  LV     VG    Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home   vg00 -wi-ao---- 12.00g                                               
  root   vg00 -wi-ao---- 19.00g                                               
  [COLOR="#FF0000"]swap_1[/COLOR] vg00 -wi-ao----  [COLOR="#FF0000"]4.10g[/COLOR]

~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME             SIZE TYPE FSTYPE      MOUNTPOINT
sr0             1024M rom          
vda               30G disk          
&#9500;&#9472;vda1           512M part vfat        /boot/efi
&#9500;&#9472;vda2             1K part          
&#9492;&#9472;vda5          29.5G part LVM2_member
  &#9500;&#9472;vg00-root     19G lvm  ext4        /
  &#9500;&#9472;vg00-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vg00-home     12G lvm  ext4        /home
vdb               10G disk          
&#9492;&#9472;vdb1            10G part LVM2_member 
  &#9492;&#9472;vg00-root     19G lvm  ext4        /
  
```
Simple.  The swap is swap_1 and 4.10G in size.

I prefer 
a) having an LV over a swap partition or swap file.  Personal preference.
b) leaving some space unused inside the VG, for needs like snapshots and last minute growth of other LVs in 5 seconds.  For example, I can extend any of the existing LVs using the free 4.39G of space.  With LVM, the tremendous flexibility comes by NOT using all the storage for mounted file systems.  I needed more storage than the first HDD had, so I added another and merged it into a single VG, vg00.  From that point on, any LV could use that space to grow or for snapshots.

It comes down to personal preference.  I know that some things didn't work (don't work?) with swapfiles that have worked for 20 yrs with swap partitions and swap LVs. Just not enough testing and a desire to push that junk onto the users.  For a non-LTS, I suppose that could be acceptable, but for an LTS, everything should work, perfect, always.

---

### Post by GhX6GZMB on 2021-09-13
I'm confused. Is this a VM setup or a real install?

This reply only applies if it's a real install.

Redo from start, and define the partioning first (in your mind or on paper).

During installation, select manual partitioning, and if you want Hibernation, define at least these partitions:
/ = 20...30 GB
SWAP = RAM size plus a bit
/home = all of the rest, unless you need other partitions or other free space.

Format all partitions to ext4 (IIRC this is not needed on SWAP which has a different format).

---

### Post by pslacker on 2021-09-13
Thanks again for all the responses.

To clarify, let me say that my concerns are really that a) I want to be able to hibernate the computer, b) that the swap size is appropriate (given 8 GB of RAM), and that c) when it comes to using either a swap file or swap partition, I'm using whatever approach is currently recommended.

Currently it seems like I have only 1 GB of swap space, that the swap is on a partition (even though I think a file is more recommended for my situation), and that I can't hibernate the computer.


Here's the info @TheFU requested:

```
~$ sudo pvs
  PV                     VG        Fmt  Attr PSize    PFree
  /dev/mapper/sda6_crypt vgxubuntu lvm2 a--  <464.53g    0 


~$ sudo vgs
  VG        #PV #LV #SN Attr   VSize    VFree
  vgxubuntu   1   2   0 wz--n- <464.53g    0 


~$sudo lvs
  LV     VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   vgxubuntu -wi-ao---- 463.57g                                                    
  swap_1 vgxubuntu -wi-ao---- 980.00m   


~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                     SIZE TYPE  FSTYPE      MOUNTPOINT
sda                    465.8G disk              
&#9500;&#9472;sda1                   512M part  vfat        /boot/efi
&#9500;&#9472;sda2                     1K part              
&#9500;&#9472;sda5                   731M part  ext4        /boot
&#9492;&#9472;sda6                 464.6G part  crypto_LUKS 
  &#9492;&#9472;sda6_crypt         464.5G crypt LVM2_member 
    &#9500;&#9472;vgxubuntu-root   463.6G lvm   ext4        /
    &#9492;&#9472;vgxubuntu-swap_1   980M lvm   swap        [SWAP]
sr0                     1024M rom[/I]

```
And to answer ml9104, this *is* a real install. 

If I have to reinstall to enable hibernation, okay ... but I'm really confused:  Do most people never hibernate their computers?  I don't understand why the installation defaults would just assume no one ever does this, and not even give any option for allowing this during setup.  It just seems like such a hassle to have to do this all over again just to enable what I thought was basic functionality (I realize no one here is on the Xubuntu development team, so I'm not criticizing you!  I'm just surprised, that's all.)

My brain is full at the moment, but I know I'll have more questions :|  Thanks for any you can answer.

Jamie

---

### Post by TheFu on 2021-09-14
First, you have an encrypted/lvm installation.  Whenever posting to these forums, always include "encrypted/lvm install" to get the best help possible. It is VERY important.

If you use encryption, DO NOT HIBERNATE!!! There are security reasons.  It is like putting a tarp over an open roof, but then creating holes in the tarp to let the sunshine inside.  It is nice when it is sunny outside, but terrible in a rain storm.

```
~$ sudo vgs
VG #PV #LV #SN Attr VSize VFree
vgxubuntu 1 2 0 wz--n- <464.53g 0

~$sudo lvs
LV VG Attr LSize Pool Origin Data% Meta% Move Log Cpy%Sync Convert
root vgxubuntu -wi-ao---- 463.57g
swap_1 vgxubuntu -wi-ao---- 980.00m
```
Please edit your post above to use "code tags", so all the output lines of and is readable.  Hard to read data makes it less likely that people will bother reviewing it.

That "root" LV is 10x too large ... actually 35G is my "this is huge" size for a root LV.  The root LV should hold the OS and application installs.  This is helpful for upgrades, backups, and restores later.  /home really should be in a different LV - call it "home".  Start with 50G per user.
I think the swap of 980MB (~1G) is too small for a typical desktop.  I'm convinced that 4.1G is the only answer needed for "how big should a desktop swap file be?"  May/June 2020, there was a long thread in these forums about sizing of swap.

If you look at my post above, you can see my swap is 4.1G.  [Https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](Https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) is a post on what I think is the ideal layout for a system just like yours.  It is for my laptop, with encryption and LVM. The summary is:
```
$ sudo lvs
  LV      VG        Attr       LSize   Pool Origin Data%
  home-lv ubuntu-vg -wi-ao----  75.00g
  root    ubuntu-vg -wi-ao----  25.00g 
  stuff   ubuntu-vg -wi-ao---- 100.00g
  swap_1  ubuntu-vg -wi-ao----   4.10g
```
[LIST]
[*]My "root" is fine, but 35G wouldn't be atrocious. Backups happen daily, except when traveling.
[*]My "home" is a little larger - I needed a little more storage over the last 3 yrs, since that system was installed. Backups happen daily, except when traveling.
[*]My "stuff" is for things that never need to be backed up. This is a laptop, so when I travel, I'll put some music and videos there for evening entertainment.
[*]And the swap is 4.1G in size.
[/LIST]
Add those LVs up and you can see I'm using ... 204GB.  My disk in that laptop is 500G.  Why only have 50% of the storage available?  Because it makes for a more flexible system and provides some capabilities NOT available if there isn't some free space left unallocated to LVs. For example, my backups create LVM snapshots, then I backup the snapshots. This means the backups won't have file corruption issues since the blocks in the snapshots are frozen and cannot be modified while the backups happen.

If you need help to modify the current setup to match this, start by finding an LVM tutor online. LVM on every Linux is the same, so don't worry about Ubuntu/Debian/Redhad/CentOS/Arch ... lvm is lvm.  There is no GUI.  Reducing the size, like you need to do for "root" is the dangerous part.  Because the default install used all the storage on the system, you can't just resize the swap LV larger.  LVM's flexibility comes by leaving lots/some free space.  Resizing larger for ext4 file systems inside an LV takes 5 seconds and can be performed while the file system is in-use. This is 100% safe.

If you don't want to fix the entire LVM layout, that's fine.  Just reduce the "root" LV by 100G - hopefully you haven't used all that storage already.  Then you can disable the swap and use lvextend to make it 4.1G  (or whatever size you like), then use mkswap to make the new swap LV formatted as swap, and re-enable it.  swapon and swapoff are the commands ... 

Because this storage is all inside a LUKS encrypted container and resizing LVs to smaller sizes has to be performed off-line, you'll need a flash boot "Try Ubuntu" disk.  then you'll need to manually open the LUKS container using cryptsetup - do not mount the LVs inside it. Those LVs need to be unused during the reduction commands.  The good news is that LVs are used in the fstab and generally the fstab doesn't need to be modified just because an LV is resized. Parts of an /etc/fstab:
```
/dev/ubuntu-vg/root   /         ext4   noatime,errors=remount-ro 0 1
/dev/ubuntu-vg/home   /home     ext4   noatime,errors=remount-ro 0 1
/dev/ubuntu-vg/stuff  /stuff    ext4   noatime,errors=remount-ro 0 2
/dev/ubuntu-vg/swap_1 none      swap   sw                        0 0
```

So, the fstab "devices" are /dev/{vgname}/{lvname} ... which I find handy to trace back what is connected where.

---

### Post by pslacker on 2021-09-14
@TheFu:

Thanks for such a detailed response.

I guess the depressing thing for me is the discovery that Xubuntu's defaults turn out to be so incredibly unrealistic. I'd hoped to tweak as I went along, bit by bit as I learned more about Linux and became more comfortable — but I see that's not the case.

That said, I'm clearly going to have to do a ton of research just to install Linux in the first place (that is, trash the current install, reformat the drive, and then set up everything manually). While the link you provided gives great information about the final settings I might choose, I'm not sure what keywords to use when searching for tutorials to help me even feel capable of following the instructions.

I'd guess **multiple partition LVM tutorial** would be a place to start, but would welcome other suggestions — both for accomplishing the install and any other core concepts that you would recommend.

---

### Post by TheFu on 2021-09-14
search terms: tutorial lvm linux

There are many different opinions about what a good disk layout is.  Encryption complicates everything. Mine comes from over 25 yrs as a UNIX/Linux admin.  I know I've never guessed perfect what storage needs to be where on any system, so flexibility gets me to never need a full reinstall over a rushed choice during an install.

With lvm, you can't just though commands at it. There is a required order. A process that can be different depending on the end goal and things that happen along the way.

I've posed exact lvm commands in these forums a few times, but those were for things I needed to accomplish. For encrypted setups, just let the installer do what it does, then fix it after the 2nd reboot.  For unencrypted installs, I have a little scrip that sets p the disk, partitions, sized and puts lvm setup as I like.  I do this work in a different terminal very early in the install process, before the storage screens happen, and choose "do something else" to connect each partion and LV to the needed mount locations.  The actual steps involved are beyond what most inexperienced admins would be comfortable attempting.   I think it is in the "if you have to ask how, then it isn't for you" realm.

Practising anything, including installs and disk setups, will make us better at doing it.

---

### Post by GhX6GZMB on 2021-09-14
@pslacker:
the problem is, that you apparently want an LVM/Encrypted install.
I don't know why.
But no installer on earth can help you here, you're on your own, sorry. So don't moan about "depressingly unrealistic defaults", please.

---

### Post by TheFu on 2021-09-14
The installers have to trade-off complexity with easy of used for the likely audience. There is no pleasing everyone.
If they created multiple LVs, someone would complain that it is too complex OR that the sizes for each LV are bad.  Linux people are full of opinions, including me.

But I've learned that LVM is best used by NOT allocating all the storage in a VG to the LVs.  If the installer did that, can you imagine the complaints?!  "Where's my total storage!"  Why wouldn't everyone want all the storage in a system provided? Try explaining that to normal users.  Bet you can't.

It is tough making reasonable defaults for an installation.

As for why to use encryption, there are many excellent reasons. No need to explain.  It is nice to be able to send in a storage device for warranty support without worrying what data it may contain.

---

