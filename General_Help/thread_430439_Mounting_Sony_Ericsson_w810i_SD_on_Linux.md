---
title: "Mounting Sony Ericsson w810i SD on Linux"
date: 2007-05-02
forum: General Help
---

### Post by Koobi on 2007-05-02
Hi,
I have a Sony Ericsson w810i.

Whenever I want to transfer music to it, I connect it to the PC via my data cable and copy the music, but when I eject it, Ubuntu tells me it cannot eject the device. I think, maybe, my mounting options aren't right:

```

# cat /etc/mtab
.
.
.
.
/dev/sdc1 /media/PHONE\040CARD vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sdb1 /media/PHONE vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

```


any tips on how i can sort this out?

---

### Post by fanatik on 2007-05-02
It works ok for me, it takes a while to eject, however, depending on the volume of data I have copied to it. Somewhere around 10-20 mins is usual.

I am uising Edgy, your profile says you are using Dapper... there are also some newer posts in this forum stating similar unable to unmount USB disks in Feisty.

Your /etc/fstab looks ok. Mine does not have entries for my W810i and it is automatically recognized and mounted when it is plugged in.

Regards,
James.

---

### Post by tcdrewiv on 2007-05-02
With dapper and edgy I always had the eject option to unmount my w810i .  With fiesty there is no eject option, only unmount. The unmount option will remove the usb icons from the desktop but the phone will not acknowledge the disconnect and the files will not transfer.  

Any help?

---

### Post by tcdrewiv on 2007-05-02
Found answer to problem here.
[http://ubuntuforums.org/showthread.php?t=418688&highlight=USB+HDD]("http://ubuntuforums.org/showthread.php?t=418688&highlight=USB+HDD")

---

### Post by SuperAndy on 2007-08-31
where exactly is the answer?

trying what they have suggested does not help me. i have the same problem

---

