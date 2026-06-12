---
title: "How do I remount my partitions?"
date: 2007-01-02
forum: General Help
---

### Post by jincast90 on 2007-01-02
Hello. I have just formated two of my partitions. I was wondering how do I mount these again? They are called hda1 and hda2. I was also wondering if it is possible to change the mount point to some other folder then /media so my mounts don't show up on the Desktop.

---

### Post by pseudonym on 2007-01-02
Hi, for the first part of your question, please post the contents of your /etc/fstab file.

For the second part, there should be a something in your desktop settings to handle the automounting of media on the desktop. I can't remember exactly which (I don't use Gnome or KDE anymore, and in Xfce we don't have this yet), but it should be in the 'System' menu. something which allows you to turn the drive icons off on your desktop.

---

### Post by Malta paul on 2007-01-02
Hi
It may help you to check these sights:
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)

Hope this may help :)

---

### Post by mxrten on 2007-01-02
You can either use a GUI, or as i prefer, the terminal:

Make a directory to be the mount point:
```
sudo mkdir */my/mount/point*
```
This command mounts the partition:
```
sudo mount /dev/hda1 -t *type* */my/mount/point*
```
Where *type* is ext3, vfat or whatever you chose when you formatted the partition.

If there were no errors and you can browse */my/mount/point* you can add the following line to /etc/fstab (sudo gedit /etc/fstab):
```
/dev/hda1   */my/mount/point*   *type*   defaults
```
and the partition will be automounted at boot

---

### Post by jincast90 on 2007-01-04
Ok.. This is what I did.

1. I made a directory named /mnt/Windows using the command: sudo mkdir /mnt/Windows

2. I did the following command: sudo mount /dev/hda1 -t ntfs /mnt/Windows

3. I added this line:

/dev/hda1 /mnt/Windows ntfs defaults

to the end of my /etc/fstab

I did the above commands, and I still can't use my partition. All I get is this little red icon with a white cross named Windows in my /mnt directory. So what am I doing wrong?

---

### Post by quartzy on 2007-01-04
> **jincast90 said:**
> Ok.. This is what I did.
2. I did the following command: sudo mount /dev/hda1 -t ntfs /mnt/Windows

At this point it should be mounted (adding it to fstab is so it will mount on boot).

You did format it to be a NTFS filesystem?

---

### Post by jincast90 on 2007-01-04
> **quartzy said:**
> At this point it should be mounted (adding it to fstab is so it will mount on boot).

You did format it to be a NTFS filesystem?

yes I did.

---

### Post by jincast90 on 2007-01-05
bump. No one knows what I am doing wrong? It is quite annoying.

---

### Post by mxrten on 2007-01-05
If you received no errors or complaints when executing those commands the partition should be mounted. df will list all mounted partitions:
```
df
```

If /dev/hda1 doesn't show up, post the relevant lines of dmesg here.

E.g. ```
dmesg|grep hda1    or    dmesg|tail -n 20
```

---

### Post by jincast90 on 2007-01-06
One of the lines I get when using the df command is this:

/dev/hda1             22820296   5758476  17061820  26% /mnt/Windows

Should my partition work? Because it still doesn't.

I have attached an image of how the partition looks from nautilus.

---

### Post by quartzy on 2007-01-06
What happens if you do (in a console)

```
cd /mnt/Windows
```

```
ls -l
```

You may need to sudo it.

---

### Post by mxrten on 2007-01-06
I think it's a permission issue... Open nautilus as root user:
```
gksudo nautilus
```
and see if /mnt/Windows is more co-operative.

If it works we'll just have to figure out how to change permission for the partition.

---

### Post by jincast90 on 2007-01-06
> **mxrten said:**
> I think it's a permission issue... Open nautilus as root user:
```
gksudo nautilus
```
and see if /mnt/Windows is more co-operative.

If it works we'll just have to figure out how to change permission for the partition.

When typing gksudo nautilus in the terminal nautilus comes up, but I can only access my home and media folder. The root is supposed to only contain the media and home folder? So I tried looking in my media folder, because maybe I could find my Ubuntu partition but it's not there. Only mu cdrom0, floppy, floppy0, hda1 (ntfs) and hda2 (fat32). 

