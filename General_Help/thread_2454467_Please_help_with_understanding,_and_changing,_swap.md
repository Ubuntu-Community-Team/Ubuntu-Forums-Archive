---
title: "Please help with understanding, and changing, swap: LUKS, LVM"
date: 2020-11-30
forum: General Help
---

### Post by Paddy Landau on 2020-11-30
[FONT=arial black]Background[/FONT]

I installed Ubuntu 20.04 using its default full-disk encryption, using the entire disk (so everything else was overwritten). The Ubuntu installation created three partitions:

[LIST]
[*]/dev/nvme0n1p1 (512MiB) EFI System Partition
[*]/dev/nvme0n1p2 (732 MiB) /boot
[*]/dev/nvme0n1p3 (475GiB) System partition
[/LIST]
The Ubuntu installation encrypted the System partition with LUKS (version 2): /dev/mapper/nvme0n1p3_crypt

On that, it created a LVM with two virtual partitions, viz. root and swap_1. Here is the full structure:
```
$ sudo pvscan
  PV /dev/mapper/nvme0n1p3_crypt   VG vgubuntu        lvm2 [<475.71 GiB / 0    free]
  Total: 1 [<475.71 GiB] / in use: 1 [<475.71 GiB] / in no VG: 0 [0   ]
```
```
$ sudo vgscan
  Found volume group "vgubuntu" using metadata type lvm2
```
```
$ sudo lvscan
  ACTIVE            '/dev/vgubuntu/root' [474.75 GiB] inherit
  ACTIVE            '/dev/vgubuntu/swap_1' [980.00 MiB] inherit
```
As you can see, the swap is a virtual partition of 980 MiB.

[FONT=arial black]First, my question about the swap[/FONT]

I had understood that Ubuntu 18.04 and after used a swap file rather than a swap partition by default, so I was surprised to find that it used a swap partition.

I know that an SSD needs a certain flexibility to prevent overuse of a specific area, thereby causing it to fail. Wouldn't a swap file be better than a swap partition on an SSD?

**Second, my request about the swap**

I wish to increase the size of the swap, because sometimes I use applications that use a lot of data (virtual machines, video editing, etc.).

I might also want to enable hibernation, if that's possible, so I'd need to increase swap size significantly. However, this is not a must-have; I'm prepared to accept that I can't use hibernate.

So, bearing this in mind, what is the best way to go about increasing the swap size?

[LIST=1]
[*]Using a Live CD, decrease the size of the root virtual partition and increase the size of the swap virtual partition?
[*]Using a Live CD, delete the virtual swap partition, increase the size of the root partition, and create a swap file (amending /etc/fstab accordingly)?
[*]Something else?
[/LIST]
And…

Whichever turns out to be the best way, how exactly do I go about it? I have enough knowledge of LVM to be dangerous! In other words, I'm fully familiar with the concepts, but I'm unpracticed at using it.

*Thank you*

---

### Post by Dennis N on 2020-11-30
Swapfile - I understand that you get a swapfile when there is no swap partition found by the installer during installation.

Increasing swap - Option (2) looks risk free. I would try that but not bother with increasing the size of the root logical volume - it already takes up 474 G of 475 G available.

Option (1) requires use of LVM commands lvreduce and lvextend.

---

### Post by TheFu on 2020-11-30
> I know that an SSD needs a certain flexibility to prevent overuse of a specific area, thereby causing it to fail. Wouldn't a swap file be better than a swap partition on an SSD?
No. There's no difference, except the swap file has a tiny bit more overhead due to the file system. This assumes you won't hibernate.

We need more detailed information to help you with the next questions.
Use
```
sudo pvs
sudo vgs
sudo lvs
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint
free -hm
```
to provide that information. It is very important that code tags be used and you show both the commands, all options and output. Those commands provide some redundant overlap and most of the options are here to prevent showing fake-storage devices which are not important at all.

It looks like the installation has screwed you by allocating all the storage to the root LV. I can see 2 solutions to this. There's the easy way and there's the "right" way.  If the install is recent and you plan to use it more than a year, I'd go the more-hassle-but-right way.  For a short-term need, I'd go with the easy solution.

The installer allocating more than 35-50G to the "root" LV is a huge failure in my mind. Here's my desktop disk layout:
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   17G   11G  5.0G  69% /
/dev/mapper/vgubuntu--mate-home ext4   12G  7.6G  3.7G  68% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi

