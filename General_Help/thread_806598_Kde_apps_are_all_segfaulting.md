---
title: "Kde apps are all segfaulting"
date: 2008-05-25
forum: General Help
---

### Post by SneakyWho_am_i on 2008-05-25
Doesn't matter whether or not I'm root.

```
sneaky@ubuntu:~$ kdeinit
Segmentation fault
sneaky@ubuntu:~$ amarokapp
Segmentation fault
sneaky@ubuntu:~$ dcopserver
sneaky@ubuntu:~$ konqueror
Segmentation fault
sneaky@ubuntu:~$ konsole
Segmentation fault
sneaky@ubuntu:~$ pidgin
Segmentation fault
```

Pidgin actually started (festival crashed), the others didn't.
apt-get was saying **Segmentation Faulty Tree 0%** until I cleared something from /var/cache/apt/ (*.bin, I think)

```
sneaky@ubuntu:~$ cat /var/log/syslog|grep seg
May 25 08:40:28 ubuntu kernel: [1266179.566622] flipscreen3d[23226]: segfault at 00000000 eip b7b7cc37 esp bff82b34 error 4
May 25 10:04:25 ubuntu kernel: [1271210.157892] update-manager[31354]: segfault at 23b0f908 eip b7e88283 esp bfca592c error 4
May 25 10:04:26 ubuntu kernel: [1271210.586348] apt-check[31565]: segfault at 29297908 eip b7e00283 esp bfd6967c error 4
May 25 13:17:26 ubuntu kernel: [1282774.795043] mysql-admin[18471]: segfault at 00000000 eip 080f783d esp bf81d0e0 error 4
May 25 18:45:55 ubuntu kernel: [1302455.709748] apt-cache[18887]: segfault at 7639c008 eip b7f02205 esp bfd5a74c error 4
May 25 18:46:12 ubuntu kernel: [1302473.439112] apt-cache[18918]: segfault at 76333008 eip b7e99205 esp bfab248c error 4
May 25 18:49:16 ubuntu kernel: [1302656.816655] konsole[19215]: segfault at b8403b42 eip b7f0e7e1 esp bfa510ac error 4
May 25 18:50:13 ubuntu kernel: [1302713.395236] konsole[19293]: segfault at b83e7b42 eip b7ef27e1 esp bfc582bc error 4
May 25 18:50:24 ubuntu kernel: [1302724.440901] update-manager[19307]: segfault at 73277008 eip b6c9bcc3 esp bfe8f570 error 4
May 25 18:50:24 ubuntu kernel: [1302724.537894] update-manager[19310]: segfault at 731ac008 eip b6bf2cc3 esp bfd9c1d0 error 4
May 25 18:50:27 ubuntu kernel: [1302727.915237] update-manager[19331]: segfault at 7318f008 eip b6bd5cc3 esp bf916550 error 4
May 25 18:50:30 ubuntu kernel: [1302730.363706] update-manager[19334]: segfault at 73216008 eip b6c5ccc3 esp bf9ede20 error 4
May 25 18:51:01 ubuntu kernel: [1302762.013187] update-manager[19371]: segfault at 7320e008 eip b6c54cc3 esp bfa45e80 error 4
May 25 18:52:12 ubuntu kernel: [1302832.803652] klauncher[13655]: segfault at 00000095 eip b7408ee7 esp bff1bc10 error 4
May 25 18:52:18 ubuntu kernel: [1302839.040181] gdm[5749]: segfault at 7672657f eip b78007e2 esp bfe647c0 error 6
May 25 19:14:30 ubuntu kernel: [1304168.342637] apt-get[19783]: segfault at 76fb3000 eip b7ee6cc3 esp bffd0780 error 4
May 25 19:14:42 ubuntu kernel: [1304180.392031] apt-get[19784]: segfault at 76fc6000 eip b7ef9cc3 esp bfb3bae0 error 4
May 25 19:15:32 ubuntu kernel: [1304230.350679] apt-get[19790]: segfault at 76fce000 eip b7f01cc3 esp bff366e0 error 4
May 25 19:16:31 ubuntu kernel: [1304289.262020] apt-get[19804]: segfault at 76f29000 eip b7e5ccc3 esp bfc0b350 error 4
May 25 19:42:21 ubuntu kernel: [   81.855318] apache2[6475]: segfault at 00000000 eip b7ebc970 esp bfd5945c error 6
May 25 19:41:07 ubuntu kernel: [  104.197822] kdeinit[6759]: segfault at bbdb80f8 eip b7fcc824 esp bf95efac error 4
May 25 19:41:29 ubuntu kernel: [  126.358072] konsole[6795]: segfault at b8418b42 eip b7f237e1 esp bfb961ac error 4
May 25 19:41:31 ubuntu kernel: [  127.859945] konsole[6805]: segfault at b83f5b42 eip b7f007e1 esp bff6457c error 4
May 25 19:42:22 ubuntu kernel: [  178.987019] konsole[6882]: segfault at b84cbb42 eip b7fd67e1 esp bfb911ec error 4
May 25 19:42:32 ubuntu kernel: [  188.562394] apt-check[6916]: segfault at 76f61000 eip b7c3acc3 esp bfa08ef0 error 4
May 25 19:43:46 ubuntu kernel: [  262.515818] konsole[6985]: segfault at b8481b42 eip b7f8c7e1 esp bfa7e3dc error 4
May 25 19:44:00 ubuntu kernel: [  277.182054] update-manager[6987]: segfault at 73e72000 eip b6c5bcc3 esp bf8be4f0 error 4
May 25 19:47:06 ubuntu kernel: [  462.253862] apt-get[6997]: segfault at 76fd0000 eip b7f03cc3 esp bfee4dc0 error 4
May 25 20:23:16 ubuntu kernel: [ 2629.440441] apt-get[7107]: segfault at 76f3f000 eip b7e72cc3 esp bfb72300 error 4
May 25 20:28:30 ubuntu kernel: [ 2942.541449] konsole[7175]: segfault at b8420b42 eip b7f2b7e1 esp bfcdc63c error 4
May 25 20:29:26 ubuntu kernel: [ 2998.820195] konsole[7179]: segfault at b84c4b42 eip b7fcf7e1 esp bfed302c error 4
May 25 20:29:47 ubuntu kernel: [ 3019.767910] konsole[7183]: segfault at b84a1b42 eip b7fac7e1 esp bfabbc1c error 4
May 25 20:30:41 ubuntu kernel: [ 3073.640816] konqueror[7194]: segfault at b7f69b42 eip b7f197e1 esp bf848c7c error 4
May 25 20:30:47 ubuntu kernel: [ 3079.779381] kdesu[7195]: segfault at b819bb42 eip b7f5d7e1 esp bfc77b9c error 4
May 25 20:38:14 ubuntu kernel: [ 3526.008602] kdeinit[7342]: segfault at bbcfa0f8 eip b7f0e824 esp bfe263bc error 4
May 25 20:39:19 ubuntu kernel: [ 3590.594204] amarokapp[7355]: segfault at bc5430f8 eip b7f66824 esp bf93ca0c error 4
May 25 20:39:30 ubuntu kernel: [ 3602.352591] konqueror[7361]: segfault at b7f71b42 eip b7f217e1 esp bfa9bbec error 4
May 25 20:39:32 ubuntu kernel: [ 3604.012993] konsole[7362]: segfault at b8488b42 eip b7f937e1 esp bf81216c error 4
May 25 20:40:12 ubuntu kernel: [ 3644.421272] festival[7375]: segfault at 00000023 eip b78f0857 esp bfaa1470 error 4
May 25 20:45:21 ubuntu kernel: [ 3952.066115] kdesu[7507]: segfault at b8220b42 eip b7fe27e1 esp bfdb071c error 4
```

