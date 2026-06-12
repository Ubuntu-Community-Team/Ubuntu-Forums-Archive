---
title: "NFS share not accessible if directory to large"
date: 2013-06-03
forum: General Help
---

### Post by iitywygms on 2013-06-03
Hello All:

I am running 12.04.  I have nfs setup on my server with a video directory accessible from all the computers in my home.
Yesterday, after adding another video to the nfs shared directory, it became inaccessible from other computers.  As soon as I removed the video, that directory was accesible again.  
So after playing around a bit, it seems like the directory is "full"  Once a certain size is reached, I cant get to it from other computers.  It did not matter what I added to the video directory.  
I honestly do not know what is going on or how I should go about troubleshooting.  Any suggestions?
Thanks.

---

### Post by LewisTM on 2013-06-03
First thing would be to tell us what's in your /etc/exports file and the corresponding fstab entries in your clients.

---

### Post by iitywygms on 2013-06-03
Server etc/exports

# /var/lib/mythtv/recordings    *(ro,async,no_root_squash,no_subtree_check)
# /var/lib/mythtv/videos    *(ro,async,no_root_squash,no_subtree_check)
# /var/lib/mythtv/music    *(ro,async,no_root_squash,no_subtree_check)
# /var/lib/mythtv/pictures    *(ro,async,no_root_squash,no_subtree_check)
/D2/share *(rw,async,no_root_squash,no_subtree_check)

Client fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ceaae3d8-c02c-4cf2-a071-4e0e2ef050f2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=db281925-14ec-4128-b19e-f9b8ef747ff0 none            swap    sw              0       0
192.168.2.4:/D2/share /mythbackend nfs rsize=8192,wsize=8192,timeo=14,intr


In the share directory on my server i have sub directories.
videos, music, common.

---

### Post by iitywygms on 2013-06-03
I fired up my old computer that is running 10.04.  It can access the videos directory on my server no problem.  The fstab is the same on that computer.
So this may be a bug?  Not sure.
I am not sure how I should be troubleshooting this.  I do not see any errors in dmesg or syslog.  Anywhere else I should be looking?

---

### Post by LewisTM on 2013-06-04
If I remember correctly, the 10.04 client defaulted to NFSv3 while 12.04 defaults to v4. It might be a good idea to force your server to use version 3 with the export parameter **vers=3**. Could be a bug with 12.04's client in v4 mode. Just a hunch.
Run [FONT=Courier New]sudo exportfs -ra [/FONT] on the server once the changes to /etc/exports have been made. 
You also need to reboot the clients, or at least remount the shares.

---

### Post by iitywygms on 2013-06-04
I will give the above a shot when I get home today.  
Of note.  I can access the videos directory just fine from a 10.04 client.
So.
I updated my laptop to 12.10 and it can now access the video files just fine from that laptop.  So something happened during the upgrade that solved the issue.
If I could figure out what was upgraded that fixed it, that would be great.  I would rather not upgrade all my clients to 12.10 at this time.  (All but one of my clients is at 12.04)
Just a fyi.  This is not an access issue.  I can access ALL the files just fine, IF I DO NOT make the video directory any larger.  Adding another video (or any file type for that matter) to the video directory makes it not accessible.  All other directories work just fine.
Does anyone know what changed from 12.04 to 12.10 that would affect nfs?

---

### Post by iitywygms on 2013-06-04
Okay, adding nfsvers=3 to the fstab of my clients fixes the issue.

Questions.
Is my server using ver 3 or 4?  (12.04)
If it is using 3, should it not be using 4?  
How do I make it use 4? Or do I need to?
Or is this just a bug?

---

### Post by LewisTM on 2013-06-05
> **iitywygms said:**
> Okay, adding nfsvers=3 to the fstab of my clients fixes the issue.

Questions.
Is my server using ver 3 or 4?  (12.04)
If it is using 3, should it not be using 4?  
How do I make it use 4? Or do I need to?
Or is this just a bug?
Good to know it worked!
The 12.04 server runs both modes simultaneously; v4 handles things quite differently under the hood. Old clients would query servers and connect via NFSv3 unless you specified v4 in fstab (fstype nfs4). For more recent clients, it's the opposite, to the point where a NFSv3-only server (non Ubuntu or very old) won't be recognized unless you set vers=3 in the client mount options.
So yes, I'd say this is a 12.04 NFSv4 bug. 
Never liked v4 myself, its improvements are aimed at very complex server setups, otherwise it's of little use and introduces some restrictions.

Cheers!

---

### Post by iitywygms on 2013-06-05
Thank you.  Always good to mark a problem solved.
In my haste to find a fix I updated one of my clients to 13.04.  Nfs works on it but now it has other/worse bugs.  But that is a different issue.

Edit.  Guess it's not possible to mark as solved now.  Oh well.

---

