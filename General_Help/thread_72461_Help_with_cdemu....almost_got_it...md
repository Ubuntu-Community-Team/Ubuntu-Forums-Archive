---
title: "Help with cdemu....almost got it.."
date: 2005-10-06
forum: General Help
---

### Post by floyd27 on 2005-10-06
I tired to install but it didnt go well.
1.  extract the archive:
$ tar -jxvf cdemu-<VER>.tar.bz2
2. you need the source of your current running kernel.
/lib/modules/$(shell uname -r)/build/include needs to point at it.
3. build the module:
$ make
4. install the module and user space utilities:
$ sudo make install
5. now simply load the kernel module:
$ sudo modprobe cdemu
(no message should be displayed after running modprobe)
6. to load a bin/cue image:
$ cdemu 0 image.cue
$ mount /dev/cdemu/0 /mnt/cdrom
(some things may be different on your system, YMMV)
7. for more information, please review the help output:
$ cdemu -h
Can someone help with step 2 and 6...?
Step 2 i have no idea ..
step 6 I imagine that i would replace image cue with the actual image? Di i have to be in the dir thats its located?
thanx

---

### Post by floyd27 on 2005-10-06
Hi...

2. you need the source of your current running kernel.
/lib/modules/$(shell uname -r)/build/include needs to point at it.

where it says /lib/....../build/.......
im not sure what to do with this. I know my kernel module..But where does the line STOP..? @ /build or /build/include or ?????
And what does needs to point at it mean??? the dir?  I just dont understand the directions to well?

---

### Post by floyd27 on 2005-10-06
ok its installed..
but cant aactually mount anything..
can someone sho w me an examle.
i look at every cdemu post on here and none helped..
thanx

---

### Post by az on 2005-10-06
If you install the linux-headers-2.6.10-5-386 package (or the version that matches your kernel, if you are not running that kernel) it makes the build symlink for you.  

As for using cdemu,  I dunno.

---

### Post by floyd27 on 2005-10-06
well i have it installed and did manage to mount a cue file.
but cant open it..im looking into it now..

---