Oh and by the way, I tried to change the chmod, but when doing this it gives me an error saying it is read only. I have tried chmod 777, chmod 555 and chmod 111 and they all give me the same error.

This is just way to complicated ](*,) 

So anyone have any ideas of what to do now?

---

### Post by jincast90 on 2007-01-06
> **quartzy said:**
> What happens if you do (in a console)

```
cd /mnt/Windows
```

```
ls -l
```

You may need to sudo it.

I tried typing cd /mnt/Windows, but I got told I did not have permission to do so. So I tried to type sudo cd /mnt/Windows, but it did not even recognize this as a valid command.

---

### Post by mxrten on 2007-01-06
> **jincast90 said:**
> When typing gksudo nautilus in the terminal nautilus comes up, but I can only access my home and media folder. 

Surely you must be able to navigate to /mnt/Windows... File System -> mnt -> Windows... or?

---

### Post by quartzy on 2007-01-06
> **jincast90 said:**
> When typing gksudo nautilus in the terminal nautilus comes up, but I can only access my home and media folder. The root is supposed to only contain the media and home folder? So I tried looking in my media folder, because maybe I could find my Ubuntu partition but it's not there. Only mu cdrom0, floppy, floppy0, hda1 (ntfs) and hda2 (fat32). 

Oh and by the way, I tried to change the chmod, but when doing this it gives me an error saying it is read only. I have tried chmod 777, chmod 555 and chmod 111 and they all give me the same error.

This is just way to complicated ](*,) 

So anyone have any ideas of what to do now?

This is due to it 'hiding' files (kinda like windows does the first time you want to look at C: ), in KDE you can view them by going View -> Show Hidden Files I would assume it's similar in gnome.  Or you could just type /mnt in the address bar.

Also for my suggestion, this might work:

```
sudo ls -l /mnt/Windows
```

---

### Post by jincast90 on 2007-01-07
> **quartzy said:**
> 
```
sudo ls -l /mnt/Windows
```

Hey this worked! Now does anyone know how I can view whats in my folder with a file manager like nautilus or gnome commander? In nautilus I simply just get a red icon, and in gnome commander I get this error: List Failed: Access Denied. I still can't cd to the folder from my cli, I get an error saying access denied when trying to do so. But I can view what is in it, using sudo ls -l /mnt/Windows

---

### Post by jincast90 on 2007-01-07
Bump.. This really should not be this difficult.

---

### Post by quartzy on 2007-01-07
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

:)

---

### Post by jincast90 on 2007-01-08
Ok. Im suppose to add this line: /dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
to my /etc/fstab 
If I want to mount the drive in /mnt/Windows instead of /media/windows 
Should I just type:
 /mnt/Windows ntfs  nls=utf8,umask=0222 0    0

instead of:
 /media/windows ntfs  nls=utf8,umask=0222 0    0

---

### Post by quartzy on 2007-01-08
Yes

---

### Post by xShrimp on 2007-01-08
I'm also having this same problem, I had got it to mount before, but one day it just disappeared and I haven't been able to mount it since. I've tried using NTFS-3G with Fuse, but haven't been able to get the fuseblk to be located, and the help guide on the NTFS-3G site doesn't help one bit, because I followed the instructions and I still can't get it to locate fuseblk kernel, I don't even think it exists on my filesystem. But I think I'm just gonna give up on NTFS-3G and just use the fstab  and sudo mount method.

---

### Post by tcrroadie on 2007-01-08
> **jincast90 said:**
> Ok. Im suppose to add this line: /dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
to my /etc/fstab 
If I want to mount the drive in /mnt/Windows instead of /media/windows 
Should I just type:
 /mnt/Windows ntfs  nls=utf8,umask=0222 0    0

instead of:
 /media/windows ntfs  nls=utf8,umask=0222 0    0

I was reading through this entire post and had a good feeling you were just having a problem with permissions for your NTFS partition, and then you posted the answer right here.  What you wrote is correct and should work.  When I was playing around with Slackware 2 years ago I ran into the same issue you where having.  Really all that should be needed is adding the umask=0222 option to your fstab. What this does is adds read and execute permissions to normal users and groups.

Sorry to hear that your issue persisted for 2 days.  I know some things on Linux can get frustrating, but hang in their.  It's worth it.  You will learn so much and in the future fixing problems under Linux will be a breeze.

---

