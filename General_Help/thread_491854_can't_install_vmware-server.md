---
title: "can't install vmware-server"
date: 2007-07-04
forum: General Help
---

### Post by jammodotnet on 2007-07-04
hello.
am trying the tutorial here: [http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/](http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/)

i keep getting stuck at the part where i install vmware.
apparently, i have it installed.
> A previous installation of a VMware product has been detected.
If you installed it from the VMware website, please remove it by running vmware-uninstall.pl before
proceeding.
If it was installed through Ubuntu, you must purge (completely remove) the old package.

a few months, i DID install it using automatix.
never used it, nor did i uninstall it.

i removed vmware and all associated dependencies via synaptic, i even restart, to be sure.
still get the error.

ive tried to install vmware-server via:
synaptic
automatix
and even commandline following this toot: [http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

can someone help me TOTALLY remove the old packages?
if i can do what is mentioned in the first tutorial above '10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop' then i wouldnt need wine, right?
cause i cant use Macromedia Fireworks MX in Wine cause it crashes after 10-15 minutes of use.

---

### Post by scxtt on 2007-07-04
did you run **vmware-uninstall.pl**?
did you *purge* it?

---

### Post by jammodotnet on 2007-07-04
> **scxtt said:**
> did you run **vmware-uninstall.pl**?
i've searched for this file, i cant locate it.

shouldnt it be under _/usr/bin/_ ?

> **scxtt said:**
> did you *purge* it?
i searched the forum, this seemed to work.
```
sudo aptitude purge vmware-server vmware-tools-kernel-modules
```

but then when i try to install again, i get the same error.

i know im not doing SOMEthing right.
:(

---

### Post by Gallows on 2007-07-04
Assuming you have removed it properly as suggested in the above post you could try manually removing any reference to VMWare in /etc/init.d.  I seem to remember having to manually remove a VMWare startup script when I removed VMWare Player... maybe it's a similar thing.

---

### Post by altonbr on 2007-07-04
```
sudo rm -r /etc/vmware
```

That is a remnant of the previous install. Remove that, and you should be ready to install it once again.

See the bottom of my HOWTO here: [http://ubuntuforums.org/showthread.php?t=342631](http://ubuntuforums.org/showthread.php?t=342631)

---

### Post by scxtt on 2007-07-04
> **jammodotnet said:**
> i've searched for this file, i cant locate it.

shouldnt it be under _/usr/bin/_ ?hmm, i generally install via the vmware tar file, didn't do it this time (used the one from the repo) and i don't have the perl script either - bummer ...

> i searched the forum, this seemed to work.
```
sudo aptitude purge vmware-server vmware-tools-kernel-modules
```yeah, that looks like what i was thinking ... the only thing else i can think of would be:

sudo slocate -u
sudo slocate vmware

and delete all references ...

---

### Post by altonbr on 2007-07-05
Even if you purge VMware, /etc/vmware still sticks around so you have to remove it. Once you remove it, you can install a fresh copy. That's all VMware is looking at in regards to a previous installation. Seems silly, but it's true.

---

### Post by Nano Geek on 2007-07-06
Try this:
```
sudo rm -r /etc/init.d/vmware*

```Running that worked for me.

---

