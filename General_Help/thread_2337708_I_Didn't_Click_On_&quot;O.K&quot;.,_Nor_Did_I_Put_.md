---
title: "I Didn't Click On &quot;O.K&quot;., Nor Did I Put In My Password. So, Why Did It Update?"
date: 2016-09-20
forum: General Help
---

### Post by DeadlyOats on 2016-09-20
Like the title says.  Kubuntu 16.04.1 updated on its own, without me clicking on any dialogue boxes, nor typing my password in.  Should I be worried?  It's asking me to do a System Restart...

---

### Post by RobGoss on 2016-09-20
When you say Ubuntu updated on it's own what exactly do you mean?

---

### Post by DeadlyOats on 2016-09-20
I mean that I was not given any notice that updates were available.  Usually, I'm told that updates are available. I'm usually given the option to download the updates, but then I'm prompted to enter my password.  None of that happened.  It skipped all of that, and simply told me that I needed to restart Kubuntu for the new updates to take effect.

---

### Post by &amp;KyT$0P# on 2016-09-20
Check /var/log/apt/history.log, anything in there not triggered by you?

---

### Post by DeadlyOats on 2016-09-20
Here's what I got:
> myusername@Computer'sName:~$ /var/log/apt/history.log
bash: /var/log/apt/history.log: Permission denied
myusername@Computer'sName:~$ 


---

### Post by uRock on 2016-09-20
Try ```
cat /var/log/apt/history.log
``` to see what is in the log file.

I have a Netbook running ubuntu 16.04 on it. It normally automatically installs updates on its own. The only ones it usually doesn't update are the kernels. I believe it skips them as they are new installs versus package updates.

---

### Post by DeadlyOats on 2016-09-20
Here's what I got:
> myusername@Computer'sName:~$ /var/log/apt/history.log
bash: /var/log/apt/history.log: Permission denied
myusername@Computer'sName:~$ 


---

### Post by QIII on 2016-09-20
You didn't put "cat" in front of that.

```
cat /var/log/apt/history.log
```

---

### Post by cariboo on 2016-09-21
You didn't mention what version you are using, but as of 16.04 Ubuntu and derivatives automatically update already installed packages without user intervention,

---

### Post by QIII on 2016-09-21
That is the default.  It can be changed, of course.

Another case, IMO, where something should have been opt-in rather than opt-out.  But oh well...

---

### Post by &amp;KyT$0P# on 2016-09-21
> **cariboo said:**
> You didn't mention what version you are using, but as of 16.04 Ubuntu and derivatives automatically update already installed packages without user intervention,

> **DeadlyOats said:**
> Kubuntu 16.04.1 updated on its own, 

I'd say cariboo likely nailed it :)

Just uninstall unattended-upgrades.  I did on my 16.04 system and haven't seen any resulting issues.

---

### Post by DeadlyOats on 2016-09-21
I did the

> cat /var/log/apt/history.log

This is what I got:

