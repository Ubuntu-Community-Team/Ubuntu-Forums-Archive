---
title: "accidentally deleted /home partition"
date: 2007-02-06
forum: General Help
---

### Post by carverj on 2007-02-06
Hi guys,
             Have a dual boot with XP and deleted /home when installing XP so that it would fit (had /home on /hda3 which was ext3 primary).
Now I cannot login to Ubuntu with an error as such:
"
Your home directory is listed as * edit: something or other* but doesn't appear to exist.
User's $HOME/.dmrc file being ignored. $HOME must be owned by user and not writeable by others. $HOME/.dmrc as above but with permissions 644
"
Tried all this and more (such as creating ext3 again with GParted and  testing with Gpart, which doesn't seem to support ext3).
So what could i try next? How about installing fresh Ubuntu over XP in order to create duplicate /home partition with $HOME/.dmrc file
 so that I may attempt to gain login access

Thanks loads for your help!!

---

### Post by kidders on 2007-02-06
Hi there,

> **carverj said:**
> Tried all this and moreAre you sure you did it correctly? All you really need is a home directory you can write to. So,

[LIST]
[*]It must exist.
[*]To prevent permissions warnings, you should own it and chmod 644 it.
[*]If they exist, you should make sure you own & can write to any files in your home that are used during login (most of them start with '.').
[/LIST]

When you deleted your /home partition, and /dev/hda3 failed (obviously) to mount, all you would have been left with is a /home mount point owned by root. Even so, you should still be able to do a terminal login though.

---

### Post by carverj on 2007-02-06
Ok, ta. Half way there mate!!
Managed to enter Ubuntu in recovery mode after changing owner and permissions of home folder. I then found a backup of the original /home contents and added it to /home, the above mentioned folder.Am still getting the problem with logging in. Below is an interesting part of the error/ log:
"
/etc/gdm/Xsession: Beginning session setup 
(gnome-session4499): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory '/home/jeremy/.gnome2/': Perm denied
"
Do I need to change a whole heap of attributes in order to be able to login again?
Thanks

---

### Post by Rui Pais on 2007-02-06
h,
 you to copy from your backup with** cp -a** to preserve permissions and attributes.

---

### Post by carverj on 2007-02-06
Ok, job done.
Now, error remains, so just wondering if I need to change the ownership and attributes of any other folders!?
I noticed the /root (not to be confused with /(root)) folder contains .gnome2 with the owner root for example.
Do I just change the attributes of all the folders in my / directory?
Cheers fella's

---

### Post by Rui Pais on 2007-02-06
if you only deleted /home why should you want to change any other permissions?

/root/.gnome2 it's ownn by root because it's the gnome confs for root. It's in its folder ;) 
(means that you have launched some gui app as root and it had automatically created confs for root)

---

### Post by carverj on 2007-02-06
Yeah cool, makes sense. Just tired after so many hours on one prob.
OK, here is ls -l for /home

```
drw-r--r--   3 jeremy root  4096 Feb  6 20:16 home
```

and inside that folder is:

```
drwxr-xr-x 42 jeremy root 4096 Feb  6 20:16 jeremy

```

and home stuff... do I need to make any more changes here?

```
root@jeremy-desktop:/home/jeremy# ls -ails
total 2204
786540    4 drwxr-xr-x 42 jeremy root      4096 Feb  6 20:16 .
737281    4 drw-r--r--  3 jeremy root      4096 Feb  6 20:16 ..
787589    4 -rw-------  1 jeremy jeremy     350 Feb  6 14:35 .ICEauthority
803648    4 drwx------  2 jeremy jeremy    4096 Feb  5 22:09 .Trash
787208    4 -rw-------  1 jeremy jeremy     125 Feb  6 14:35 .Xauthority
803989    4 drwxr-xr-x  2 jeremy root      4096 Jan 31 22:45 .automatix
787633    8 -rw-------  1 jeremy jeremy    5334 Feb  6 12:45 .bash_history
787205    4 -rw-r--r--  1 jeremy jeremy     220 Feb  1 03:43 .bash_logout
787206    4 -rw-r--r--  1 jeremy jeremy     414 Feb  1 03:43 .bash_profile
787207    4 -rw-r--r--  1 jeremy jeremy    2227 Feb  1 03:43 .bashrc
935999    4 drwxr-xr-x  4 jeremy jeremy    4096 Feb  1 12:42 .bmp
804127    4 drwx------  3 jeremy jeremy    4096 Jan 31 23:31 .config
804229    4 drwxr-xr-x  6 jeremy jeremy    4096 Jan 31 23:43 .democracy
787210    4 -rw-r--r--  1 jeremy jeremy      26 Jan 31 17:51 .dmrc
787588    4 -rw-------  1 jeremy jeremy      16 Jan 31 17:51 .esd_auth
803674    4 drwxr-xr-x  8 jeremy jeremy    4096 Feb  6 12:43 .evolution
787627    0 -rw-r--r--  1 jeremy jeremy       0 Feb  1 09:01 .fonts.cache-1
787211    4 drwx------  4 jeremy jeremy    4096 Feb  6 14:36 .gconf
787558    4 drwx------  2 jeremy jeremy    4096 Feb  6 14:36 .gconfd
787641    0 -rw-r-----  1 jeremy jeremy       0 Feb  6 14:36 .gksu.lock
803650    4 drwxr-xr-x  3 jeremy jeremy    4096 Jan 31 17:51 .gnome
787560    4 drwx------  9 jeremy jeremy    4096 Feb  6 12:45 .gnome2
787585    4 drwx------  2 jeremy jeremy    4096 Jan 31 17:51 .gnome2_private
803983    4 drwx------  2 jeremy jeremy    4096 Jan 31 18:21 .gnupg
787586    4 drwxr-xr-x  2 jeremy jeremy    4096 Jan 31 22:49 .gstreamer-0.10
787618    4 -rw-r--r--  1 jeremy jeremy      88 Jan 31 17:51 .gtkrc-1.2-gnome2
787630    4 -rw-------  1 jeremy jeremy      35 Feb  6 10:54 .lesshst
936058    4 drwxr-xr-x  3 jeremy jeremy    4096 Feb  1 12:51 .listen
804072    4 drwx------  3 jeremy jeremy    4096 Jan 31 23:28 .macromedia
803653    4 drwx------  3 jeremy jeremy    4096 Jan 31 17:51 .metacity
803734    4 drwx------  5 jeremy jeremy    4096 Feb  1 12:19 .mozilla
923111    4 drwxr-xr-x  2 jeremy jeremy    4096 Jan 31 23:46 .mplayer
787590    4 drwxr-xr-x  3 jeremy jeremy    4096 Feb  6 12:45 .nautilus
787634    4 -rw-r--r--  1 jeremy jeremy     988 Jan 31 23:15 .nvidia-settings-rc
803864    4 drwx------  3 jeremy jeremy    4096 Jan 31 17:55 .openoffice.org2
787628    4 -rw-------  1 jeremy jeremy     958 Feb  5 23:38 .recently-used
787632   28 -rw-r--r--  1 jeremy jeremy   25873 Feb  6 10:49 .recently-used.xbel
936006    4 drwxr-xr-x  3 jeremy jeremy    4096 Feb  1 12:47 .streamtuner
787629    0 -rw-r--r--  1 jeremy jeremy       0 Jan 31 17:59 .sudo_as_admin_successful
804130    4 drwx------  4 jeremy jeremy    4096 Jan 31 23:58 .thumbnails
804070    4 drwxr-xr-x  2 jeremy jeremy    4096 Jan 31 22:50 .update-manager
803647    4 drwx------  2 jeremy jeremy    4096 Jan 31 17:51 .update-notifier
787613    4 drwxr-xr-x  3 jeremy jeremy    4096 Jan 31 23:45 .vlc
803995    4 drwxr-xr-x  3 jeremy jeremy    4096 Feb  6 11:46 .xine
935993    4 drwxr-xr-x  4 jeremy jeremy    4096 Feb  1 12:06 .xmms
787209    4 -rw-r--r--  1 jeremy jeremy    1240 Feb  6 14:36 .xsession-errors
787619    4 drwxr-xr-x  3 jeremy jeremy    4096 Feb  6 02:59 Desktop
786585    0 lrwxrwxrwx  1 root   root        26 Feb  6 20:11 Examples -> /usr/share/example-content
804241    4 drwxr-xr-x 46 jeremy jeremy    4096 Feb  6 14:35 jeremy
787631    4 -rw-r--r--  1 jeremy jeremy    1730 Jan 29 13:17 key.gpg.asc
935985    4 drwxr-xr-x  2 jeremy jeremy    4096 Jul 19  2006 lib
935987    4 drwxr-xr-x  2 jeremy jeremy    4096 Jul 19  2006 mozilla
923136    4 drwxr-xr-x  2 jeremy jeremy    4096 Jul 19  2006 plugins
935990    4 drwxr-xr-x  2 jeremy jeremy    4096 Jul 19  2006 postinst
787637    4 -rwxr-xr-x  1 jeremy jeremy    2472 Feb  1 00:00 realplay
787640    4 -rwxr-xr-x  1 jeremy jeremy    2486 Feb  1 00:00 realplay.bak
787636  564 -rwxr-xr-x  1 jeremy jeremy  570344 Jul 19  2006 realplay.bin
923188    4 drwxr-xr-x  7 jeremy jeremy    4096 Jul 19  2006 share


```

---

### Post by Rui Pais on 2007-02-06
> **carverj said:**
> Yeah cool, makes sense. Just tired after so many hours on one prob.
:(

> 
OK, here is ls -l for /home

```
drw-r--r--   3 jeremy root  4096 Feb  6 20:16 home
```

and inside that folder is:

```
drwxr-xr-x 42 jeremy root 4096 Feb  6 20:16 jeremy

```

mine is
```
drwxr-xr-x 57 rui    rui    4096 2007-02-05 22:10 rui
```

that should not be any problem, but if you want to be sure why not make
sudo mv /home/jeremy /home/jeremy_TEMP
and redo the cp -a from backup of all /home/jeremy? 
That would ensure that either jeremy folder as all inside contends would have correct permissions (assuming that your backup is ok, of course)

---

### Post by carverj on 2007-02-06
oh, OK. I'll give it a go!
 and here is fstab. It has been through a few changes:

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
UUID=0ae14e7b-753c-411b-bc66-4060dcb0c415 / ext3 defaults,errors=remount-ro 0 1
UUID=b7632bcb-c426-404c-b28e-53f5d4a440d5  none ext3 defaults 0 0 
UUID=24DCEEA3DCEE6E8C /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
UUID=869153eb-666a-48f4-954e-56e6105436e4 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

Could the problem be read only access here?

---

### Post by Rui Pais on 2007-02-06
the **/ ext3 defaults,errors=remount-ro** is for the case of you got errors on filesystem when you boot, and it's ok
> **carverj said:**
> 
UUID=b7632bcb-c426-404c-b28e-53f5d4a440d5  **none** ext3 defaults 0 0 

this is not correct.

should be **/home** intead of **none**. 
And if you remade/format the partition you should ensure that the UUID is correct (you mention on your first post that is hda3) check with:
```
sudo vol_id /dev/hda3 |grep UUID
```

---

### Post by carverj on 2007-02-06
output of that command is:

```
root@jeremy-desktop:~# sudo vol_id /dev/hda3 | grep UUID
ID_FS_UUID=869153eb-666a-48f4-954e-56e6105436e4

```

So, would you score it out completely from fstab?
I was trying to leave the entry in, but wasn't sure about which mount point entry to write so I used none!

Also, is it possible that it is still looking at my old /home partition (/dev/hda3) for login conf. files?
May I need to reformat this partition?

---

### Post by Rui Pais on 2007-02-06
> **carverj said:**
> output of that command is:

```
root@jeremy-desktop:~# sudo vol_id /dev/hda3 | grep UUID
ID_FS_UUID=869153eb-666a-48f4-954e-56e6105436e4

```

So, would you score it out completely from fstab?
I was trying to leave the entry in, but wasn't sure about which mount point entry to write so I used none!

Yes, you should put then:
```
UUID=869153eb-666a-48f4-954e-56e6105436e4  /home  ext3 defaults  0  0 
```
or even better:
```
UUID=869153eb-666a-48f4-954e-56e6105436e4  /home  ext3 defaults,noatime  0  2 
```

removing that old reference to a gone partition.
The UUID change everytime you format the partition.

---

### Post by carverj on 2007-02-06
Ok, changed fstab. Following error from fsck:

```
Log of fsck -C -R -A -a 
Tue Feb  6 22:36:26 2007

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=b7632bcb-c426-404c-b28e-53f5d4a440d5'

fsck died with exit status 8

Tue Feb  6 22:36:26 2007
----------------
```

Do I need to make /dev/hda3 a /home partition again somehow?
Also, I noticed that there is no synaptic in recovery mode, So I am having trouble installing GParted, etc.

---

### Post by Rui Pais on 2007-02-06
> **carverj said:**
> Ok, changed fstab. Following error from fsck:

```
Log of fsck -C -R -A -a 
Tue Feb  6 22:36:26 2007

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=b7632bcb-c426-404c-b28e-53f5d4a440d5'

fsck died with exit status 8

Tue Feb  6 22:36:26 2007
----------------
```

Do I need to make /dev/hda3 a /home partition again somehow?
Also, I noticed that there is no synaptic in recovery mode, So I am having trouble installing GParted, etc.

no prob. you just forget to remove the old line thats all. (you need to rest)

in recovery mode you don't have X server, so no synaptic and gparted will not start too.
You can use apt-get or aptitude to install stuff. 
 
double check fstab and try to reboot again. It should work normally with correct UUID of all partitions.

Good luck.

---

### Post by carverj on 2007-02-06
In,
     yup, scored out that line, cleaned up the other UUID's in fstab, and finally found a missing x permission for the /home folder and that's it.
Thanks so much for all your help!!
Definitely would have given up if it weren't for all that help.

---

### Post by Rui Pais on 2007-02-06
> **carverj said:**
> In,
     yup, scored out that line, cleaned up the other UUID's in fstab, and finally found a missing x permission for the /home folder and that's it.
Thanks so much for all your help!!
Definitely would have given up if it weren't for all that help.

he he, glad you make it, carverj :)

have fun.

---