> sneaky@ubuntu:~$ uname -a
Linux ubuntu 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

Any ideas would be great. I think it's the kernel but I'm loathe to restart because then I would feel compelled to fsck.

EDIT:
Doesn't matter which window manager I use, or which kernel. Tried everything back to 2.6.24.17 (besides, this problem started in the middle of a session and I have to reboot to change kernels at this time)
Also it's not all just kde apps, even apache2 won't start.
apache2 exits with "error 6" in syslog, not "error 4"

---

### Post by SneakyWho_am_i on 2008-05-25
OK so I'm dealing with two different things. Here's apache2 going nuts.
```
[New Thread 0xb77f0700 (LWP 9597)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb77f0700 (LWP 9597)]
0xb7f4e970 in apr_proc_mutex_unix_setup_lock ()
   from /usr/lib/libapr-1.so.0
(gdb) bt
#0  0xb7f4e970 in apr_proc_mutex_unix_setup_lock ()
   from /usr/lib/libapr-1.so.0
#1  0xb7f51a15 in apr_initialize ()
   from /usr/lib/libapr-1.so.0
#2  0xb7f51aa7 in apr_app_initialize ()
   from /usr/lib/libapr-1.so.0
#3  0x08066556 in main ()
```

But that's a different problem to all the other applications (including kdesu) so let's ignore apache2 for now.

