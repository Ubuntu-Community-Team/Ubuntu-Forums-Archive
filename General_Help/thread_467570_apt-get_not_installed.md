---
title: "apt-get not installed"
date: 2007-06-07
forum: General Help
---

### Post by AllanP on 2007-06-07
I just installed Debian Etch on another partition. All went well except that now when I boot Ubuntu I get among other things "apt-get not installed install by typing apt-get install apt" which doesn't work. I restored a backup image of Ubuntu and still get the same message. I have to hit Ctrl-D to continue boot. I never touched the MBR where Ubuntu resides. Hope I explained this well enough. While booting it said there would be an error log at /var/log/fsck/checkfs which wasn't there.

---

### Post by pbw on 2007-06-07
wget it, then use dpkg to reinstall. Sounds like you have more issues than just that however.

---

### Post by AllanP on 2007-06-07
Thanks for the quick reply and yes it does sound like more problems which, weren't there before my Debian install. Regretting already. Maybe have to re-install Ubuntu.

---

### Post by pbw on 2007-06-07
yeah, i'd say try doing what i suggested first, then reinstall *buntu-desktop and see if it fixes things.

---

### Post by AllanP on 2007-06-07
Tried wget:
 sudo wget install apt
Password:
--19:27:33--  [http://install/](http://install/)
           => `index.html'
Resolving install... failed: Name or service not known.
--19:27:33--  [http://apt/](http://apt/)
           => `index.html'
Resolving apt... failed: Name or service not known.

FINISHED --19:27:33--
Downloaded: 0 bytes in 0 files

Did I not do it right

and how do I apply dpkg?

---

### Post by pbw on 2007-06-07
wget [http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.6.46.4ubuntu10_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.6.46.4ubuntu10_i386.deb)

sudo dpkg -i apt_0.6.46.4ubuntu10_i386.deb

---

### Post by AllanP on 2007-06-07
> **pbw said:**
> wget [http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.6.46.4ubuntu10_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.6.46.4ubuntu10_i386.deb)

sudo dpkg -i apt_0.6.46.4ubuntu10_i386.deb


sudo wget [http://mirrors.kernel.org/ubuntu/poo...ntu10_i386.deb](http://mirrors.kernel.org/ubuntu/poo...ntu10_i386.deb)
Password:
--19:42:40--  [http://mirrors.kernel.org/ubuntu/poo...ntu10_i386.deb](http://mirrors.kernel.org/ubuntu/poo...ntu10_i386.deb)
           => `poo...ntu10_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:42:40 ERROR 404: Not Found.

---

### Post by pbw on 2007-06-07
[http://mirror.clarkson.edu/pub/distributions/ubuntu/pool/main/a/apt/apt_0.6.46.4ubuntu10_i386.deb](http://mirror.clarkson.edu/pub/distributions/ubuntu/pool/main/a/apt/apt_0.6.46.4ubuntu10_i386.deb)

wget that url. mirror was bad. I just assumed any on the list were fine. I checked this one before posting it.

---

### Post by AllanP on 2007-06-07
Thanks for all your help but, I got the same response "404" from that one. Feeling a little guilty taking up your time here.

---

### Post by AllanP on 2007-06-07
I've been chatting with another on Fedora and got this response to my problem. I'll try this:

His response

The real problem is in /etc/fstab where the UUID numbers don't match what's expected due to the modification. What I did was go into /etc/fstab and remove the associated UUID and change /media/hdxx to /dev/hdxx The rest of the fstab should be okay. For instance, here's my current /etc/fstab:

Quote:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdb1
UUID=612b7d8f-402b-47c5-a6fc-182e58172a68 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1
/dev/hda1 ext3 defaults 0 2
# /dev/hda3
UUID=3871c963-c69b-4127-a67e-2e403478e1b6 /media/hda3 ext3 defaults 0 2
# /dev/hda4
UUID=cdb4fd6c-9bb9-438b-8482-b4514ef44891 /media/hda4 ext3 defaults 0 2
# /dev/hdb2
/dev/hdb2 ext3 defaults 0 2
# /dev/hdb3
UUID=d7072ff4-8dd9-4d94-8320-ae0b34c86a3f /media/hdb3 ext3 defaults 0 2
# /dev/hdb5
UUID=261550cd-1a45-4e07-bae3-450a314e5fc1 /media/hdb5 ext3 defaults 0 2
# /dev/hda5
UUID=d3fbf8b1-17e9-4629-b84a-07a291865fc0 none swap sw 0 0
# /dev/hdb6
UUID=048e8b46-80c2-4336-9d19-107b9af288de none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

---

### Post by pbw on 2007-06-07
yeah, i forgot about uuid crap. 

Just enter blkid in terminal to find out. Then edit fstab.

---

### Post by AllanP on 2007-06-08
> **pbw said:**
> yeah, i forgot about uuid crap. 

Just enter blkid in terminal to find out. Then edit fstab.

Yowsa!!!! Thanks a lot. That was the solution. Boy I gotta make some notes on that one. You're a whiz thanks again wow.

Regards, Allan

---