$ free -hm
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       928Mi       229Mi       7.0Mi       2.7Gi       2.7Gi
Swap:         4.1Gi        47Mi       4.1Gi
```

I want the smallest "root" LV I can have.
Then I want the "home" LV to be sized for that I'll need in the next few months.  With LVM, increasing an LV is trivial, 5 seconds.  
But reducing an LV is a huge hassle. To reduce the "root" LV will require booting from alternate media so it is unused. Because you've used encryption (I do as well), that means getting to the LVM objects required unlocking the encrypted container first. Depending on the live-boot environment that you use, just clicking in a file manager might prompt you for access. Be certain that you know the name of the encrypted container.  If the file manager doesn't make it easy, you'll need to use **cryptsetup** to open the volume, then **vgchange -ay** to activate the LVM, then **lvreduce --resizefs** ... yadda, yadda, yadda.  Basically it is like an onion. Each layer has to be unwrapped and handled in the proper order going in, changing things, and coming back out.

You decide which method.

BTW, > Using a Live CD, delete the virtual swap partition, increase the size of the root partition, and create a swap file (amending /etc/fstab accordingly)? actually doesn't require using a Live CD.  You can do this on the running system.

---

### Post by TheFu on 2020-11-30
I don't think hibernation works with swapfiles and definitely not inside LVM + LUKS encryption.
I use standby with LVM + LUKS encryption, nightly and have for years. It works.

---

### Post by Paddy Landau on 2020-11-30
> **Dennis N said:**
> Swapfile - I understand that you get a swapfile when there is no swap partition found by the installer during installation.
Thanks. Is it automatic, so that if I get rid of the swap partition, will Ubuntu automatically create a swap file?
> **TheFu said:**
> No. There's no difference, except the swap file has a tiny bit more overhead due to the file system.
That's good to know.
> **TheFu said:**
> I want the smallest "root" LV I can have.
Then I want the "home" LV to be sized…
It looks like the installation has screwed you by allocating all the storage to the root LV.
The "root" is for the entire system, including /home. They're not separate partitions. I'm happy to stick with that, because when the time comes to upgrade to 22.04, I'll reinstall from scratch rather than upgrading from 20.04 to 22.04. I maintain regular multiple full backups of all of my data, so data loss is not an issue.
> **TheFu said:**
> We need more detailed information…
Here are my answers.
```
$ sudo pvs
  PV                          VG       Fmt  Attr PSize    PFree
  /dev/mapper/nvme0n1p3_crypt vgubuntu lvm2 a--  <475.71g    0
```
```
$ sudo vgs
  VG       #PV #LV #SN Attr   VSize    VFree
  vgubuntu   1   2   0 wz--n- <475.71g    0
```
```
$ sudo lvs
  LV     VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   vgubuntu -wi-ao---- 474.75g
  swap_1 vgubuntu -wi-ao---- 980.00m
```
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
df: /run/user/1000/doc: Operation not permitted
Filesystem                Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu-root ext4  467G  136G  307G  31% /
/dev/nvme0n1p2            ext4  705M  206M  448M  32% /boot
/dev/nvme0n1p1            vfat  511M   40M  472M   8% /boot/efi
```
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                    SIZE TYPE  FSTYPE      MOUNTPOINT
nvme0n1                 477G disk              
|-nvme0n1p1             512M part  vfat        /boot/efi
|-nvme0n1p2             732M part  ext4        /boot
`-nvme0n1p3           475.7G part  crypto_LUKS 
  `-nvme0n1p3_crypt   475.7G crypt LVM2_member 
    |-vgubuntu-root   474.8G lvm   ext4        /
    `-vgubuntu-swap_1   980M lvm   swap        [SWAP]
```
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           15Gi       2.6Gi       6.1Gi       795Mi       6.6Gi        11Gi
Swap:         979Mi          0B       979Mi
```
> **TheFu said:**
> If the install is recent and you plan to use it more than a year, I'd go the more-hassle-but-right way.  For a short-term need, I'd go with the easy solution.
Fairly recent, and I'll go for the "right way" if it's more robust.
> **TheFu said:**
> … reducing an LV is a huge hassle.
That's OK; I'm happy to delete the swap virtual partition, and increase root into that unused space.
> **TheFu said:**
> … clicking in a file manager might prompt you for access.
The file manager in Ubuntu is Nautilus, and I don't know how to go about doing that in Nautilus. I'll have to use the command line.
> **TheFu said:**
> BTW,  actually doesn't require using a Live CD.  You can do this on the running system.
LVM is mighty flexible! That's good to know.
> **TheFu said:**
> I don't think hibernation works with swapfiles and definitely not inside LVM + LUKS encryption.
It might not work with swap files, but it definitely can work with a swap partition in LUKS and LVM — I've [made it work]("https://help.ubuntu.com/community/ManualFullSystemEncryption") (albeit that the link is slightly out of date).

---

### Post by TheFu on 2020-11-30
The "right way": [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)

The "easy way" would be to 
[LIST=1]
[*]disable the swap, **swapoff**
[*]delete the swap LV, **lvremove**
[*]create a swap file inside the "root" LV filesystem, **fallocate** 
[*]format the swap file into swap, **mkswap** 
[*]lock down the swap file permissions/ownership, 600 root:root, then 
[*]fix the fstab to use the swap file, removing the swap LV - **sudoedit**
[/LIST]
I think this is lazy, wrong, and poor storage architecture.

Of course, there are different opinions on all of this.

---

### Post by GhX6GZMB on 2020-11-30
> **TheFu said:**
> I don't think hibernation works with swapfiles

I've never been able to get hibernate to work with a swapfile, but it works perfectly with a swap partition. I'm aware that the *ubuntu developers disencourage hibernate and have it disabled as default.

---

### Post by roykcaroll456 on 2020-11-30
[COLOR=#000000]*there[']("https://www.rumblerum.com/")s no difference, except the swap file has a tiny bit more overhead due to the file system.*[/COLOR]

---

### Post by Paddy Landau on 2020-12-01
> **TheFu said:**
> The "right way": [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)
That's probably overkill for me. I'll stick with one partition for my root and home.
> **TheFu said:**
> The "easy way" would be to…
Thank you. I'm going to go this way, partly because it matches my needs, partly because it's safer, even if it's "lazy, wrong, and poor storage architecture" :wink: :lol:

I realise that this means going without hibernate, and that's OK, I'll live with it.
> **ml9104 said:**
> I've never been able to get hibernate to work with a swapfile, but it works perfectly with a swap partition. I'm aware that the *ubuntu developers disencourage hibernate and have it disabled as default.
Is it discouraged because of the complications with a swap file? Or is there a fundamental reason behind the thinking?

---

### Post by Paddy Landau on 2020-12-01
I have gone through the process.

Here are my results.
> **TheFu said:**
> disable the swap, **swapoff**
```
$ sudo swapoff --all
```
> **TheFu said:**
> fix the fstab … removing the swap LV - **sudoedit**
Edited /etc/fstab to remove the swap.
> **TheFu said:**
> delete the swap LV, **lvremove**
```
$ sudo lvremove vgubuntu/swap_1
```
Extend the root partition:
```
$ sudo lvscan
  ACTIVE            '/dev/vgubuntu/root' [474.75 GiB] inherit

