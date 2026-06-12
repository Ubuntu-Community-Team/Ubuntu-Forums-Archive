---
title: "Can't use 'cd, ./configure, make...' method for install"
date: 2007-08-06
forum: General Help
---

### Post by NonPermissive on 2007-08-06
Note: I'm using VMware to use Ubuntu 7.04 as a guest on Windows XP Home.
This is my terminal session:

---------------------------------------------------------------------------
ubuntu@ubuntu:~$ cd /home/ubuntu/Downloads/pidgin-2.0.0
ubuntu@ubuntu:~/Downloads/pidgin-2.0.0$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
ubuntu@ubuntu:~/Downloads/pidgin-2.0.0$ 

----------------------------------------------------------------------
I've tried this with a few different packages.
Thank you in advance.

---

### Post by Steve1961 on 2007-08-06
Install the build-essential package

---

### Post by jnorthr on 2007-08-06
This may be a permissions issue with the target folder you are trying to create the .object files in, or the folder may be missing.

---

### Post by NonPermissive on 2007-08-06
That seems to have worked. Thanks.
It's still running though, so I'll confirm in a sec.

---

### Post by NonPermissive on 2007-08-06
K, now it says this:  checking for GLIB... no
no
configure: error:

You must have the GLib 2.0 development headers installed to build.

Where do I get that?

---

### Post by Steve1961 on 2007-08-06
sudo apt-get install libglib2.0-dev

---

### Post by NonPermissive on 2007-08-06
Running...

---

### Post by NonPermissive on 2007-08-06
configure: error:

You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you only want to build Finch then specify --disable-gtkui when running configure.

I'm going offline for a while.

---

### Post by Steve1961 on 2007-08-06
see:

[http://www.ubuntugeek.com/howto-install-pidgin-200-on-ubuntu-feisty-with-plugin-pack.html](http://www.ubuntugeek.com/howto-install-pidgin-200-on-ubuntu-feisty-with-plugin-pack.html)

---

### Post by NonPermissive on 2007-08-07
I tried the directions, and got this:
------------------------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ wget [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb)
--21:04:56--  [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb)
           => `pidgin_2.0.0-1_i386.deb'
Resolving download.ubuntu.pl... 87.230.27.156
Connecting to download.ubuntu.pl|87.230.27.156|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:04:57 ERROR 404: Not Found.
--------------------------------------------------------------------------------------------------------

I have the problem I made the topic about for *all* programs I attempt.

---

### Post by Boreras on 2007-08-08
the wget command fails because the link doesn't exist. using a site as [getdeb]("http://getdeb.net") you can find the required deb install packages (pidgin 2.1.0 (appearently not quite stable) is on that site as well, besides, the most stable right now is pidgin 2.0.2, the one you're trying to install is old)

the ./configure fails because, well, exactly as it says. Your missing the development files for the gtk library. install them using
"sudo apt-get install libgtk2.0-dev"

---

