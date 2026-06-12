---
title: "How to stop Ubuntu mounting one particular drive automatically"
date: 2008-02-11
forum: General Help
---

### Post by lotus49 on 2008-02-11
I have a Huawei E220 modem which includes a CD lookalike containing the Windows drivers which Ubuntu mounts automatically but which is clearly no use in Linux (and not much use in Windows after the first time either).

How do I stop Ubuntu automatically mounting this drive (but still automount everything else)?

---

### Post by ferdostar on 2008-02-11
```
sudo gedit /etc/fstab
```

---

### Post by bernied on 2008-02-11
In case that response was not quite enough information, you would need to do something like:
- identify the name of the device that is being mounted. The 'mount' command in a terminal will do this for you.
- once you know the device's name, create an entry (or edit the existing entry if there is one) for it in /etc/fstab, using the command given by ferdostar above. In the area for options, have the word 'noauto' to prevent automounting.

See 'man mount' and 'man fstab' (in a terminal) for more detail.

---

### Post by lotus49 on 2008-02-12
> **bernied said:**
> In case that response was not quite enough information, you would need to do something like:
- identify the name of the device that is being mounted. The 'mount' command in a terminal will do this for you.
- once you know the device's name, create an entry (or edit the existing entry if there is one) for it in /etc/fstab, using the command given by ferdostar above. In the area for options, have the word 'noauto' to prevent automounting.

See 'man mount' and 'man fstab' (in a terminal) for more detail.

Indeed.  There is no entry for the device in fstab but I know how to identify the device so I can add one.  The noauto option is what I needed to know.

Thanks.

EDIT

Having looked into this further it appears that ISO9660 filesystems do not have a UUID.  Identifying the filesystem by device name won't work as the next physical device I plug in is likely to be called /dev/sdc1 (regardless of whether it's my E220 or another flash disk or HDD) so how do I uniquely identify a CD (in this case it isn't really a CD it just looks like one to Ubuntu)?

---

### Post by bernied on 2008-02-12
> **lotus49 said:**
> Having looked into this further it appears that ISO9660 filesystems do not have a UUID.  Identifying the filesystem by device name won't work as the next physical device I plug in is likely to be called /dev/sdc1 (regardless of whether it's my E220 or another flash disk or HDD) so how do I uniquely identify a CD (in this case it isn't really a CD it just looks like one to Ubuntu)?

Tricky. Two more ideas, both pretty vague I'm sorry:
- does the filesystem have a label? I think you can use this as an identifier for some filesystems in fstab. So instead of ```
/dev/sdc1 /mnt/nowhere ...
```something like```
LABEL=NastyModem /mnt/nowhere ...
```I don't know how you find the label on a ISO9660 filesystem under linux. Maybe [isoinfo](http://linux.die.net/man/8/isoinfo) could tell you something.
- investigate udev rules - the device will have a unique hardware ID that you should be able to make a rule for

And another idea that's not so vague - this is what I do when hardware really gets to me:
- get another modem

---

### Post by lyso on 2008-03-29
The following line works for me with a Huawei E220:

```

/dev/disk/by-id/usb-HUAWEI_Mass_Storage-0:0 /huawei  udf,iso9660 user,noauto,exec 0       0

```

i.e. /dev/disk/by-id should contain a link that is probably unique for the device. I don't have a CDROM drive for my laptop - so I can't test whether this has an effect on real CDs. But it shouldn't...

---

### Post by defmomo on 2008-03-29
I believe removing the line for that drive from the /etc/fstab file should remove stop it from being mounted automatically

---

### Post by dcstar on 2008-03-29
> **defmomo said:**
> I believe removing the line for that drive from the /etc/fstab file should remove stop it from being mounted automatically

External USB devices are** not** listed in the fstab file (and should not be in normal circumstances).

In this circumstance it is acceptable to list it, but the proper solution would be to modify a UDEV file to ignore this particular device (or just live with the Ubuntu automounting doing what it is supposed to do).

Having removable devices in the fstab file can cause all sorts of issues for the simple fact that the fstab file is essentially for permanent devices, not ones that may or may not be there during various system phases.

---

