---
title: "virtual cd drive"
date: 2005-09-30
forum: General Help
---

### Post by Jerrac on 2005-09-30
On windows I use a program called GameDrive to make virtual cds out of my game cds. That way I don't have to constantly switch cds all the time. How can I do that with Linux?

---

### Post by fabiand on 2005-10-06
Hey,

have a look at
[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)
or try:
```

dd if=/dev/cdrom of=my_cd_image.img
mkdir ~/my_cd_directory
sudo mount -oloop my_cd_image.img ~/my_cd_directory

```

- fabiand

---

### Post by Jerrac on 2005-10-09
Well, I have tried mounting the iso file I made into the cdrom directory under media. But the game I am trying it with won't regonize it as the cd. So... Any ideas what I could do?

And when I try to install cdemu it says this:
> firstuser@jerrac:~/Desktop/cdemu-0.7$ sudo make
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/firstuser/Desktop/cdemu-0.7 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/firstuser/Desktop/cdemu-0.7/cdemu.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/firstuser/Desktop/cdemu-0.7/cdemu.o] Error 127
make[1]: *** [_module_/home/firstuser/Desktop/cdemu-0.7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [all] Error 2
firstuser@jerrac:~/Desktop/cdemu-0.7$ sudo make install
**** Installing files ****
install -D -m 644 cdemu.ko      /lib/modules/2.6.12-9-386/misc/cdemu.ko
install: cannot stat `cdemu.ko': No such file or directory
make: *** [install] Error 1
firstuser@jerrac:~/Desktop/cdemu-0.7$


When I tried the code stuff, it didn't seem to do anything.

---

### Post by floyd27 on 2005-10-09
I would give up now while you can..
Linux and bin/cue files is not a match...

This is where linux falls apart..

---

### Post by madjo on 2005-10-09
[QUOTE=floyd27]I would give up now while you can..
Linux and bin/cue files is not a match...

This is where linux falls apart..[/QUOTE]
for you perhaps, others might be able to crack it.

---

### Post by floyd27 on 2005-10-09
you shouldnt have to ....
Wouldnt it be great if things just worked...

---

### Post by madjo on 2005-10-10
Most things work as it should. Just because it doesn't work for person A, doesn't automatically mean that it also doesn't work for person B.

That said, I have to say that I have yet to try cdemu or any of the other possible options for virtual cd drives (don't have a need for it yet, I don't download that many dvds).

---

