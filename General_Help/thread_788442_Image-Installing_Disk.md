---
title: "Image-Installing Disk"
date: 2008-05-09
forum: General Help
---

### Post by gali98 on 2008-05-09
Hey guys!

So I have a thing I'm trying to work on. Basically I want to be able to take an image of a hard drive (or partition) and put it on a bootable disk with the sole purpose of this disk is to be able to  pop it in and boot from it. 
Once booted the disk will load some kind of environment that will automatically copy over the image to the hard drive.
I think this seems very simple...
to make the image simply do:
```
dd if=/dev/sda of=image.img
```
then slap that on a disk (when I say disk I really mean a dvd, but I suppose I could also do it with a usb drive)
that has a small bootable linux that loads up and executes the command:
```
dd if=image.img of=/dev/sda
```

This seems very simple, but I've never seen it anywhere. I guess most people use ghost of the oss equivilent, but I want to be network dependent.

A couple of other things that could be added is that it would format the disk before imaging and etc....

I don't really know how to get started... so if anybody could help me, or point me in the right direction, or point out the errors in my thinking, I would 'preciate it very much!:)
Kory

---

### Post by gali98 on 2008-05-10
Hey guys... Just bumping this thread once cause there are only 11 views and most of them are mine :P
Cheers,
Kory

---

### Post by gali98 on 2008-05-12
Does anyone know where to start with this? Should I just start with something like DSL or the like? Please help.... This could be a big timer-saver. Thanks,
Kory

---