```

Start-Date: 2016-09-05  15:19:58
Install: handbrake:amd64 (0.10.2+ds1-2build1)
End-Date: 2016-09-05  15:20:01

Start-Date: 2016-09-05  15:47:45
Commandline: apt-get install libdvd-pkg
Requested-By: deadlyoats (1000)
Install: libltdl-dev:amd64 (2.4.6-0.1, automatic), autotools-dev:amd64 (20150820.1, automatic), libmail-sendmail-perl:amd64 (0.79.16-1, automatic), m4:amd64 (1.4.17-5, automatic), libfakeroot:amd64 (1.20.2-1ubuntu1, automatic), libalgorithm-diff-perl:amd64 (1.19.03-1, automatic), libalgorithm-merge-perl:amd64 (0.08-3, automatic), dh-autoreconf:amd64 (11, automatic), g++:amd64 (4:5.3.1-1ubuntu1, automatic), automake:amd64 (1:1.15-4ubuntu1, automatic), dh-strip-nondeterminism:amd64 (0.015-1, automatic), build-essential:amd64 (12.1ubuntu2, automatic), libfile-stripnondeterminism-perl:amd64 (0.015-1, automatic), po-debconf:amd64 (1.0.19, automatic), libdvd-pkg:amd64 (1.4.0-1-1), autoconf:amd64 (2.69-9, automatic), libstdc++-5-dev:amd64 (5.4.0-6ubuntu1~16.04.2, automatic), g++-5:amd64 (5.4.0-6ubuntu1~16.04.2, automatic), fakeroot:amd64 (1.20.2-1ubuntu1, automatic), debhelper:amd64 (9.20160115ubuntu3, automatic), autopoint:amd64 (0.19.7-2ubuntu3, automatic), libalgorithm-diff-xs-perl:amd64 (0.04-4build1, automatic), libsys-hostname-long-perl:amd64 (1.5-1, automatic), libtool:amd64 (2.4.6-0.1, automatic), dpkg-dev:amd64 (1.18.4ubuntu1.1, automatic), libsigsegv2:amd64 (2.10-4, automatic)
End-Date: 2016-09-05  15:48:42

Start-Date: 2016-09-05  20:39:59
Commandline: apt-get install vlc libaacs0 libbluray-bdj libbluray1
Requested-By: deadlyoats (1000)
Install: libasm4-java:amd64 (5.0.4-1, automatic), libbluray-bdj:amd64 (1:0.9.2-2)
End-Date: 2016-09-05  20:40:02

Start-Date: 2016-09-07  02:41:24
Commandline: /usr/bin/unattended-upgrade
Upgrade: chromium-codecs-ffmpeg-extra:amd64 (51.0.2704.79-0ubuntu0.16.04.1.1242, 52.0.2743.116-0ubuntu0.16.04.1.1250)
End-Date: 2016-09-07  02:41:26

Start-Date: 2016-09-08  06:34:46
Upgrade: libgles2-mesa:amd64 (11.2.0-1ubuntu2.1, 11.2.0-1ubuntu2.2), libgles1-mesa:amd64 (11.2.0-1ubuntu2.1, 11.2.0-1ubuntu2.2), libglapi-mesa:amd64 (11.2.0-1ubuntu2.1, 11.2.0-1ubuntu2.2), snapd:amd64 (2.13, 2.14.2~16.04), libxatracker2:amd64 (11.2.0-1ubuntu2.1, 11.2.0-1ubuntu2.2), libegl1-mesa:amd64 (11.2.0-1ubuntu2.1, 11.2.0-1ubuntu2.2), libgbm1:amd64 (11.2.0-1ubuntu2.1, 11.2.0-1ubuntu2.2), libwayland-egl1-mesa:amd64 (11.2.0-1ubuntu2.1, 11.2.0-1ubuntu2.2), libgl1-mesa-dri:amd64 (11.2.0-1ubuntu2.1, 11.2.0-1ubuntu2.2), libgl1-mesa-glx:amd64 (11.2.0-1ubuntu2.1, 11.2.0-1ubuntu2.2), libp11-kit0:amd64 (0.23.2-3, 0.23.2-5~ubuntu16.04.1), mesa-vdpau-drivers:amd64 (11.2.0-1ubuntu2.1, 11.2.0-1ubuntu2.2)
End-Date: 2016-09-08  06:35:13

Start-Date: 2016-09-09  23:15:12
Upgrade: libappstream-glib8:amd64 (0.5.13-1ubuntu2, 0.5.13-1ubuntu3), accountsservice:amd64 (0.6.40-2ubuntu11.1, 0.6.40-2ubuntu11.2), libaccountsservice0:amd64 (0.6.40-2ubuntu11.1, 0.6.40-2ubuntu11.2)
End-Date: 2016-09-09  23:15:20

Start-Date: 2016-09-14  08:41:14
Commandline: /usr/bin/unattended-upgrade
Upgrade: flashplugin-installer:amd64 (11.2.202.632ubuntu0.16.04.1, 11.2.202.635ubuntu0.16.04.1), mysql-client-core-5.7:amd64 (5.7.13-0ubuntu0.16.04.2, 5.7.15-0ubuntu0.16.04.1), oxideqt-codecs-extra:amd64 (1.16.5-0ubuntu0.16.04.1, 1.17.7-0ubuntu0.16.04.1), mysql-common:amd64 (5.7.13-0ubuntu0.16.04.2, 5.7.15-0ubuntu0.16.04.1), libmysqlclient20:amd64 (5.7.13-0ubuntu0.16.04.2, 5.7.15-0ubuntu0.16.04.1), mysql-server-core-5.7:amd64 (5.7.13-0ubuntu0.16.04.2, 5.7.15-0ubuntu0.16.04.1)
End-Date: 2016-09-14  08:41:45

Start-Date: 2016-09-15  06:06:05
Upgrade: libsystemd0:amd64 (229-4ubuntu7, 229-4ubuntu8), udev:amd64 (229-4ubuntu7, 229-4ubuntu8), libudev1:amd64 (229-4ubuntu7, 229-4ubuntu8), systemd-sysv:amd64 (229-4ubuntu7, 229-4ubuntu8), libpam-systemd:amd64 (229-4ubuntu7, 229-4ubuntu8), systemd:amd64 (229-4ubuntu7, 229-4ubuntu8)
End-Date: 2016-09-15  06:06:47

Start-Date: 2016-09-20  16:47:34
Commandline: /usr/bin/unattended-upgrade
Install: linux-image-4.4.0-38-generic:amd64 (4.4.0-38.57, automatic), linux-image-extra-4.4.0-38-generic:amd64 (4.4.0-38.57, automatic), linux-headers-4.4.0-38-generic:amd64 (4.4.0-38.57, automatic), linux-headers-4.4.0-38:amd64 (4.4.0-38.57, automatic)
Upgrade: libservlet3.1-java:amd64 (8.0.32-1ubuntu1.1, 8.0.32-1ubuntu1.2), linux-headers-generic:amd64 (4.4.0.36.38, 4.4.0.38.40), linux-libc-dev:amd64 (4.4.0-36.55, 4.4.0-38.57), linux-image-generic:amd64 (4.4.0.36.38, 4.4.0.38.40), linux-generic:amd64 (4.4.0.36.38, 4.4.0.38.40)
End-Date: 2016-09-20  16:50:12

```

