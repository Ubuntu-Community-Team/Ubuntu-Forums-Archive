---
title: "md2 disappears on reboot"
date: 2014-10-13
forum: General Help
---

### Post by Edwin_Solares on 2014-10-13
I'm having some issues with 14.04 LTS. One my monitor layout configuration never stays. It always resets on reboot.

But I have to say the most annoying thing is having my raid5 array completely disappear on every reboot.  I have updated intramfs I have also, added it to mdadm.conf through an update command. everything looks good but once i reboot. /dev/md2 (which is the device name for my raid5) is completely gone. the /dev/md2 file is gone, and so is the link i created in /dev/md/ is gone as if it never existed. It's the most bizzare thing I have seen in ubuntu yet. 

The only way to get my raid5 to come back is to run
```
mdadm --create /dev/md2 --assume-clean --level=5 --raid-devices=4 /dev/sd[c-f]
```

once done, I am able to mount the raid5 md2 device and everything is peachy. Why is it though that everything seems to reset on reboot and if I never made changes to begin with.

I have two md devices that I created on install that don't change, or disappear. they are md0 and md1

when i run cat /proc/mdstat i get the following (after i recreate my raid5)

```
md2 : active raid5 sdf[3] sde[2] sdd[1] sdc[0]      4395021312 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
md1 : active raid0 sda3[0] sdb3[1]
      404405248 blocks super 1.2 512k chunks
      
md0 : active raid0 sdb2[1] sda2[0]
      62499840 blocks super 1.2 512k chunks
```

also when i do mdadm --examine --scan i get the following:
```
ARRAY /dev/md/0 metadata=1.2 UUID=6814f7a7:704a5bbd:06f894f9:2807b981 name=edwin-ranzlab-ubserver:0ARRAY /dev/md/1 metadata=1.2 UUID=661c06b4:8366df60:83c2ac54:2f411126 name=edwin-ranzlab-ubserver:1
ARRAY /dev/md/2 metadata=1.2 UUID=bf1d436b:b2578874:8a0153b8:2336e015 name=edwin-ranzlab-ubserver:2
```

Which is great, but once i reboot, /dev/md2 and /dev/md/2 completely disappear. what in the world is going on? Please help. the dual monitor arrangement is another problem, I just wanted to mention it as it seems my system "resets" on reboot.

---

