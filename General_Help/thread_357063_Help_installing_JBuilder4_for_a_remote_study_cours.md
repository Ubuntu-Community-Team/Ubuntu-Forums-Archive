---
title: "Help installing JBuilder4 for a remote study course"
date: 2007-02-09
forum: General Help
---

### Post by theolster on 2007-02-09
Hi,

I'm studying Java with the Open University in the UK.  This course requires JBuilder4 to be installed, and on the CD provided they have installers for Windows, Solaris and Linux :-)

Since I only use Windoze for my Uni work I'd really like to get this working on Edgy - then I can delete that damn MS partition.

The install guide says this:> 
If you encounter errors when installing JBuilder using the main installation launcher, you can install each component separately. The sequence of installation is important, so install them in this order:

   1. fnd_linux_install.bin
   2. doc_install.bin (optional)
   3. smp_install.bin (optional) And this is the result> $ fnd_linux_install.bin
bash: fnd_linux_install.bin: command not foundPlease help!

---

### Post by theolster on 2007-02-13
Does anyone know how to identify which command isn't found?  Hmmm...

---

### Post by cawebster on 2007-04-07
I just learned this one trying to install JBuilder 7.

try:

./fnd_linux_install.bin

I was told that Linux doesn't recognize executable programs the same as Windoze and that if there wasn't a path set up you had to precede executables with a ./ .  You'll probably also need to use sudo to install it as root.

sudo ./fnd_linux_install.bin

I hope this is helpful.  I got past this part and have run into all manner of trouble that I don't begin to understand.

---