Actually, there was a ton more, but it was way too long.  I think I couldn't post it because of its length.  So, I just posted the bottom half of it.

---

### Post by howefield on 2016-09-21
> **DeadlyOats said:**
> 

```
Start-Date: 2016-09-20  16:47:34
Commandline: /usr/bin/unattended-upgrade
Install: linux-image-4.4.0-38-generic:amd64 (4.4.0-38.57, automatic), linux-image-extra-4.4.0-38-generic:amd64 (4.4.0-38.57, automatic), linux-headers-4.4.0-38-generic:amd64 (4.4.0-38.57, automatic), linux-headers-4.4.0-38:amd64 (4.4.0-38.57, automatic)
Upgrade: libservlet3.1-java:amd64 (8.0.32-1ubuntu1.1, 8.0.32-1ubuntu1.2), linux-headers-generic:amd64 (4.4.0.36.38, 4.4.0.38.40), linux-libc-dev:amd64 (4.4.0-36.55, 4.4.0-38.57), linux-image-generic:amd64 (4.4.0.36.38, 4.4.0.38.40), linux-generic:amd64 (4.4.0.36.38, 4.4.0.38.40)
End-Date: 2016-09-20  16:50:12
```

Prize for cariboo...

Kernel update in the last unattended upgrade would have prompted the restart message.

So, no, nothing to worry about unless you don't wish unattended upgrade to take place. Thanks for the thread, I'd missed that 16.04 nugget.

---

### Post by DeadlyOats on 2016-09-21
Thanks!  That's a big load off of my mind!  I must have forgot to do the restart, the last time I did the update.  Thanks again your your help!

---

