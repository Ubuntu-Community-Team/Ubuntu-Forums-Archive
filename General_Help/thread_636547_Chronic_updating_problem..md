---
title: "Chronic updating problem."
date: 2007-12-09
forum: General Help
---

### Post by sapu on 2007-12-09
After trying to update my Ubuntu Gutsy machine, I would get the following error:

```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

After clicking "Okay" (My only option) it closes the updater.
Apon typing "sudo apt-get install -f" I get this:

```
dpp@pmkcpu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gnome-games-data
Recommended packages:
  gnome-games-extra-data
The following packages will be upgraded:
  gnome-games-data
1 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B/9969kB of archives.
After unpacking 106kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 90315 files and directories currently installed.)
Preparing to replace gnome-games-data 1:2.20.0.1-0ubuntu2 (using .../gnome-games-data_1%3a2.20.1-0ubuntu1_all.deb) ...
Unpacking replacement gnome-games-data ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/gnome-games-data_1%3a2.20.1-0ubuntu1_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/gnome/help/gnomine/sv/figures/imnotsureflagscheckbox.png')
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-games-data_1%3a2.20.1-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And now I can't install anything via terminal. I can't install vmware, can't get a mp3 codec,

Current build (specs and details):
[http://reviews.cnet.com/laptops/hp-compaq-nx6125/4507-3121_7-31417988.html?tag=sub](http://reviews.cnet.com/laptops/hp-compaq-nx6125/4507-3121_7-31417988.html?tag=sub)

Also, I have almost no knowledge in linux or ubuntu. I know most of the basics.
i've also searched this site (and google) for a fix. I haven't found anything.

---

### Post by fjgaude on 2007-12-10
You can try this to get going again:

```
sudo apt-get clean
```

---

### Post by sapu on 2007-12-10
Yeah that really didn't seem to do much, but I wouldn't know, I'm not educated in Linux that well. But after I did that, I went into the Packet Manager and went to "filters" and went to "broken" and re-installed the broken packages.

Everything seems fixed now.

---

