---
title: "Update Manager update troubles"
date: 2008-05-29
forum: General Help
---

### Post by gfixler on 2008-05-29
I've had some Update Manager update troubles, and I think it's just that I was out of space on my /boot partition. I've managed to get everything in the past 2 days of these errors to install, but usually end up with a series of errors in a popup window. I've cleared up 66% of /boot by moving all the old 2.6.24-14 stuff to a different partition, but don't know how to get the parts that errored out to fix themselves up now. It seems to be related to updating, or installing in the first place the 2.6.24-17 stuff. Any clues? I could probably wait for the next string of updates now that I have the space, but that's not guaranteed to fix it, and I'm curious about what happened, and how to force it through myself anyway. Thanks!

Here's what was in the error message popup window:

```
E: linux-image-2.6.24-17-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-17-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-17-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
```



Here's what was left in the Update Manager's built-in console after the error (I made bold the out-of-space error, and have since cleared up 66% of the space on /boot (was 5% previously)):

```
(Reading database ... 200834 files and directories currently installed.)
Preparing to replace f-spot 0.4.2-1ubuntu3 (using .../f-spot_0.4.3.1-0ubuntu1_amd64.deb) ...
Unpacking replacement f-spot ...
Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

**gzip: stdout: No space left on device**
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-generic:
 linux-ubuntu-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
  Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-generic:
 linux-restricted-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-17-generic; however:
  Package linux-restricted-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.17.19); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up f-spot (0.4.3.1-0ubuntu1) ...

Errors were encountered while processing:
 linux-image-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-17-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-17-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

**gzip: stdout: No space left on device**
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-generic:
 linux-ubuntu-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
  Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-generic:
 linux-restricted-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-17-generic; however:
  Package linux-restricted-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.17.19); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
```

---

### Post by pelle.k on 2008-05-29
You may try ```
sudo dpkg --confiure -a
```

---

### Post by gfixler on 2008-05-29
> **pelle.k said:**
> You may try ```
sudo dpkg --configure -a
```

That did it, thanks!

---

### Post by Shazaam on 2008-05-29
Other commands that help sometimes....
```
sudo apt-get install -f
```
or...
```
sudo aptitude install -f
```

-f means fix-broken.

---

### Post by plucky on 2008-05-29
> -f means force

From **man apt-get**

 > -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. Any Package that are
           specified must completely correct the problem. The option is
           sometimes necessary when running APT for the first time; APT itself
           does not allow broken package dependencies to exist on a system. It
           is possible that a system´s dependency structure can be so corrupt
           as to require manual intervention (which usually means using
           dselect or dpkg --remove to eliminate some of the offending
           packages). Use of this option together with -m may produce an error
           in some situations. Configuration Item: APT::Get::Fix-Broken.


---

### Post by fprintf on 2008-07-22
> **pelle.k said:**
> You may try ```
sudo dpkg --confiure -a
```

Awesome, it worked. I did need to allow the system to overwrite menu.lst, and then had to manually go back and fix it. Apparently the "three way" merge isn't quite 100% just yet and that is why the dependency errors.

---