All of the other programs which crash are crashing after two consecutive calls in ld-linux.so.2:
> Starting program: /usr/bin/amarokapp
(no debugging symbols found)
(no debugging symbols found)

Program received signal SIGSEGV, Segmentation fault.
0xb7f4d824 in ?? () from /lib/ld-linux.so.2
(gdb) bt
#0  0xb7f4d824 in ?? () from /lib/ld-linux.so.2
#1  0xb7f21ed8 in ?? ()
#2  0x00000000 in ?? ()

and

> Starting program: /usr/bin/konsole
(no debugging symbols found)
(no debugging symbols found)

Program received signal SIGSEGV, Segmentation fault.
0xb7f4e7e1 in ?? () from /lib/ld-linux.so.2
(gdb) bt
#0  0xb7f4e7e1 in ?? () from /lib/ld-linux.so.2
#1  0xb7f22ef8 in ?? ()
#2  0x00000000 in ?? ()
(gdb)

I tried reconfiguring libc6 but to no avail. Will try compiling another copy of amarokapp and maybe some others, so I can squeeze some debugging stuff out of them (can't find -dbg packages in the repo for any of this stuff!!)

Still, I've never written a line of C in my life, and I'm by no means a computer programmer so I'm still keen on some help if anyone has any ideas ;)

EDIT: IIRC KDE uses SVN. Amarok I can't download because it comes through SVN. SVN is crashing exactly the same way as what apache2 is crashing. I am not sure what to do at this point, but at least I still have apt and suchlike to play with.
All my programs were running fine yesterday or the day before, then I found that I couldn't reopen them after I closed them. It's just an intranet server (and workstation, cause I'm cheap) but yeah.
Maybe there's a way to roll back updates in Synaptic (globally, not package by package), and then I might be able to turn up something interesting.
At least firefox, sudo, synaptic, dpkg-reconfigure, apt-cache and apt-get are all working 100% :) :) :)

EDIT2:
```
apt-cache source amarok
```
then
```
cd amarok*
chmod -R 777 .
./configure --prefix=`kde-config --prefix` --enable-debug=full
```

Produced
```
<snip>checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... libraries /usr/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... no
configure: error:
you need to install kdelibs first.

If you did install kdelibs, then the Qt version that is picked up by
this configure is not the same version you used to compile kdelibs.
The Qt Plugin installed by kdelibs is *ONLY* loadable if it is the
_same Qt version_, compiled with the _same compiler_ and the same Qt
configuration settings.


```

But:
```
sneaky@ubuntu:~/amarok-1.4.9.1$ sudo apt-get install kdelibs
Reading package lists... Done
Building dependency tree
Reading state information... Done
kdelibs is already the newest version.
The following packages were automatically installed and are no longer required:
  flex
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

I have no idea what to do at this point, lol.

---

