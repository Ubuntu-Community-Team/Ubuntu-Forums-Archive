---
title: "Removable media sometimes mounts at /media/xx, sometimes at /media/user/xx"
date: 2014-06-01
forum: General Help
---

### Post by morganpatrick on 2014-06-01
Hello,

I have had this issue for a while, first with Ubunutu 12.04, and now with Ubuntu 14.04. An external hard drive named 'xthd', for example, would mount at /media/xthd. Then, one day, I would either remove and re-insert the media, or remove it and then reboot --- I'm not sure what combination triggers this --- and suddenly, I'm now mounted at /media/myusername/xthd.

I've had this happen, had to reset a lot of paths to photos, and movies in programs like Shotwell or XBMC... only to have it switch back and have to do it all over. I would like my removable media to pick one and stick with it, preferably /media/xthd.

I have used fstab in the past to force something to mount a certain way, but my understanding is that this only matters at boot, and is therefore not helpful for removable media. Could someone explain to me what is going on, and how to remedy it?

Thanks so much.

---

### Post by morganpatrick on 2014-06-18
It looks like I could maybe use udev rules to fix this problem, but I don't know enough about udev rules to make this work. Could someone help me out?

---

### Post by Bucky Ball on 2014-06-19
This is old, but could get you started. See post #3 and continue.

[https://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/](https://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/)

As suggested a bit further down, in the example given in post #3:

```
/dev/usbhdd1 /media/usbhdd ext3 rw,user,noauto 0 0
```

... I would replace '/dev/usbhdd1' with the UUID of the partition. That is convention now. To find the UUIDs, with the drive plugged in, run:

```

sudo blkid
```

That will show the UUIDs, and thus, your udev line would be something like:

```
UUID=insert-correct-partition-UUID-here /media/xthd ext4 rw,user,noauto 0 0
```

You will need to create that mount point first, though, by running this command:

```

sudo mkdir /media/xthd
```

Hope that helps. I had a vaguely similar issue with an external eSATA drive not giving me permissions to do anything and I fixed with a custom udev rule. Hope this works for you, too. Good luck. ;)

---

