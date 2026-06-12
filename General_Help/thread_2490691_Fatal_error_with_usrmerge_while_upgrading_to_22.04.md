---
title: "Fatal error with usrmerge while upgrading to 22.04: duplicated locations of libssl an"
date: 2023-09-12
forum: General Help
---

### Post by varikvi on 2023-09-12
I am finding what it seems a common issue when upgrading Ubuntu versions - a `usrmerge` fatal error which also prevents the correct symlink assignments. 


An indication that there was something wrong with the `usrmerge` appeared during the Ubuntu version upgrade from 20.04 to 22.04. The Ubuntu upgrade did happen:


    ```
ec@ec:~$ lsb_release -a
    No LSB modules are available.
    Distributor ID:    Ubuntu
    Description:    Ubuntu 22.04.3 LTS
    Release:    22.04
    Codename:    jammy
``` 


but a warning message said that the upgrade was actually incomplete and error-prone, asking me to solve the issue so the upgrade could be fully completed.


I found that the `usrmerge` was giving problems to everyone.


The most common solution online was to try to updgrade `usrmerge`. This is an example on what people normally do:


[https://bugs.launchpad.net/ubuntu/+source/usrmerge/+bug/1993943/comments/5](https://bugs.launchpad.net/ubuntu/+source/usrmerge/+bug/1993943/comments/5)


However, when I try `sudo apt install usrmerge` or similar actions on`usrmerge`, it always throws a fatal error when finding a first discrepancy:


    ```
FATAL ERROR:
**Both /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 and /usr/lib/x86_64-linux-gnu/libcrypto.so.1.0.0 exist**.
    
    You can try correcting the errors reported and running again
    /usr/lib/usrmerge/convert-usrmerge until it will complete without errors.
    Do not install or update other Debian packages until the program
    has been run successfully.
    
    dpkg: error processing package usrmerge (--configure):
     installed usrmerge package post-installation script subprocess returned error exit status 1
    Errors were encountered while processing:
     usrmerge
    E: Sub-process /usr/bin/dpkg returned an error code (1)
```


The error above suggests that the duplicated files are in these two directories:
* /usr/lib/x86_64-linux-gnu/
* /lib/x86_64-linux-gnu/


Then I found out that the same failing directory pattern is associated to two files:
`libcrypto.so.1.0.0` and `libssl.so.1.0.0` files.


The ones in `/usr/lib/x86_64-linux-gnu/` are originals, while the `lib*.so.1.0.0`'s in `/lib/x86_64-linux-gnu/` are symlinks of other symlinks:


    lrwxrwxrwx 1 root root      11 apr 26  2019 libssl.so.1.0.0 -> libssl.so.6
    lrwxrwxrwx 1 root root      42 apr 24  2019 libssl.so.6 -> /usr/local/ampps/extra/lib/libssl.so.1.0.0


The `lib*.so.6` are then pointing to duplicated `lib*.so.1.0.0` in a different directory which seems to be related to ampps (MySQL dependencies?).


I have found many examples of `usrmerge` failure with incorrect links and locations but none similar to my problem. What seems to be relevant to all of them is this explanation: [https://askubuntu.com/a/1441239/1728935](https://askubuntu.com/a/1441239/1728935)


So, it appears that I should use only one original of the `lib*.so.1.0.0` to be used as source of the symlink in the `lib` sub-directory, but there are other symlinks, the `lib*.so.6`, sitting right in between that I don´t know how to solve :L. If someone can explain me the safest way to correct this apparent discrepancy so I don't end breaking something else (*Disclaimer*: I am not linux-expert)?

---

### Post by cipri.tom on 2023-09-21
I am seeing the same error. And, like you say, since this is something running in background of `do-release-upgrade`, it is out of our control. Wishing someone has a hint

---

### Post by #&amp;thj^% on 2023-09-21
> **varikvi said:**
> 
So, it appears that I should use only one original of the `lib*.so.1.0.0` to be used as source of the symlink in the `lib` sub-directory, but there are other symlinks, the `lib*.so.6`, sitting right in between that I don´t know how to solve :L. If someone can explain me the safest way to correct this apparent discrepancy so I don't end breaking something else (*Disclaimer*: I am not linux-expert)?

I'm not sure I can help but will you show this please:
```
cd /usr/lib/ && ls | grep linux.so.2

```
EDIT: Never Mind This Post is over a Week Old
@cipri.tom open a new thread with your topic.

---

### Post by MAFoElffen on 2023-09-21
Stop. (Both the OP and the second person...) At least in your understanding of /lib & /usr/lib.
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls -lah /lib
lrwxrwxrwx 1 root root 7 Sep 23  2021 /lib -> usr/lib

```
/lib is a symbolic link to /usr/lib. There are no duplicates there...

---

### Post by #&amp;thj^% on 2023-09-22
> **MAFoElffen said:**
> Stop.
/lib is a symbolic link to /usr/lib. There are no duplicates there...
+1
```
 cd /usr/lib/ && ls | grep .so 
console-setup
klibc-qrjdleQmVUSXMeCB-fuBoSLiQ0A.so
ld-linux.so.2
libfreecell-solver.so.0
libfreecell-solver.so.0.6.0
libhardsid-builder.so.0
libhardsid-builder.so.0.0.1
libnvidia-gtk2.so.510.47.03
libnvidia-gtk3.so.510.47.03
libresid-builder.so.0
libresid-builder.so.0.0.1
libsidplay2.so.1
libsidplay2.so.1.0.1
linux-sound-base

```

---

### Post by varikvi on 2023-09-25
Thanks @1fallen and @MaFoElffen for responding to my thread. Sorry for my lack of knowledge (I already said I was not linux savvy). I can change the title of the thread if that helps.

However my problem persists. Can any of you help me to interpret how this error is preventing the full deployment of ubuntu 22.04 and how to deal with it? Here a fragment of my original error message, as in the first post.

FATAL ERROR:
**Both /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 and /usr/lib/x86_64-linux-gnu/libcrypto.so.1.0.0 exist**.

---

### Post by #&amp;thj^% on 2023-09-25
First show us this:
```
ls -lah /lib
lrwxrwxrwx 1 root root 7 Sep 21 06:47 /lib -> usr/lib

```
Next we need to see:
```
cd /usr/lib/ && ls | grep .so 

```
And this is very important to see:
```
sudo apt upgrade
```
Please wrap all those returns one at a time but in Code tags, see my signature to use Code Tags.
I'll be away for a few hours today.

---

### Post by varikvi on 2023-10-02
@1fallen

Sorry for my late reply. Busy at work. Here my answers. Is there something that you can spot from the list below?

```

ls -lah /lib
total 136K
drwxr-xr-x 14 root root 4,0K aug 31 12:49 .
drwxr-xr-x 26 root root 4,0K okt 21  2020 ..
lrwxrwxrwx  1 root root   17 aug 31 12:49 apparmor -> /usr/lib/apparmor
lrwxrwxrwx  1 root root   15 aug 31 12:49 brltty -> /usr/lib/brltty
drwxr-xr-x  2 root root 4,0K aug 31 12:34 console-setup
lrwxrwxrwx  1 root root   21 jan  5  2015 cpp -> /etc/alternatives/cpp
lrwxrwxrwx  1 root root   13 aug 31 12:49 crda -> /usr/lib/crda
drwxr-xr-x 93 root root  56K aug 31 12:44 firmware
lrwxrwxrwx  1 root root   15 aug 31 12:49 hdparm -> /usr/lib/hdparm
drwxr-xr-x  2 root root 4,0K aug 31 12:44 i386-linux-gnu
drwxr-xr-x  2 root root 4,0K aug 31 12:33 ifupdown
lrwxrwxrwx  1 root root   13 aug 31 12:49 init -> /usr/lib/init
lrwxrwxrwx  1 root root   45 aug 31 12:49 klibc-K8e6DOmVI9JpyGMLR7qNe5iZeBk.so -> /usr/lib/klibc-K8e6DOmVI9JpyGMLR7qNe5iZeBk.so
lrwxrwxrwx  1 root root   28 jul  7  2022 ld-linux.so.2 -> i386-linux-gnu/ld-linux.so.2
lrwxrwxrwx  1 root root   22 aug 31 12:49 libgcc_s.so.1 -> /usr/lib/libgcc_s.so.1
drwxr-xr-x  2 root root 4,0K aug 31 12:42 linux-sound-base
lrwxrwxrwx  1 root root   12 aug 31 12:49 lsb -> /usr/lib/lsb
drwxr-xr-x  2 root root 4,0K aug 31 14:33 modprobe.d
drwxr-xr-x 57 root root 4,0K aug 31 12:44 modules
drwxr-xr-x  2 root root 4,0K aug 31 12:36 netplan
lrwxrwxrwx  1 root root   17 aug 31 12:49 plymouth -> /usr/lib/plymouth
lrwxrwxrwx  1 root root   22 aug 31 12:49 recovery-mode -> /usr/lib/recovery-mode
lrwxrwxrwx  1 root root   19 aug 31 12:49 resolvconf -> /usr/lib/resolvconf
drwxr-xr-x  3 root root  12K aug 31 12:49 systemd
lrwxrwxrwx  1 root root   17 aug 31 12:49 terminfo -> /usr/lib/terminfo
drwxr-xr-x  2 root root 4,0K aug 31 12:59 udev
drwxr-xr-x  2 root root 4,0K aug 31 12:41 ufw
drwxr-xr-x  3 root root  20K aug 31 12:49 x86_64-linux-gnu

```



```

cd /usr/lib/ && ls | grep .so
klibc-K8e6DOmVI9JpyGMLR7qNe5iZeBk.so
libBLT.2.5.so.8.6
libBLTlite.2.5.so.8.6
libcamel-1.2.so.49
libcamel-1.2.so.49.0.0
libcodeblocks.so.0
libcodeblocks.so.0.0.1
libebackend-1.2.so.7
libebackend-1.2.so.7.0.0
libebook-1.2.so.14
libebook-1.2.so.14.3.1
libebook-contacts-1.2.so.0
libebook-contacts-1.2.so.0.0.0
libecal-1.2.so.16
libecal-1.2.so.16.0.0
libedata-book-1.2.so.20
libedata-book-1.2.so.20.0.0
libedata-cal-1.2.so.23
libedata-cal-1.2.so.23.0.0
libedataserver-1.2.so.18
libedataserver-1.2.so.18.0.0
libgcc_s.so.1
libgdata.so.19
libgdata.so.19.2.1
libgnome-bluetooth.so.11
libgnome-bluetooth.so.11.0.0
libinproctrace.so
libmfp.so
libmfp.so.1
libmfp.so.1.0.1
libnetpbm.so.10
libnetpbm.so.10.0
libpanel-applet.so.3
libpanel-applet.so.3.0.0
librhythmbox-core.so.8
librhythmbox-core.so.8.0.0
libR.so
libtiff.so
libtiff.so.3
libtiff.so.3.6.1
libwps-0.3.so.3
libwps-0.3.so.3.0.0
lp_solve
resolvconf

```

```

sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  python2.7-minimal libimage-magick-perl imagemagick libjs-jquery-ui
  libopenexr25 libmagick++-6.q16-8 python3-scipy libpostproc55
  libmagickcore-6.q16-6-extra libavcodec58 libimage-magick-q16-perl
  libmagickwand-6.q16-6 libpython2.7 libavutil56 imagemagick-6.q16 libswscale5
  libmagickcore-6.q16-6 libswresample3 imagemagick-6-common libavformat58
  python2.7 libpython2.7-minimal libpython2.7-stdlib libavfilter7
Learn more about Ubuntu Pro at https://ubuntu.com/pro
The following packages have been kept back:
  gcc-10-base
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up usrmerge (25ubuntu2) ...
Smartmatch is experimental at /usr/lib/usrmerge/convert-usrmerge line 172.


FATAL ERROR:
Both /lib/x86_64-linux-gnu/libc.so.6 and /usr/lib/x86_64-linux-gnu/libc.so.6 exist.


You can try correcting the errors reported and running again
/usr/lib/usrmerge/convert-usrmerge until it will complete without errors.
Do not install or update other Debian packages until the program
has been run successfully.


dpkg: error processing package usrmerge (--configure):
 installed usrmerge package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 usrmerge
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

