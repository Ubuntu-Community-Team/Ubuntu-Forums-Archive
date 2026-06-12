---
title: "Software index Broken please help me"
date: 2007-05-15
forum: General Help
---

### Post by heather on 2007-05-15
Hi

My Software index Broken
When i tried to update and
it told me to

sudo apt-get install -f

my output is


sudo apt-get install -f
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
electricity@lqx:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libmjpegtools0
The following NEW packages will be installed:
  libmjpegtools0
0 upgraded, 1 newly installed, 0 to remove and 33 not upgraded.
2 not fully installed or removed.
Need to get 0B/229kB of archives.
After unpacking 631kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libmjpegtools0
Install these packages without verification [y/N]? y
(Reading database ... 91800 files and directories currently installed.)
Unpacking libmjpegtools0 (from .../libmjpegtools0_1%3a1.8.0-0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
lqx:~$

---

### Post by mahy on 2007-05-15
Are you sure no other relevant apps are running? How about firing up Synaptic and letting it fix broken packages?

---

### Post by ayoli on 2007-05-15
you may try :
```
sudo dpkg --force-all -i /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb
```

---

### Post by heather on 2007-05-15
Hm something seems to have worked that time Thank you

(sound problem fixed as well)


But for some reason my start up sounds are gone (((in kde only not in gnome)))

i dont even have a mixer volume control in add to panel section and i have chosen the correct sound device becasue my wav sounds play fine in recorcer.

Perhaps when i added kdebase not everything was installed correctly
during that broken phase?

i Deinstalled then reinstalled kde then installed the sound mixer
so all is well again Thank You


Thank YOu

---

