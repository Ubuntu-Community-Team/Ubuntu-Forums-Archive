---
title: "extended LVM volumes"
date: 2022-04-12
forum: General Help
---

### Post by noahdb on 2022-04-12
Hi there,

I have seen a few tutorials on this matter.  I am wondering if somebody can recommend the best way to increase the size of an LVM volume please?  Running ubuntu 20.04

Currently my LVM is 196G and want the volume to take up the entire drive space which is close to 2TB.

Any help is appreciated.

--- snip ----
```
&#10095; df -kh
Filesystem                                  Size  Used Avail Use% Mounted on
udev                                         32G     0   32G   0% /dev
tmpfs                                       6.3G  2.7M  6.3G   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv           196G  127G   60G  69% /
tmpfs                                        32G  8.2M   32G   1% /dev/shm
tmpfs                                       5.0M     0  5.0M   0% /run/lock
tmpfs                                        32G     0   32G   0% /sys/fs/cgroup
/dev/nvme0n1p2                              976M  208M  702M  23% /boot
/dev/nvme0n1p1                              511M  5.3M  506M   2% /boot/efi
/dev/loop0                                  111M  111M     0 100% /snap/core/12834
/dev/loop1                                   56M   56M     0 100% /snap/core18/2344
/dev/loop2                                   62M   62M     0 100% /snap/core20/1405
/dev/loop3                                   62M   62M     0 100% /snap/core20/1376
/dev/loop6                                   44M   44M     0 100% /snap/snapd/15177
/dev/loop5                                   44M   44M     0 100% /snap/certbot/1952
/dev/loop4                                   68M   68M     0 100% /snap/lxd/22526
/dev/loop7                                   68M   68M     0 100% /snap/lxd/22753
/dev/loop8                                   45M   45M     0 100% /snap/snapd/15314
/dev/loop9                                   56M   56M     0 100% /snap/core18/2284
tmpfs                                       6.3G   12K  6.3G   1% /run/user/1000
tmpfs                                       6.3G     0  6.3G   0% /run/user/996
```
--- snip ---

--- snip ---
```
nuc# lsblk -o name,size,fstype,label,mountpoint | grep -v 'snap'
NAME                        SIZE FSTYPE      LABEL MOUNTPOINT
nvme0n1                     1.9T
&#9500;&#9472;nvme0n1p1                 512M vfat              /boot/efi
&#9500;&#9472;nvme0n1p2                   1G ext4              /boot
&#9492;&#9472;nvme0n1p3                 1.9T LVM2_member
  &#9492;&#9472;ubuntu--vg-ubuntu--lv   200G ext4              /
```

---- snip ---


Cheers,
Noah

---

### Post by TheFu on 2022-04-13
An "lvm volume" isn't sufficient information.  Also, whenever posting terminal output, please
a) show the exact command run.
b) wrap the command and the output in forum 'code' tags - the advanced editor here (#) can do it, or you can use quote/bold/italic tags and replace those with "code".
c) for LVM stuff, we need to see output from 
sudo pvs
sudo vgs
sudo lvs
Depending on what those show, it could be a 5 second thing or something that you shouldn't do.  From what I'm seeing now, I think it is a 5 second thing, unless you want to fix the mess you've already begun.  / being 200G is much, much, much, too large.  It should be 35G. Also, swap should be a separate LV, as should /var/ and /home/.  These aren't huge issues to fix ... now. But if they aren't corrected, they will become a problem.

Some handy commands to put into aliases - both remove loop devices and other non-storage things that show up, but are useless 99.999% of the time:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs

```
That 'code block' above was created using a 'quote' tag, then I just swapped quote-->code at the beginning and end, leaving the other formatting alone.

---

### Post by Dennis N on 2022-04-13
If you want to increase the size of ubuntu-lv and use all the remaining free space in it's volume group, you could use this command:
 
```
sudo lvextend --resizefs --size +100%FREE /dev/ubuntu-vg/ubuntu-lv
```

It appears volume group ubuntu-vg was created using partition 3 (the only LVM member on your disk), and only ubuntu-lv exists in it. (Using the code tags, which preserve indentation, would make this clearer.)

---

### Post by TheFu on 2022-04-13
Using 100% of the VG storage prevents/removes all sorts of other great features from being possible with LVM - like snapshots.  Please consider that BEFORE doing it.  snapshots are critical for getting non-corrupted backups.

The trick to using LVM is to only allocate space to the specific LV when it is needed, not before.  I try to do it 3 months at a time, since the lvextend command takes just 5 seconds.

---

### Post by ActionParsnip on 2022-04-13
> **TheFu said:**
> Using 100% of the VG storage prevents/removes all sorts of other great features from being possible with LVM - like snapshots.  Please consider that BEFORE doing it.  snapshots are critical for getting non-corrupted backups.

The trick to using LVM is to only allocate space to the specific LV when it is needed, not before.  I try to do it 3 months at a time, since the lvextend command takes just 5 seconds.

+1 for this

---

### Post by noahdb on 2022-04-13
Thanks everybody for the advice.

For TheFu here is the LVM related command output

```

&#10095; sudo pvs
  PV             VG        Fmt  Attr PSize PFree
  /dev/nvme0n1p3 ubuntu-vg lvm2 a--  1.86t <1.67t
&#10095; sudo vgs
  VG        #PV #LV #SN Attr   VSize VFree
  ubuntu-vg   1   1   0 wz--n- 1.86t <1.67t
&#10095; sudo lvs
  LV        VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 200.00g

```

---

### Post by TheFu on 2022-04-13
So, that data confirms there is 1.67tb in the VG and 200GB has been allocated to a single LV.  The storage is an NVMe SSD. Fast. Also, that you aren't using any advanced LVM capabilities like thin provisioning.

You have some choices to make. 

Option A: the 5 second answer that won't fix anything?

Option B: Change the layout before there is too many issues. That will involve creating new LVs, moving files from the current ubuntu-lv into those new LVs, mounting each new LV using very common /etc/fstab lines.  Can also move from a swapfile to a swap "partition" (really a swap LV). That will make the swap have a few extra layers that aren't needed.  Block access is cleaner than file system on block access in a swap.  It isn't too hard, especially because you have lots and lots of unused storage that makes this easy at this point.
If this option, then you'll end up with something like this:
```
# Part  mount           part_type       fs_type size
1       /boot/efi       EFI             fat32   50MB (dual+boot needs more)
2       /boot           LINUX           ext2    600MB
3       LVM             LVM             na      Remaining storage
 root   /               LV              ext4    35GB
 home   /home           LV              ext4    40GB (will need to see what is being used already)
 var    /var            LV              ext4    1GB (will need to see what is being used already)
 swap   swap            LV/SWAP         swap    4.1GB
```

Since you are using 200G already, the above will need to be tweaked.  That's really about /home and /var and some other LVs that aren't listed.

You can do A and B.

You are lucky.  LVM will make this relatively painless.

In the meantime, ensure your backups are in good shape.

What is the choice?

---

