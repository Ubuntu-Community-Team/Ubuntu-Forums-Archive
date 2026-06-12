---
title: "fsck fails on startup"
date: 2007-02-13
forum: General Help
---

### Post by ingo on 2007-02-13
SOLVED

Hi,

feeling a little dumb, but here goes:

I rearranged one of my hard disks - deleted the old hda7, increased hda6 in size and created a new smaller hda7. On booting the box would stop and tell me that fsck died with exit status 8 (operational error!) - very helpful  [-X

I created the proper mount point and arranged the fstab accordingly (word of warning, I'm behind the times with these new fancy fstab arrangements, so this may well be the cause of the error).

Below is a copy of /var/log/fsck/checkfs
> ingo@dicker:~$ cat /var/log/fsck/checkfs
Log of fsck -C -R -A -a
Tue Feb 13 15:12:26 2007

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda5: 0 files, 1/1316038 clusters
downloads: clean, 61492/1311552 files, 1570739/2622603 blocks
games: clean, 2984/1311552 files, 1454737/2622603 blocks
multimedia: clean, 9443/8372224 files, 13328948/16723657 blocks
maintenance: clean, 13536/6029312 files, 10362138/12056774 blocks
fsck.ext3: Unable to resolve 'UUID=e4f9cb52-fd67-4acc-a274-3106b76f7be2'
Gentoo: clean, 224939/1311552 files, 449175/2622603 blocks (check in 2 mounts)
/: clean, 126466/1311552 files, 583468/2622603 blocks
Suse10.0: clean, 362236/1314144 files, 2420176/2624200 blocks
SUSE9.3: clean, 258990/1310720 files, 1997879/2620595 blocks
usr: clean, 270504/1310720 files, 1625564/2620595 blocks
/dev/sda8: clean, 127492/1311552 files, 911395/2622603 blocks
/dev/sda9: clean, 12/1311552 files, 49374/2622603 blocks
personal: clean, 6141/263296 files, 258126/526128 blocks
fsck died with exit status 8

Tue Feb 13 15:12:28 2007
----------------
ingo@dicker:~$And here is the relevant fstab entry:
> # /dev/hda7
UUID=e4f9cb52-fd67-4acc-a274-3106b76f7be2 /.personalhda ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2Can anybody make any sense of that? I've tried rebooting, but the error continues...

Much obliged :)

SOLVED - all I had to do was 
> sudo vol_id -u /dev/hda7
And I got the proper code.

---

### Post by pollinn on 2007-04-19
Hi, 

I understand nothing of the above.. but
I am getting the same error, here is my log file 

Log of fsck -C -R -A -a 
Fri Apr 20 07:05:00 2007

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 52952 files, 2260090/2718346 clusters
/dev/sda5: Superblock last write time is in the future.  FIXED.
/dev/sda5: clean, 2810/3655680 files, 1997498/7311575 blocks
fsck.ext3: Unable to resolve 'UUID=3506b9bc-6202-4d56-87f5-0f1f08173c4e'

fsck died with exit status 8

Fri Apr 20 05:05:13 2007
----------------

/Sda 5 is my home directory, if i just start gdm i get a login screen but after login i get an error message telling me that my home dir doesn't exist and it results in another login screen.
Pressing Enter and then CONTROL-D starts up Ubuntu with no problems.. but without a login screen.. i think :s 

Would vol_id -u /dev/sda5 solve my problem ??

---

### Post by pollinn on 2007-04-19
Ohh, the only dumb thing i did before this happened was to change the permissions of a partition from root to my user. It was an ext3 partition with nothing on it, the path was /media/Documents.
And it was involved in the error at first.. then i did some more dumb **** that has nothing to do with this.

---

### Post by pollinn on 2007-04-19
Some Monologue i' m doing. 

Anyway. That other dumb sh_t was to repartition my then ext32 /media/Documents to a fat32 /media/Documents.. 

Once i changed the fstab file to fat32, it boots fine.  The permissions are back to root so i guess that was the problem. 

BUT my troubles aren't over. The partition does not show up on the desktop like it should.. and i get a Gnome-panel that is empty and will not close. 

Should i just start over and reinstall??? 
Cause if it's bugging like that i will not be happy with it.

---

### Post by ingo on 2007-04-20
What you need is the relevant and correct UUID entry in your fstab file. For the former open a bash and enter > sudo vol_id -u /dev/sda5Now highlight the output to copy it onto your clipboard, open your fstab with > sudo gedit /etc/fstaband replace the old UUID for your sda5 entry with the new one in your clipboard and Bob's your uncle. Reboot to check.

If I were you I'd get rid of that fat32 partition, change it back to ext3 unless you are a devote fan of defragmentation and lost clusters...

HTH

---

### Post by pollinn on 2007-04-20
Thanks, 

I am actually beginning to understand :D And this got rid of my gnome panel problem.
But the partition still isn't visible on the desktop all though it mounts alright. 
In the fstab file it is set to /media/Documents as mount point. But in gparted it has a blank mount point. Can u make any sence of that ???

---

### Post by ingo on 2007-04-20
Sorry mate, cannot help you with gnome as I'm on kde...

---

