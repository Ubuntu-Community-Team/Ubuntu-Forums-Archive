---
title: "Accidently added a Second LVM to my Swap"
date: 2020-09-28
forum: General Help
---

### Post by afrodeity on 2020-09-28
If I lsblk

```
sda                8:0    0 223.6G  0 disk 
&#9492;&#9472;sda1             8:1    0 223.6G  0 part 
  &#9500;&#9472;ubuntu--vg-root
  &#9474;              253:0    0 252.2G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1
                 253:1    0   980M  0 lvm  [SWAP]
sdb                8:16   0  29.6G  0 disk 
&#9492;&#9472;sdb1             8:17   0  29.6G  0 part 
  &#9492;&#9472;ubuntu--vg-root

```

was in the process of adding a 30GB LVM and resizing my root according to [steps over here]("https://www.cyberciti.biz/faq/howto-add-disk-to-lvm-volume-on-linux-to-increase-size-of-pool/")

I got as far as the following step: 

> sudo lvm lvextend -l +100%FREE /dev/ubuntu-box-1-vg/root

and issued this command: 

```
sudo lvm lvextend -l +100%FREE /dev/ubuntu-vg/root
```

but realise it should have been something like this:

> sudo lvm lvextend -l +100%FREE /dev/mapper/ubuntu--vg-root

Not sure how to get out of this one, am busy studying my options, including, [extend and reduce.]("https://www.linuxsysadmins.com/extend-and-reduce-lvm-in-linux/")

Would appreciate any advice or assistance, since I don't want to destroy my primary LVM.

Both LVMs are now root but the extra space has been allocated to my swap, it seems.

```
cat /proc/swaps
Filename				Type		Size	Used	Priority
/dev/dm-1                               partition	1003516	0	-2

```

---

### Post by afrodeity on 2020-09-28
If I comment out my swap in /etc/fstab

reboot and attempt to turn swapoff, the command fails:

```
sudo swapoff ubuntu--vg-swap_1
swapoff: ubuntu--vg-swap_1: swapoff failed: Invalid argument
```

I guess I have to reduce the size of the LVM group, [somehow]("https://tldp.org/HOWTO/LVM-HOWTO/reducelv.html")

---

### Post by afrodeity on 2020-09-28
I I make sure the disk is unmounted:

```
umount /dev/sdb1
umount: /dev/sdb1: not mounted.
```

```
sudo vgreduce ubuntu-vg /dev/sdb1

  Physical volume "/dev/sdb1" still in use
afropunk@afropunk:~$ sudo umount /dev/sdb1

```


still fails. I guess I have to boot with a live disk, and try this when both disks are no longer in use?

UYet, it still appears feasible to do this without using a live disk:

According to this[ thread on ServerFault:]("https://serverfault.com/questions/864965/logical-volume-in-use-cannot-remove-logical-volume")

Not for the faint-hearted, am going to have dinner and attend to the matter in the morning

---

### Post by afrodeity on 2020-09-28
```
sudo pvdisplay /dev/ubuntu-vg
  Failed to find device for physical volume "/dev/ubuntu-vg"
```

doesn't display the physical disks that form the ubuntu-vg lvm group,

nor does this:
```
sudo pvdisplay /dev/mapper/ubuntu--vg-root
  Failed to find device for physical volume "/dev/mapper/ubuntu--vg-root".
```

---

### Post by afrodeity on 2020-09-28
```
sudo lvreduce -L 223.57G /dev/mapper/ubuntu--vg-root
  Rounding size to boundary between physical extents: 223.57 GiB.
  WARNING: Reducing active and open logical volume to 223.57 GiB.
  THIS MAY DESTROY YOUR DATA (filesystem etc.)
Do you really want to reduce ubuntu-vg/root? [y/n]: y
  /dev/sdb1: BLKDISCARD ioctl at offset 1032847360 size 30693916672 failed: Input/output error.
  Size of logical volume ubuntu-vg/root changed from <252.16 GiB (64552 extents) to 223.57 GiB (57234 extents).
  Logical volume ubuntu-vg/root successfully resized.
```

