---
title: "[SOLVED] Is there any way to reinstall dpkg?"
date: 2008-01-26
forum: General Help
---

### Post by WildeBeest on 2008-01-26
I can't install any updates or applications.

I get the following error messages every time.

dpkg: can't mmap package info file '/var/lib/dpkg/available': No such device

E: Sub-process /usr/bin/dpkg returned an error code (2)

Do I just have to re-install Ubuntu 7.1?

---

### Post by taurus on 2008-01-26
Let's see if you have a backup, available-old, copy on your machine.

```
ls -la /var/lib/dpkg
```

---

### Post by WildeBeest on 2008-01-26
the output of that command is:

drwxr-xr-x  8 root root    4096 2008-01-23 12:10 .
drwxr-xr-x 49 root root    4096 2007-12-15 10:04 ..
drwxr-xr-x  2 root root    4096 2008-01-20 09:09 alternatives
drwxr-xr-x  2 root root    4096 2008-01-23 12:10 available
-rw-r--r--  1 root root       8 2007-12-12 12:36 cmethopt
-rw-r--r--  1 root root    3038 2007-12-12 20:56 diversions
-rw-r--r--  1 root root    2956 2007-12-12 20:56 diversions-old
drwxr-xr-x  2 root root  229376 2008-01-20 09:08 info
-rw-r-----  1 root root       0 2008-01-26 11:49 lock
drwxr-xr-x  2 root root    4096 2007-09-21 16:21 parts
-rw-r--r--  1 root root      30 2007-12-12 12:48 statoverride
-rw-r--r--  1 root root       0 2007-12-12 12:36 statoverride-old
-rw-r--r--  1 root root 1180451 2008-01-20 09:14 status
-rw-r--r--  1 root root 1180450 2008-01-20 09:14 status-old
drwxr-xr-x  2 root root    4096 2008-01-20 09:09 triggers
drwxr-xr-x  2 root root    4096 2008-01-20 09:09 updates

---

### Post by disturbedite on 2008-01-26
perhaps ```
sudo apt-get install --reinstall dpkg
```?

---

### Post by WildeBeest on 2008-01-26
willy@WES:~$ sudo apt-get install --reinstall dpkg
[sudo] password for willy:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 14 not upgraded.
Need to get 2175kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main dpkg 1.14.5ubuntu16 [2175kB]
Fetched 2175kB in 3s (600kB/s) 
dpkg: can't mmap package info file `/var/lib/dpkg/available': No such device
E: Sub-process /usr/bin/dpkg returned an error code (2)

Same message I get with everything I attempt to install.

---

### Post by doorknob60 on 2008-01-26
You could always try copying dpkg from another computer or the Live CD even.

---

### Post by WildeBeest on 2008-01-26
which folder does dpkg reside?

---

### Post by WildeBeest on 2008-01-27
Doesn't anyone know whats going on?

With all the "experts" here, I must be able to get a timely solution.

---

### Post by WildeBeest on 2008-01-27
I found that the "available" folder is missing. So I created one, still get the same error messages.

I deleted the "available" folder and created an "available" file. All good now.

---

### Post by Rising Sun on 2008-04-09
Hello i am also facing the problem with dpkg

 can u clearly explain  what u have deleted and how u have included answer folder

u kept answer file or folder 

if file what is that how u have generated

Thanks in advance

---

### Post by unutbu on 2008-04-09
If you are getting the following error message:

dpkg: can't mmap package info file `/var/lib/dpkg/available': No such device

then from the messages above, it appears that the solution to the problem is

```
sudo touch /var/lib/dpkg/available
sudo chmod 644 /var/lib/dpkg/available
```

---

### Post by WildeBeest on 2008-04-09
Rising Sun

In my case I had a folder named "available". I deleted it and created an empty file named "available"
That did the trick for me.

---

### Post by Rising Sun on 2008-04-10
Hi thanks for ur king reply

my problem didnt solve yet

actually i am installing rpm packages in ubuntu by using alien

the process is 
[I][I][I]
root@xxxxr:~/Desktop/Project# alien libxml2-2.6.30-1.aix5.2.ppc.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/libxml2
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current build architecture i386 does not appear in package's list (powerpc)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: libxml2-2.6.30: No such file or directory[/FONT][/B]


this is the error message i am getting, how to get rid of this  please reply

Thanks in advance

---

### Post by erginemr on 2008-04-10
It seems from the error message that you are using a PC (i386 architecture), where as the package you are trying to convert to *.deb with alien has been made for a MAC (power-pc architecture). You need to find a package with i386, x86, etc. in its name.

---

