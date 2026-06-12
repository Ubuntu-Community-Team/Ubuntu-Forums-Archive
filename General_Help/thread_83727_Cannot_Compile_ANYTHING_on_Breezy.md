---
title: "Cannot Compile ANYTHING on Breezy"
date: 2005-10-29
forum: General Help
---

### Post by arvmenon on 2005-10-29
I searched the forum and Google a lot before positng this, so please forgive me if I sound a bit edgy. I have been trying to get the hdaps and ibm_acpi module to compilefor the past 2 days now with no success. It is really ANNOYING that installing the kernel source and the kernel header files take so long and is so COMPLICATED compared to say Fedora. I looked through the posts and installed the linux-headers, linux-sources not to mention build-essentials and others.

My errors
_________

For hdaps

 make
make -C /lib/modules/2.6.12-9-686/build SUBDIRS=/home/arvmenon/Desktop/hdaps-20050825-02/kernel modules
make[1]: Entering directory `/lib/modules/2.6.12-9-686/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-686/build'
make: *** [default] Error 2


For ibm_acpi

make
make -C /lib/modules/2.6.12-9-686/build SUBDIRS=/home/arvmenon/Desktop/ibm-acpi-0.11 modules
make[1]: Entering directory `/lib/modules/2.6.12-9-686/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-686/build'
make: *** [default] Error 2


Is there ANYTHING left to do after installing the linux-headers, linux-source and the build-essentials package?

I have been seeing a lot of articles about how to compile a custom kernel, but not anything related to compiling a module AGAINST A KERNEL SOURCE.

I would appreciate any help you guys can give me.

Whats funny is that compiling programs was straightforward as anything in Fedora.

Anyway,
Cheers

---

### Post by jeremyk on 2005-10-29
I think your problem is the following:

the kernel 2.12 has been compiled with gcc 3.4 et the compiler that is installed by default is gcc 4.

So install gcc 3.4 and edit your bash.bashrc file:

gedit  /etc/bash.bashrc

add at the end of the file:

export CC=/usr/bin/gcc-3.4

I hope it will help.

---

### Post by arvmenon on 2005-10-29
Thanks for the reply, but I tried that. It still does the same thing.

---

### Post by bionnaki on 2005-10-29
sudo apt-get install build-essential

---

### Post by arvmenon on 2005-10-29
Again, I had installed all that. But it still gave me the same error.

---

### Post by mo_x on 2005-10-29
Did you install the headers for linux-kernel-2.6.12-9-686 ?
If you familiar with the syntax of makefiles you can take a look at the Makefile in the /lib/modules/2.6.12-9-686/build directory (link to your headers directory).

---

### Post by arvmenon on 2005-10-29
[QUOTE=mo_x]Did you install the headers for linux-kernel-2.6.12-9-686 ?
If you familiar with the syntax of makefiles you can take a look at the Makefile in the /lib/modules/2.6.12-9-686/build directory (link to your headers directory).[/QUOTE]

I tried pointing it to the headers directory and I got this.

arvmenon@anvil-t42-avm:~/setups/hdaps-20050825-02/kernel$ make
make -C /usr/src/linux-headers-2.6.12-9-686 SUBDIRS/=/home/arvmenon/setups/hdaps-20050825-02/kernel modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-686'
  CHK     include/linux/version.h
/bin/sh: include/linux/version.h.tmp: Permission denied
  UPD     include/linux/version.h
mv: cannot stat `include/linux/version.h.tmp': No such file or directory
make[1]: *** [include/linux/version.h] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-686'
make: *** [default] Error 2

I did the same thing with sudo, but this time I got a different error.

arvmenon@anvil-t42-avm:~/setups/hdaps-20050825-02/kernel$ sudo make
make -C /usr/src/linux-headers-2.6.12-9-686 SUBDIRS/=/home/arvmenon/setups/hdaps-20050825-02/kernel modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-686'
  CHK     include/linux/version.h
  UPD     include/linux/version.h
make[2]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-686'
make: *** [default] Error 2


Any ideas?


Here is the makefile (original)

# Makefile for hdaps driver

obj-m += hdaps.o

default:
	make -C /lib/modules/$(shell uname -r)/build SUBDIRS=$(PWD) modules

install:
	install -D --mode=644 hdaps.ko \
		/lib/modules/`uname -r`/kernel/drivers/misc/hdaps.ko
	/sbin/depmod -A

clean:
	rm -rf *.o *.ko *.mod.c .hdaps.*.cmd .tmp_versions

---

### Post by mo_x on 2005-10-30
There seems to be something wrong with your setup.
I would try to remove and reinstall the linux-headers-2.6.12-9-686 package.
Check that the /lib/modules/2.6.12-9-686/build directory is linked to the /usr/src/linux-headers-2.6.12-9-686 directory. Then try again to compile with the original makefile.

Also from your altered makefile ist shows "SUBDIRS/=...", the "/" should not be there i think, typo?

---

