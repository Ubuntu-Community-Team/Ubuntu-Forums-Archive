---
title: "RPM Dependences Failure!!"
date: 2006-09-17
forum: General Help
---

### Post by JD_2020 on 2006-09-17
Hi --

So I've been putzing around with Ubuntu lately. I abandoned configuring my web server manually from the ground up, and went with LAMPP.

So I have a web server configured, secured, and working. My phpMyAdmin works, I can create a database real fine. My perl and PHP pages load fine. Great!

But wait! I have to restore a 2.5 GB sql dump to my server. Can't do it through phpMyAdmin as it is way too big. Can't do it through MySQL directly by typing "mysql" into the terminal because it says Access Denied for root@localhost.

Okay so I write a perl script that will connect to the database using a user and pass I setup via phpMyAdmin (which has all privileges) and will make the queries one by one overnight. 

BUT WAIT! I don't have the right perl modules.

So I go to cpan and try to

```
install DBD::mysql
```

and it failed miserably. 

> Can't exec "mysql_config": No such file or directory at Makefile.PL line 451.

I googled that problem and learned that I needed some RPM package to solve that error. So I download the RPM package, but of course don't have RPM installed.

```
apt-get install rpm
```

It installs RPM for me, very helpful, and I type in:

```
rpm -ivh MySQL-devel-4.1.21-0.glibc23.x86_64.rpm
```

And oh boy, wouldn't you know it - after all that when things looked like they were falling in place, I get the following error messages:

> error: Failed dependencies:
        /bin/sh is needed by MySQL-devel-4.1.21-0.glibc23.x86_64
        libc.so.6()(64bit) is needed by MySQL-devel-4.1.21-0.glibc23.x86_64
        libc.so.6(GLIBC_2.2.5)(64bit) is needed by MySQL-devel-4.1.21-0.glibc23.x86_64
        libcrypt.so.1()(64bit) is needed by MySQL-devel-4.1.21-0.glibc23.x86_64
        libm.so.6()(64bit) is needed by MySQL-devel-4.1.21-0.glibc23.x86_64
        libnsl.so.1()(64bit) is needed by MySQL-devel-4.1.21-0.glibc23.x86_64
        libpthread.so.0()(64bit) is needed by MySQL-devel-4.1.21-0.glibc23.x86_64
        libpthread.so.0(GLIBC_2.2.5)(64bit) is needed by MySQL-devel-4.1.21-0.glibc23.x86_64
        libpthread.so.0(GLIBC_2.3.2)(64bit) is needed by MySQL-devel-4.1.21-0.glibc23.x86_64


I google some of those errors, and one of them I found I could solve by doing something like

```
ln -s /bin/bash /bin/sh
```

But I tried that and got:

> ln: creating symbolic link `/bin/sh' to `/bin/bash': File exists

So next I tried:

```
vi /etc/shells
```

and inside of that file a lot of things listed, including /bin/sh and /bin/bash.

So I have run out of Google resources and turn to the community for help. As of now, I need to learn how to get past all these failed dependencies. THEN I will be able to try to actually install the RPM. After that, I will try to install DBD::mysql once more and that will likely fail again for something else.

One step at a time :). Boy I love linux! (/sarcasm)

-JD

---

### Post by em3raldxiii on 2006-09-17
Outa curiosity, what happens when you do this:

```
sudo aptitude install mySQL-devel-4.1.21-0.glibc23.x86_64
```

And I have been convinced that using "Aptitude" to install as opposed to "apt-get" is better because it handles dependencies better - mostly with when you have to remove something later, but also when you install stuff.  On two occasions, when I used aptitude instead, it installed dependencies that were not with apt-get, so now I use aptitude pretty much exclusively.  This MAY help.

NOTE:  If it asks you to overwrite any of your config files with a new version, I am thinking you should say NO if you want to maintain your existing setup and database and stuff.  Just a thought.

Alternatively, you may be able to use sudo aptitude install xxxxxx (for example libpthread).

Finally, you might also have better luck with synaptic because it's pretty good at handling dependencies too.  I am sure you probably already tried that route, but I just figured I'd mention it just in case.

Good luck!

---

### Post by kuja on 2006-09-17
Hey JD, just an idea, but rather than just installing rpms via the rpm command, it's probably a better idea to convert the rpm files to deb files with alien.

---

### Post by Anduu on 2006-09-18
rpm's are not comatible with Ubuntu.

Converting it to deb with alien should work however you are better of to find a precompiled deb or better yet compile/install it yourself.

---

### Post by JD_2020 on 2006-09-18
sudo aptitude install mySQL-devel-4.1.21-0.glibc23.x86_64

did nothing.

> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "mySQL-devel-4.1.21-0.glibc23.x86_64"
The following packages have been kept back:
  bind9-host dnsutils libbind9-0 libdns21 libisc11 libisccc0 libisccfg1
  liblwres9 libssl0.9.8 libxfont1 linux-image-2.6.15-26-amd64-server
  openssl xorg-driver-fglrx
0 packages upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


I tried upgrading cpan too and it did nothing...

---