now to remove the second drive from the vg?

---

### Post by TheFu on 2020-09-28
/dev/ubuntu-vg/root ==  /dev/mapper/ubuntu--vg-root 
Those both point to the same DM device.  They use symbolic links. Nothing special about them. They are 100% normal, symlinks, just like any others on the box.

In general, you don't need lvm + lvextend as an option.  Just use **lvextend** as the command.
Be very careful using lvreduce or lvresize. Always have backups before using either.

I'd like to see some facts before saying anything more.
```
sudo pvs
sudo vgs
sudo lvs
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
commands + output, please.  All wrapped in code tags.
Might be helpful to see the ftab file contents too. Please.

For swap, I'd like to see **swapon -s**.

Then if you can clearly say what you'd like changed about each LV, someone can help.

pvdisplay, vgdisplay and lvdisplay are the old-school commands that show way more detail that we need for stuff like this. Let's keep it short and to the point, unless you want specific striping across different PVs.

LVM is the system name. Once we know LVM is involved, we generally don't need anything more that say "lvm" anywhere.
LV is a logical volume.
VG is a volume group.
PV is a physical volume.
There is nothing called an "lvm group."  It is important to use the correct terms for the correct objects to prevent confusion in communications.  Please.

When I see the other commands you are throwing at the shell, it looks like you aren't using the manpages to get the correct options required for each command.  When working with LVM, you'll need to lookup those options.  The same applies to swapon and swapoff commands.  Incorrect and partial options aren't sufficient.

So ... here's one of my systems fstab files:
```
UUID=9CE4-930A  /boot/efi       vfat    utf8,umask=007,gid=46 0       1
/dev/vgubuntu-mate/root /       ext4    errors=remount-ro 0 1
/dev/vgubuntu-mate/home /home   ext4    errors=remount-ro 0 1
/dev/vgubuntu-mate/swap_1 none  swap    sw      0       0
```
See how the LVs are all in /dev/vgubuntu-mate/?
```
regulus:/dev/vgubuntu-mate$ ll
total 0
drwxr-xr-x  2 root root  100 Sep 28 15:51 ./
drwxr-xr-x 20 root root 4120 Sep 28 15:51 ../
lrwxrwxrwx  1 root root    7 Sep 28 15:51 home -> ../dm-2
lrwxrwxrwx  1 root root    7 Sep 28 15:51 root -> ../dm-0
lrwxrwxrwx  1 root root    7 Sep 28 15:51 swap_1 -> ../dm-1
```
They are just symlinks to device-mapper objects in /dev/.  I can also see symlinks in the /dev/mapper/ directory:
```
regulus:/dev/mapper$ ll
total 0
drwxr-xr-x  2 root root     120 Sep 28 15:51 ./
drwxr-xr-x 20 root root    4120 Sep 28 15:51 ../
crw-------  1 root root 10, 236 Sep 28 15:51 control
lrwxrwxrwx  1 root root       7 Sep 28 15:51 vgubuntu--mate-home -> ../dm-2
lrwxrwxrwx  1 root root       7 Sep 28 15:51 vgubuntu--mate-root -> ../dm-0
lrwxrwxrwx  1 root root       7 Sep 28 15:51 vgubuntu--mate-swap_1 -> ../dm-1
```
They use slightly different names, but also point to exactly the same dm-? objects.  100% normal symbolic links.  When we run swapon/off or lvextend commands, we can use any of these three different file objects.  The dm-? files can change from boot to boot, so it is best to use the generated /dev/mapper/ or /dev/{vg-name}/{lv-name} files.  I prefer to use the 2nd option, since those make sense to my human brain and convey extra knowledge.  But you can use whatever you like.
My fstab was manually edited to use the /dev/{vg-name}/{lv-name} version for my sanity.  When we use LVM, we get rebuilt symlinks in those directories when the storage gets scanned during boot. Those symlinks are guaranteed to be correct, just like the symlinks for UUIDs are.   UUIDs are handy, if we don't have any other choice.  They are just symlinks too, BTW.  Look in /dev/disk/by-uuid/ and you'll see the UUID symlinks that point to the device-mapper files.

Hopefully, this can clarify why you see different names used in different arguments for swap and LV commands. They are probably pointing at the same things, but there are multiple different answers possible. That's all.  Without a firm understand of symlinks and how they are used under /dev/, it is easy to become confused.

---

### Post by afrodeity on 2020-09-29
This is what it looks like now after lvreduce. Would appreciate advice on what my options are. Not sure now what I did wrong per my first post, but yes, its possibly lack of a man page, modifier.

```
sudo pvs
  PV         VG        Fmt  Attr PSize    PFree  
  /dev/sda1  ubuntu-vg lvm2 a--  <223.57g      0 
  /dev/sdb1  ubuntu-vg lvm2 a--   <29.55g <28.59g

