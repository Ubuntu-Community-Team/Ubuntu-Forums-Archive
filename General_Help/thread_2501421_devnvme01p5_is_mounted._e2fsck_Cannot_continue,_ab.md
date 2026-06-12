---
title: "/devnvme01p5 is mounted. e2fsck: Cannot continue, aborting."
date: 2024-10-06
forum: General Help
---

### Post by makem2 on 2024-10-06
I used advanced recovery mode to fsck my Ubuntu 24.04 instance due to filesystem checks on every boot.

I used the 'fsck' option from the menu and received the error:

/lib/recovery-mode/recovery-menu: line 80: /etc/default/rcs: No such file or directory.
fsck from util-linux 2.39.3
/dev/nvme0n1p5 is mounted
e2fsck: Cannot continue, aborting.

/dev/nvme0n1p5 is the mount point for /, /var/snap/...
/dev/nvme0n1p6 is the mount point for /home

I re-tried the same method this time using 'root access', separately, on each of the nvme's but received the same message each time.

Help?

---

### Post by tea for one on 2024-10-06
> **makem2 said:**
> /dev/nvme0n1p5 is mounted
e2fsck: Cannot continue, aborting
Boot into a "Try Ubuntu" live session
If (unusually) your partitions are mounted:-
```
sudo umount -a
```
```
sudo fsck /dev/nvme0n1p5
```

---

### Post by 1fallen on 2024-10-06
+1 for tea for one ^^^^
Also in Advanced mode "fsck" should be ran as:
```
sudo fsck -f /
```
I pointed that out in your last thread as well.

AND seeing how I see many fsck running at boot, I feel there is a bug in the soup.

On Mine and NOT MOUNTED:
```
[FONT=monospace][COLOR=#000000]sudo fsck -f /dev/nvme0n1p2 [/COLOR]
[sudo] password for me:  
fsck from util-linux 2.40.2 
e2fsck 1.47.1 (20-May-2024) 
Pass 1: Checking inodes, blocks, and sizes 
Inode 23863922 extent tree (at level 1) could be shorter.  Optimize<y>? yes 
Pass 1E: Optimizing extent trees 
Pass 2: Checking directory structure 
Pass 3: Checking directory connectivity 
Pass 4: Checking reference counts 
Pass 5: Checking group summary information 

/dev/nvme0n1p2: ***** FILE SYSTEM WAS MODIFIED ***** 
/dev/nvme0n1p2: 2612399/30507008 files (0.3% non-contiguous), 45034541/122018696 blocks



```
[/FONT]

---

### Post by makem2 on 2024-10-06
> **tea for one said:**
> Boot into a "Try Ubuntu" live session
If (unusually) your partitions are mounted:-
```
sudo umount -a
```
```
sudo fsck /dev/nvme0n1p5
```

I did try that but the live session was 20.04 not 24.04 which I still have to do but rl intervenes as usual

---

### Post by makem2 on 2024-10-06
> **1fallen2 said:**
> +1 for tea for one ^^^^
Also in Advanced mode "fsck" should be ran as:
```
sudo fsck -f /
```
I pointed that out in your last thread as well.

AND seeing how I see many fsck running at boot, I feel there is a bug in the soup.

On Mine and NOT MOUNTED:
```
[FONT=monospace][COLOR=#000000]sudo fsck -f /dev/nvme0n1p2 [/COLOR]
[sudo] password for me:  
fsck from util-linux 2.40.2 
e2fsck 1.47.1 (20-May-2024) 
Pass 1: Checking inodes, blocks, and sizes 
Inode 23863922 extent tree (at level 1) could be shorter.  Optimize<y>? yes 
Pass 1E: Optimizing extent trees 
Pass 2: Checking directory structure 
Pass 3: Checking directory connectivity 
Pass 4: Checking reference counts 
Pass 5: Checking group summary information 

/dev/nvme0n1p2: ***** FILE SYSTEM WAS MODIFIED ***** 
/dev/nvme0n1p2: 2612399/30507008 files (0.3% non-contiguous), 45034541/122018696 blocks


[/FONT]
```[FONT=monospace]
[/FONT]

I think its related to the file it complains about. I have a feeling its related to Wayland. Is there a way to check if any Wayland bits and pieces remain which might need it?

Edit: Ah I remember long time ago I had Gnome desktop for some reason and Wayland was involved in the reaso which I forget.

Can I remove the Gnome desktop I ask and maybe, just maybe that will take out the need for rcs file. There are dozens or Wayland bits and piece still installed but no idea which is needed as its tied into many things.

Gnome desktop no longer installed - must have purged it.

Btw I did use sudo fsck -f / in advanced mode, thought I posted the result somewhere there.

---

### Post by 1fallen on 2024-10-06
> **makem2 said:**
>  Is there a way to check if any Wayland bits and pieces remain which might need it?

Dang Wayland is very new to me so give me a beat to think  about that????? I'm a Devout XFCE guy.
But for the past year I've been running a Plasma-6 system with wayland and I'm falling in Like with it. :mrgreen:

If you get a chance when in Advanced Mode >>Root try
```
apt autoremove --purge
```

---

### Post by makem2 on 2024-10-06
> **1fallen2 said:**
> Dang Wayland is very new to me so give me a beat to think  about that????? I'm a Devout XFCE guy.
But for the past year I've been running a Plasma-6 system with wayland and I'm falling in Like with it. :mrgreen:

If you get a chance when in Advanced Mode >>Root try
```
apt autoremove --purge
```

Done - nothing to remove

Edit: I'm a Devout XFCE guy

---

### Post by 1fallen on 2024-10-06
Just a though, and Thanks for replying.
I knew you was XFCEman, but the wayland part threw me.

---

