---
title: "No Synaptic, No Dpkg, How Do I Install?"
date: 2006-12-16
forum: General Help
---

### Post by Ohmz on 2006-12-16
I recently got ahold of a Soekris board, with a 233mhz processor, 128 onboard ram, 3 network ports, a miniPCI slot, and a compact flash slot. I installed a stripped down version of Ubuntu on the flash card from an image someone made for me. Unfortunetely the image was so stripped down it doesn't contain any of the apt functions or dkpg. I got ahold of the source for synaptic and dkpg but I need a C compiler. Of course the only ones I can find are in .deb format.
    Is there any way to install .deb files without dkpg or synaptic, or can anyone point me in the direction of a C compiler that isn't a deb file. So far I haven't been able to install any new programs on the system and am getting a bit frustrated.

---

### Post by pay on 2006-12-16
Try extracting the debs and copying the files to the appropriate place (they will be categorised in folders when you extract it to it won't be hard to figure out where they go).

---

### Post by az on 2006-12-17
--root=dir | --admindir=dir | --instdir=dir
              Change   default   directories.    admindir  defaults  to
              /var/lib/dpkg and contains many files that give  informa&#8208;
              tion  about  status of installed or uninstalled packages,
              etc.  instdir defaults to / and refers to  the  directory
              where  packages are to be installed.  instdir is also the
              directory passed to chroot(2)  before  running  package&#8217;s
              installation  scripts,  which  means that the scripts see
              instdir as a root directory.  Changing root changes inst&#8208;
              dir to dir and admindir to dir/var/lib/dpkg.

Ex:
sudo dpkg -i file.deb --root=/media/sda1

Use the --root parameter in dpkg to install the dpkg deb to your flash card.  You should be able to mount the flash card on an ubuntu computer and then install the package(s) from there.

Kinda like chrooting into your flash card, but you use the package manager of the ubuntu system you are running.  That's how the alternate installer does it.

---

### Post by Ohmz on 2006-12-17
Great idea!! I didn't even think of putting the flash card back into my writer and just using my desktop to install the package management programs. Thanks!

---

### Post by az on 2006-12-17
It's amazing.  There's always some command-line switch for everything.....

---