$ sudo lvextend --extents=100%FREE --resizefs vgubuntu/root
  New size given (245 extents) not larger than existing size (121536 extents)

$ sudo lvscan
  ACTIVE            '/dev/vgubuntu/root' [474.75 GiB] inherit
```
As you can see, the root partition wasn't extended, so I now have a little wasted space on the disk.

Why is this, do you know? Did I enter the command incorrectly?
> **TheFu said:**
> create a swap file inside the "root" LV filesystem, **fallocate**
```
$ sudo fallocate --length=4g /swapfile
```
> **TheFu said:**
> lock down the swap file permissions/ownership, 600 root:root
```
$ sudo chmod go-r /swapfile
```
> **TheFu said:**
> format the swap file into swap, **mkswap**
```
$ sudo mkswap --label=swap /swapfile
sudo swapon /swapfile
```


> **TheFu said:**
> fix the fstab to use the swap file … - **sudoedit**
```
/swapfile swap swap sw 0 0
```
I've restarted my computer and it seems to work…

BUT…

See my next post.

---

### Post by Paddy Landau on 2020-12-01
On startup, after entering the LUKS passphrase, the computer stalls for a short while. The error messages read:
```
  Volume group "vgubuntu" not found
  Cannot process volume group vgubuntu
  Volume group "vgubuntu" not found
  Cannot process volume group vgubuntu
  Failed to find logical volume "vgubuntu/swap_1"
Gave up waiting for suspend/resume device
```
Can you tell me why it's still looking for vgubuntu/swap_1? It's not in my fstab, and I don't know where else it could be.

EDIT: I found only comments relating to the deleted swap:
```
$ sudo grep -FI --recursive 'vgubuntu/swap_1' /etc  
/etc/lvm/backup/vgubuntu:description = "Created *after* executing 'lvremove vgubuntu/swap_1'"
/etc/lvm/archive/vgubuntu_00001-41805311.vg:description = "Created *before* executing 'lvremove vgubuntu/swap_1'"
```

**EDIT: Solved!**

It turns out that initramfs (whatever that is!) keeps a record of the swaps in case of resuming from hibernation, and needs to be updated.
```
$ sudo update-initramfs -uk all
update-initramfs: Generating /boot/initrd.img-5.4.0-56-generic
update-initramfs: Generating /boot/initrd.img-5.4.0-54-generic
```
This did the trick.

The boot still starts with one error:
```
  Volume group "vgubuntu" not found
  Cannot process volume group vgubuntu
```
It would be nice to eliminate that error, but I suppose that's for a new thread.

---

