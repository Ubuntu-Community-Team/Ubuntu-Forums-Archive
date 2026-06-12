---
title: "Help mounting a drive from the command line"
date: 2008-03-25
forum: General Help
---

### Post by jhorto1 on 2008-03-25
Guys,
Hopefully this is a simple one. I just need to mount a windows ntfs drive from the command line.

The drive is called /dev/sdb1 and the mount point is /media/data

Could someone tell me how to do this in ubuntu? I've tried

sudo mount -t /dev/sdb1 /media/data 

and it didn't work saying something like it /media/data didn't exist.

As you can see, I'm a total n00b and would really appreciate some help.
I've been working on this on and off for two days now and have it so messed up that I can't just mount it from the file manager anymore.

Thank you very much for your time.

Jim

---

### Post by MPH on 2008-03-25
Try using the "make directory" command before the "mount" command to make the "data" directory...

sudo mkdir /media/data

---

### Post by jhorto1 on 2008-03-25
Forgot to tell you that I did check the man page but couldn't decipher it. I also googled this and found several examples, but couldn't get any of them to work.

This whole thing started when I wanted to access my windows drive without being prompted for my ubuntu password every time.
 I right clicked on DATA drive from the file manager and typed in a mount point with slashes in it. I'm pretty sure that's where my trouble started. Afterwards I could never mount the drive using the file manager. I heard in a google search result that  the options would show up again if I was able to mount the drive using the command line. 
I also tried mounting it with the fstab file and only managed to somehow make my other windows partition completely disappear. This is extremely frustrating at times, but I like learning new things.

That's where I stand.


Thanks again for your help.

---

### Post by jhorto1 on 2008-03-26
Thanks MPH!!!

That got me going. I did the mkdir command and followed it with:

sudo mount -t ntfs /dev/sdb1 /media/data

I'd forgotten to specify ntfs. I wonder if this will get it to mount every time now or do I have to try and edit that fstab file again. The last time I did, I made my other windows drive disappear too.

I really don't want to supply my password every time to access that drive.

---

### Post by vanadium on 2008-03-26
You do not really need to add the "-t ntfs": Ubuntu is smart enough to recognize the partition type.

Anyway, if indeed you want the partition to be mounted automatically during startup, you will need to add an entry to fstab. This is only needed for permanent disks. Removable drives such as USB drives are mounted automatically when plugged in through another mechanism.

---

### Post by jhorto1 on 2008-04-03
Thanks guys. I've edited the fstab file and now everything is auto mounting.

I really appreciate all of the help.

---

### Post by #Reistlehr- on 2008-04-03
if you just use -t ntfs then you might have problems reading and writing to the parition. you should install the ntfs-3g package, and mount with that. Just as a note, you should always apply the partition type, if you dont, you can have problems writing, and reading stuff. 

```

sudo apt-get install ntfs-3g

```

then mount with this

sudo mount -t ntfs-3g /dev/sdb1 /media/foldername

this will give you better use of the NTFS filesystem.

---

### Post by jhorto1 on 2008-04-09
I think I'll give it a try, although so far I've had no problems reading / writing to the ntfs.

---

