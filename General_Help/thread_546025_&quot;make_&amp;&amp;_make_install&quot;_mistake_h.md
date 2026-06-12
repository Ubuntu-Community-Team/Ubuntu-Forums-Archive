---
title: "&quot;make &amp;&amp; make install&quot; mistake how to correct?"
date: 2007-09-08
forum: General Help
---

### Post by thegreatbeste on 2007-09-08
Hi there.

I tried to get the sony_acpi to work and followed a tutorial ([url"http://www.peterschultz.de/ffsony.shtml]here[/url]  in german)

i somehow forgot to edit the Makefile from "KDIR := /lib/modules/$(shell uname -r)/build" to "KDIR := /lib/modules/$(shell uname -r)/".

But it compiled without any errors.
```
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/isabelle/t/sony_acpi modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/isabelle/t/sony_acpi/sony_acpi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/isabelle/t/sony_acpi/sony_acpi.mod.o
  LD [M]  /home/isabelle/t/sony_acpi/sony_acpi.ko
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.20-16-generic'
cp sony_acpi.ko /lib/modules/2.6.20-16-generic/kernel/drivers/acpi/
depmod -a

```

Now i have the problem that i got no fnkey support (Sony hotkey) and so it wont let me run fsfn to use keys for brightness.

So i tried to compile again with the correct Makefile, but i just get errors
```
make -C /lib/modules/2.6.20-16-generic/ SUBDIRS=/home/isabelle/t/sony_acpi modules
make[1]: Betrete Verzeichnis '/lib/modules/2.6.20-16-generic'
make[1]: *** Keine Regel, um »modules« zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis '/lib/modules/2.6.20-16-generic'
make: *** [default] Fehler 2

```

simply says no rules to create >>modules<<

What do i need to make undone to recompile with the coorect makefile??

I already replaced the compiled files with the original files from the archive

---

### Post by wirelessmonkey on 2007-09-08
Try
make clean
make 
make install

---

### Post by thegreatbeste on 2007-09-08
Same error

```
root@isabelle-laptop:~/t/sony_acpi# make clean && make && make install
rm -rf *.[oas] .*.flags *.ko .*.cmd .*.d .*.tmp *.mod.c .tmp_versions
make -C /lib/modules/2.6.20-16-generic/ SUBDIRS=/home/isabelle/t/sony_acpi modules
make[1]: Betrete Verzeichnis '/lib/modules/2.6.20-16-generic'
make[1]: *** Keine Regel, um »modules« zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis '/lib/modules/2.6.20-16-generic'
make: *** [default] Fehler 2

```

i hope i got this right with make clean, make and make install

---

