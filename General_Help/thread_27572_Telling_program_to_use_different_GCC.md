---
title: "Telling program to use different GCC"
date: 2005-04-16
forum: General Help
---

### Post by Dracontopes on 2005-04-16
With the new Breezy updates, GCC-4.0 was installed. The kernel-image I am using was compiled with gcc 3.3. Now I need to compile a module (see this thread: [http://www.ubuntuforums.org/showthread.php?t=27256](http://www.ubuntuforums.org/showthread.php?t=27256)) but it does not work when compiled with the standard gcc version (which is 4.0). 

Is there any way to tell "make" to use a different gcc version? In synaptic I can see that version 3.3 is also installed. Or must I configure gcc to use other another version?

(Uninstalling 4.0 is rather difficult as this will also uninstall the standard gcc package. As a result the gcc command is disfunctional... :/ )

---

### Post by dataw0lf on 2005-04-16
You should be able to use it by 'gcc-3.3' rather than 'gcc'.

---

### Post by Stormy Eyes on 2005-04-16
Gentoo had a gcc-config tool that would let you choose which version of GCC to use, but I suspect that it's specific to Gentoo as a Google search doesn't turn up any references to gcc-config in Debian. Couldn't you just remove gcc 4, install gcc 3.3, and go on from there? If not, then why not try rebuilding the kernel with gcc 4?

---

### Post by Dracontopes on 2005-04-17
[QUOTE=dataw0lf]You should be able to use it by 'gcc-3.3' rather than 'gcc'.[/QUOTE]
 Well, I'm trying to do something like "make", which will create a module. The modules wil have to be made with gcc-3.3, not 4.0 (or it won't work) So where can I tell "make" to use another gcc versioN?

Uninstalling 4.0 is not really an option because it will break the gcc package. I am rebuilding my 2.6.11 kernel, I loaded the default 2.6.11 config file which came with the ubuntu2.6.11kernel. It will automatically be compiled with gcc verison 4.0 right?

---

### Post by khc on 2005-04-17
man update-alternative, or just symlink /usr/bin/gcc-3.3 to /usr/bin/gcc

---

### Post by nautilus on 2005-04-17
or do: ./configure CC=gcc-3.3; make CC=gcc-3.3

or

export CC=gcc-3.3
./configure
make

---

### Post by Dracontopes on 2005-04-17
Thank you both, that did the trick :)

Happy man now :-\"

---

### Post by bigblop on 2005-07-08
when I type ./configure I just get:

johs@ubuntu:/usr/bin$ ./configure ++=g++-2.95
bash: ./configure: No such file or directory
johs@ubuntu:/usr/bin$


I am trying to do it with the g++ compiler instead.


From which dir should I run ./configure?

---