```

```
sudo vgs
  VG        #PV #LV #SN Attr   VSize   VFree  
  ubuntu-vg   2   2   0 wz--n- 253.11g <28.59g

```

```
sudo lvs
  LV     VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   ubuntu-vg -wi-ao---- 223.57g                                                    
  swap_1 ubuntu-vg -wi-a----- 980.00m      

```
```

lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                    SIZE TYPE FSTYPE      MOUNTPOINT
sda                   223.6G disk             
&#9492;&#9472;sda1                223.6G part LVM2_member 
  &#9500;&#9472;ubuntu--vg-root   223.6G lvm  ext4        /
  &#9492;&#9472;ubuntu--vg-swap_1   980M lvm  swap        
sdb                    29.6G disk             
&#9492;&#9472;sdb1                 29.6G part LVM2_member 
  &#9492;&#9472;ubuntu--vg-root   223.6G lvm  ext4        /
sr0                    1024M rom            

```

swapon -s
shows no summary of swaps, so I assume the swap is off, since I removed it from my fstab?

Not sure why the VG size is still 253G but lsblk reports an LV of 223G ...?

---

### Post by HermanAB on 2020-09-29
Hmm, in general, I find that using a swap file is less hassle and there is no speed difference.

---

### Post by TheFu on 2020-09-29
I was nearly complete with a reply, then firefox crashed.  Something is really wrong with firefox since I patched Saturday.  It has been crashing every few hours.  Got an updated version this morning and it appears to still be crashing.

I'm not going to re-write all of that. Sorry.  The gist is I still don't know what you think is wrong or what you actually did.  There are 2 PVs, but no command is shown where the 2nd PV was added to the VG, so that doesn't appear to have been a mistake.  What is it you believe is wrong? I can't guess.

---

### Post by afrodeity on 2020-09-30
As you can see /dev/sdb1 is 29G ssd. When I expanded the root file system, it didn't add as an expansion of the main file system, but rather, it extended my swap.

I can try to expand again so that the total will include the space on sdb1 which is still part of the LVM?

But need guidance on the correct method to do so, since clearly I missed something?

---

### Post by TheFu on 2020-09-30
> **afrodeity said:**
>  But need guidance on the correct method to do so, since clearly I missed something?

I can agree with this.  LVM is the generic term for the system, not any specific thing.
PVs, VGs, and LVs are the object we can manipulate.  [https://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](https://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

There are a number of LVM system tutorials. Create a virtual machine, add a few fake, tiny, HDDs to it and play with the commands inside that VM as a sandbox to learn the LVM system and try out stuff. Inside a VM, you can't do any harm.  1MB is just as good as 100GB for a fake HDD.

I have no idea how a second partition got added to a VG unless a specific command was used - like pvcreate or vgcreate.  lvextend can't do it.
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                    SIZE TYPE FSTYPE      MOUNTPOINT
sda                   223.6G disk             
&#9492;&#9472;sda1                223.6G part LVM2_member 
  &#9500;&#9472;ubuntu--vg-root   223.6G lvm  ext4        /
  &#9492;&#9472;ubuntu--vg-swap_1   980M lvm  swap        
sdb                    29.6G disk             
&#9492;&#9472;sdb1                 29.6G part LVM2_member 
  &#9492;&#9472;ubuntu--vg-root   223.6G lvm  ext4        /
```
That shows that the "root" LV is spanning sda1 and sdb1. Isn't that what you wanted?  I think it is a bad idea to span file systems across multiple physical devices, but hey, it's your machine, not mine.  Last time I spanned a file system like that, I lost 80% of my data.
I don't see that swap_1 was extended.
When you ran 
```
sudo lvextend -l +100%FREE /dev/ubuntu-vg/root
```
is there a reason you didn't extend the file system at the same time using the **--resizefs ** option? If you don't do that, then you need to run another command to resize the file system.  I always just include the command at the lvextend time to make my life easier.  **resize2fs** appears to be the command.

