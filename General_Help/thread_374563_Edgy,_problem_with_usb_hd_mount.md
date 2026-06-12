---
title: "Edgy, problem with usb hd mount"
date: 2007-03-02
forum: General Help
---

### Post by francesco44 on 2007-03-02
I have two different machines. A desktop with Dapper, a laptop with Edgy, no customization ever. Straightforward and happy install!

I have a small USB HD (4Giga) which is perfectly detected and mounted in Dapper. But not in Edgy the volume is detected but characterized with a flag as "impossible to mount". I have also the same kind of problem with a USB Key, one partition (in the unix file format I suppose) is perfectly recognized, the other partition is detected but not mounted. Another key is not recognized at all.

Looking through  the forums, I didn't find the solution, but it seem that other people have the same problem. Looking through the wiki gave me the information that something new regarding the mounting of disks and partitions has changed in Edgy (UUID?). But I could not understand it properly.

Thank you for a short explanation to a new ubuntu (and unix) user!

---

### Post by bodhi.zazen on 2007-03-02
Well, as to uuid, you can mount a device by location, label, or uuid

mount /dev/sda1 .......

mount LABEL=xxx ......

mount UUID=xxx-yyy-zzz

To list your devices by uuid :

enter this command in a termianl :

```
blkid
```

For further information on uuid : [http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

fstab & options : [http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)


=======

As to your problem, I have no idea ....

Connect your devices and post the output of :

```
sudo fdisk -l
```

Also try pmount :

```
pmount /dev/sda1 usb
```

That command should mount the usb at /media/usb ....

Post any error messages ....

---

### Post by francesco44 on 2007-03-04
Thanks Bodhi, I have too mucch to do to try today but I will follow your advices

Piero Franchesco

---

