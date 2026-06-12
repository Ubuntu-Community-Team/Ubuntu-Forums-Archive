---
title: "chroot from liveusb, should you be able to install, update, upgrade?"
date: 2014-05-09
forum: General Help
---

### Post by sdowney717 on 2014-05-09
I tried and cant.
I can navigate folders.
followed this to chroot
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

specific commands I ran are

> sudo mount /dev/sdb1 /mnt
sudo chroot /mnt


```
root@ubuntu:/# apt-get update
Err http://security.ubuntu.com trusty-security InRelease
  
Err http://extras.ubuntu.com trusty InRelease
  
Err http://us.archive.ubuntu.com trusty InRelease
  
Err http://us.archive.ubuntu.com trusty-updates InRelease
  
Err http://us.archive.ubuntu.com trusty-backports InRelease
  
Err http://security.ubuntu.com trusty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com trusty Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com trusty-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://extras.ubuntu.com trusty Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err http://us.archive.ubuntu.com trusty-backports Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
root@ubuntu:/# apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  docbook-xml libcairo-perl libept1.4.12 libglib-perl libgtk2-perl
  libpango-perl librarian0 rarian-compat sgml-data
Suggested packages:
  docbook docbook-dsssl docbook-xsl docbook-defguide libfont-freetype-perl
  libgtk2-perl-doc perlsgml w3-recs opensp libxml2-utils dwww menu deborphan
  tasksel
The following NEW packages will be installed:
  docbook-xml libcairo-perl libept1.4.12 libglib-perl libgtk2-perl
  libpango-perl librarian0 rarian-compat sgml-data synaptic
0 upgraded, 10 newly installed, 0 to remove and 81 not upgraded.
Need to get 3,441 kB of archives.
After this operation, 17.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libept1.4.12 amd64 1.0.12
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main sgml-data all 2.0.9-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main docbook-xml all 4.5-7.2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe libcairo-perl amd64 1.104-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe libglib-perl amd64 3:1.304-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe libpango-perl amd64 1.224-2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe libgtk2-perl amd64 2:1.249-2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main librarian0 amd64 0.8.1-5ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main rarian-compat amd64 0.8.1-5ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe synaptic amd64 0.81.1
  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libe/libept/libept1.4.12_1.0.12_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/sgml-data/sgml-data_2.0.9-1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/docbook-xml/docbook-xml_4.5-7.2_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libc/libcairo-perl/libcairo-perl_1.104-1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libg/libglib-perl/libglib-perl_1.304-1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libp/libpango-perl/libpango-perl_1.224-2_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libg/libgtk2-perl/libgtk2-perl_1.249-2_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rarian/librarian0_0.8.1-5ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rarian/rarian-compat_0.8.1-5ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/s/synaptic/synaptic_0.81.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu:/# ls
bin    dev   initrd.img  lost+found  opt   run	 sys  var
boot   etc   lib	 media	     proc  sbin  tmp  vmlinuz
cdrom  home  lib64	 mnt	     root  srv	 usr
root@ubuntu:/# cd media
root@ubuntu:/media# ls
floppy	floppy0
root@ubuntu:/media# cd ..
root@ubuntu:/# ls
bin    dev   initrd.img  lost+found  opt   run	 sys  var
boot   etc   lib	 media	     proc  sbin  tmp  vmlinuz
cdrom  home  lib64	 mnt	     root  srv	 usr
root@ubuntu:/# cd tmp
root@ubuntu:/tmp# ls
root@ubuntu:/tmp# mkdir 
mkdir: missing operand
Try 'mkdir --help' for more information.
root@ubuntu:/tmp# mkdir test
root@ubuntu:/tmp# ls
test
root@ubuntu:/tmp# rmdir test
root@ubuntu:/tmp# ls
root@ubuntu:/tmp# 

```

---

### Post by steeldriver on 2014-05-09
Sounds like a networking issue - did you include /run as one of the bind-mounted dirs in the chroot?

---

### Post by sdowney717 on 2014-05-09
No, please tell me more on what to do?

[http://lukeplant.me.uk/blog/posts/sharing-internet-connection-to-chroot/](http://lukeplant.me.uk/blog/posts/sharing-internet-connection-to-chroot/)

got it!
resolve.conf is needed in bind

I also bound /tmp

---

### Post by steeldriver on 2014-05-09
It's a while since I've done this so you may want to wait for someone more knowledgeable to chime in, but iirc you should be doing something like

```

sudo mount /dev/sdb1 /mnt

```
then
```

[COLOR=#0000ff]sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /run /mnt/run[/COLOR]

```
before you 
```

sudo chroot /mnt

```

---