BTW, **lvreduce** is a very dangerous command. Only use that when you have 100% backups for everything first.  To remove a PV from use inside a VG, well - I've never done that. Let me check the manpage. Looks like **vgreduce** is the command.
> vgreduce removes one or more unused PVs from a VG. Seems like that is what you are saying you want to accomplish. Appears there are many caveats to using the command.

When I'm looking for LVM related commands, I know they are in 3 different groups.  
[LIST=1]
[*]PV
[*]VG
[*]LV
[/LIST]
To see all the LV related commands, in a terminal, I'll enter lv{tab}{tab} ... and the list will be shown.  create, remove, extend, reduce, change and convert.  I ignore all the commands that begin with "lvm" - those are left over from the 1990s, I'm guessing.
To see all the VG related commands, in a terminal, I'll enter vg{tab}{tab} ....
To see all the PV related commands, in a terminal, I'll enter pv{tab}{tab} ....
They all have create, remove, extend, reduce, change and convert commands. 

And I always use the --resizefs with lv* commands.  This only works with ext4 file systems, so if anyone uses jfs or xfs or one of the other file systems, they are on their own and need to manually resize up/down the file system later.

I'm sorry we seem to be unable to communicate. That's all my fault. Hopefully, someone else will jump in and help or translate where we are failing.

---

### Post by afrodeity on 2020-10-07
Just an update at how I resolved the problem, it appears that due to eyestrain, I had neglected a crucial step lvmextend, and then had gone back instead of forward.

So after doing the above, I issued the following:
 
```

sudo lvm lvextend -l +100%FREE /dev/ubuntu-vg/root

sudo resize2fs -p /dev/mapper/ubuntu--vg-root

```

and so the extra GB are now showing up as part of my root file system, and if I lsblk
```

sda                    8:0    0 223.6G  0 disk 
&#9492;&#9472;sda1                 8:1    0 223.6G  0 part 
  &#9500;&#9472;ubuntu--vg-root  253:0    0 252.2G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1
                     253:1    0   980M  0 lvm  
sdb                    8:16   0  29.6G  0 disk 
&#9492;&#9472;sdb1                 8:17   0  29.6G  0 part 
  &#9492;&#9472;ubuntu--vg-root  253:0    0 252.2G  0 lvm  /

```

---

### Post by TheFu on 2020-10-07
There's no reason to use "lvm lvextend", just use "lvextend" as the command.  Every character is an opportunity for a bug. Limit the characters for all commands, when possible. As said in post #11 above, if 
```
sudo lvextend **--resizefs** -l +100%FREE /dev/ubuntu-vg/root
```
had been used, then all would have been done. No need for a separate resize2fs command.

Allocating all the available storage in a VG can break things, like LVM *snapshots* which are commonly used for perfect backups that don't have any corrupt data due to data changing during backup runs. An snapshots is one of the most important capabilities for any volume manager.  Using "+100%FREE" means storage needs to be ordered.

Glad you figured it out.

---

### Post by afrodeity on 2020-10-09
Ah Fu, but of course, that's what I omitted both times, thank you.:popcorn:

---

