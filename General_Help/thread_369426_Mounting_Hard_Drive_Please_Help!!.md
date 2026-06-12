---
title: "Mounting Hard Drive Please Help!!"
date: 2007-02-24
forum: General Help
---

### Post by amdalex on 2007-02-24
Right now on my computer I have a 10gb hard drive with windows 98 and a 25gb hard drive with ubuntu on it. The 10gb hard drive is FAT32 and the ubuntu drive is ext3. Also the ubuntu drive is the master and windows drive is a slave. They both use the primary IDE port. I went on to ubuntuguide.org and found the command to mount the windows drive and typed it into the terminal but it came up with an error. Do you guys think you could give me the command to mount me windows drive so I can use it? Sorry for the long post, I just wanted to make sure that you guys knew everything about my computer.:confused:

---

### Post by nereid on 2007-02-24
Which was the command you entered from the ubuntuguide site (please don't forget the parameters)?

---

### Post by altaaa on 2007-02-24
First, create the directory /media/windows:
[FONT="Courier New"]sudo mkdir /media/windows[/FONT]

Then, mount the harddrive:
[FONT="Courier New"]sudo mount /dev/hdb1 /media/windows/ -t vfat -o iocharset=utf8,umask=000[/FONT]

If you want ubuntu to do this on startup, add the following line to /etc/fstab (make a backup first!):
[FONT="Courier New"]/dev/hdb1    /media/windows vfat  iocharset=utf8,umask=000  0    0[/FONT]

For reference:
/dev/hda -> Primary IDE Master
/dev/hdb -> Primary IDE Slave
/dev/hdc -> Secondary IDE master
/dev/hdd -> Secondary IDE slave

If you get errors, post them here.

---

### Post by RedSquirrel on 2007-02-24
> **amdalex said:**
> Right now on my computer I have a 10gb hard drive with windows 98 and a 25gb hard drive with ubuntu on it. The 10gb hard drive is FAT32 and the ubuntu drive is ext3. Also the ubuntu drive is the master and windows drive is a slave. They both use the primary IDE port. I went on to ubuntuguide.org and found the command to mount the windows drive and typed it into the terminal but it came up with an error. Do you guys think you could give me the command to mount me windows drive so I can use it? Sorry for the long post, I just wanted to make sure that you guys knew everything about my computer.:confused:

I don't think we know enough yet. :)

Can you post the output of the following commands (run them in a terminal):

```
 sudo fdisk -l
```

(that's an l, as in larry) and

```
 more /etc/fstab
```

Thanks.

---

### Post by RedSquirrel on 2007-02-24
> **altaaa said:**
> First, create the directory /media/windows:
[FONT=Courier New]sudo mkdir /media/windows[/FONT]

Then, mount the harddrive:
[FONT=Courier New]sudo mount /dev/hdb1 /media/windows/ -t vfat -o iocharset=utf8,umask=000[/FONT]

If you want ubuntu to do this on startup, add the following line to /etc/fstab (make a backup first!):
[FONT=Courier New]/dev/hdb1    /media/windows vfat  iocharset=utf8,umask=000  0    0[/FONT]


This might not be necessary. It's possible that the line is already in /etc/fstab.


> 
For reference:
/dev/hda -> Primary IDE Master
/dev/hdb -> Primary IDE Slave
/dev/hdc -> Secundary IDE master
/dev/hdd -> Secundary IDE slave


It *should* work that way, but sometimes it doesn't. I think looking at the output of 'fdisk -l' and the contents of /etc/fstab would be a wise precaution.

---

### Post by altaaa on 2007-02-24
> **RedSquirrel said:**
> It *should* work that way, but sometimes it doesn't. I think looking at the output of 'fdisk -l' and the contents of /etc/fstab would be a wise precaution.

Amdalex states he used the command from ubuntuguide.org, he didn't say he changed it to make it look for the pri slave drive. If the manual mount works, there shouldn't be a problem with adding it to /etc/fstab. However, taking precautions never hurt anybody :)

---

