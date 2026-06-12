---
title: "CDemu"
date: 2005-04-15
forum: General Help
---

### Post by Dracontopes on 2005-04-15
I am trying to make cdemu work so I can mount cue/bin files. When I get to the point where I must load the module, an error occurs.

```
chris@chris:~ $ sudo modprobe cdemu
Password:
FATAL: Error inserting cdemu (/lib/modules/2.6.11-1-k7/misc/cdemu.ko): Invalid module format
chris@chris:~ $
```

Any help on this? ;) (Is it because I am using a fairly new kernel?)

[http://cdemu.sourceforge.net]("http://cdemu.sourceforge.net")

---

### Post by az on 2005-04-15
"Current Release: 0.7
This release supports the 2.4 and 2.6 Linux kernels.
cdemu-0.7.tar.bz2 

"

How did you make the module?

---

### Post by Dracontopes on 2005-04-15
This is what I was trying to do:

The install is quite simple:

  [list=1]
[*]extract the archive: $ tar -jxvf cdemu-<VER>.tar.bz2
[*]you need the source of your current running kernel.
     /lib/modules/$(shell uname -r)/build/include needs to point at it.
[*]build the module:      $ make
[*]install the module and user space utilities:      $ sudo make install
[*]now simply load the kernel module:      $ sudo modprobe cdemu
      (no message should be displayed after running modprobe)
[*]to load a bin/cue image:      $ cdemu 0 image.cue
      $ mount /dev/cdemu/0 /mnt/cdrom
      (some things may be different on your system, [YMMV]("http://www.everything2.com/index.pl?node_id=YMMV"))
[*]for more information, please review the help output:      $ cdemu -h
 
[/list] I am trying to install 0.7, yes :)

---

### Post by Dracontopes on 2005-04-15
Ow, I just checked dmesg and this came up:

```

cdemu: version magic '2.6.11-1-k7 preempt K7 gcc-4.0' should be '2.6.11-1-k7 preempt K7 gcc-3.3'

```

gcc-4.0 was auto-installed with Breezy updates... What now?

---

### Post by az on 2005-04-16
Use synaptic to remove it...


You can tell the compiler to use any version of gcc installed but just removeing gcc 4.0 will probably save you a lot of headache for the time being...

---

### Post by Dracontopes on 2005-04-16
[QUOTE=azz]Use synaptic to remove it...


You can tell the compiler to use any version of gcc installed but just removeing gcc 4.0 will probably save you a lot of headache for the time being...[/QUOTE]
 When I want to remove gcc-4.0, synaptic will also remove the gcc package and build-essential... When I do that, any make command will result in messages like cannot find gcc... :(

So, how can I tell a compiler to use another gcc version?

---

### Post by soritong on 2005-05-27
[QUOTE=Dracontopes]When I want to remove gcc-4.0, synaptic will also remove the gcc package and build-essential... When I do that, any make command will result in messages like cannot find gcc... :(

So, how can I tell a compiler to use another gcc version?[/QUOTE]
 Regarding step number 2....what EXACTLY am I supposed to do? I'm a bit of a newbie and I'm completely baffled

---

