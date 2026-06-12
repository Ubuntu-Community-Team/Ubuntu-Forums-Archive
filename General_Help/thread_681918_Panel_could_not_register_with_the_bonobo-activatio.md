---
title: "Panel could not register with the bonobo-activation server"
date: 2008-01-29
forum: General Help
---

### Post by clicknclack on 2008-01-29
Hi,

I'm running Ubuntu 7.10 on x86 64-bit machine.

Gnome panel (top and bottom desktop panels) do not appear, and I get the following popup error message:

{
The panel has encountered a fatal error

The panel could not register with the bonobo-activation server (error code: 1) and will exit.
It may be automatically restarted.
}

Any ideas on how to fix this.

Thank you.

---

### Post by fhaverkamp on 2008-02-17
I am getting a very similar message but error code: 3. My system is a Core2 Quad Q6600 4x2.4GHz with 4GB RAM. Have you found a solution yet?
As an experiment I tried the 32-bit version. That worked without trouble. I removed 2GB RAM and tried the 64-bit version again, with no success.

---

### Post by Tuxoid on 2008-02-24
ya, I tried to reinstalled libbonobo2-common with:

```
sudo apt-get install --reinstall libbonobo2-common --force-yes
```

it gives me a couple errors:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/599kB of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 197201 files and directories currently installed.)
Preparing to replace libbonobo2-common 2.20.0-0ubuntu1 (using .../libbonobo2-common_2.20.0-0ubuntu1_i386.deb) ...
Unpacking replacement libbonobo2-common ...
dpkg: error processing /cdrom//pool/main/libb/libbonobo/libbonobo2-common_2.20.0-0ubuntu1_i386.deb (--unpack):
 unable to stat `./usr/share/gtk-doc/html/bonobo-activation' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /cdrom//pool/main/libb/libbonobo/libbonobo2-common_2.20.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I got the same basic problem everyone else in the thread does. KDE 3.5 was broken as well, but I have fixed it and now its fully functional. it all happened after using gparted to fix some ext3 issues. Funny, it never affected XFCE or KDE 4.0.

I'm under Ubuntu 7.10 and I'm willing to fix it at the Terminal if needed.

---

### Post by Tuxoid on 2008-02-24
> **Tuxoid said:**
> ya, I tried to reinstalled libbonobo2-common with:

```
sudo apt-get install --reinstall libbonobo2-common --force-yes
```

it gives me a couple errors:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/599kB of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 197201 files and directories currently installed.)
Preparing to replace libbonobo2-common 2.20.0-0ubuntu1 (using .../libbonobo2-common_2.20.0-0ubuntu1_i386.deb) ...
Unpacking replacement libbonobo2-common ...
dpkg: error processing /cdrom//pool/main/libb/libbonobo/libbonobo2-common_2.20.0-0ubuntu1_i386.deb (--unpack):
 unable to stat `./usr/share/gtk-doc/html/bonobo-activation' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /cdrom//pool/main/libb/libbonobo/libbonobo2-common_2.20.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I got the same basic problem everyone else in the thread does. KDE 3.5 was broken as well, but I have fixed it and now its fully functional. it all happened after using gparted to fix some ext3 issues. Funny, it never affected XFCE or KDE 4.0.

I'm under Ubuntu 7.10 and I'm willing to fix it at the Terminal if needed.

Fixed it! Just run the command line I gave and cd into the directory dpkg says it's 'unable to stat' and remove the file it's 'unable to stat' and run the apt line again. Keep this up until apt-get no longer says it's 'unable to stat' files and it will then install.

---

