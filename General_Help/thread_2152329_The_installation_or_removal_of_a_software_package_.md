---
title: "The installation or removal of a software package failed"
date: 2013-06-07
forum: General Help
---

### Post by checoimg on 2013-06-07
Hi guys!

I'm trying to update Ubuntu and I get an error : "The installation or removal of a software package failed"

When I try to remove Opera I get the same message. This is Ubuntu 13.04 64bit.

---

### Post by checoimg on 2013-06-07
When I do "sudo apt-get purge opera"
 I get:
"dpkg: warning: 'find' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin
E: Sub-process /usr/bin/dpkg returned an error code (2) "

---

### Post by slickymaster on 2013-06-07
There is probably something messed up with the permissions of find, find is located in **/usr/bin/find.** Check its permissions:```
~$ ls -l /usr/bin/find
```it should return something like this:```
-rwxr-xr-x 1 root root 158364 Out 29  2012 /usr/bin/find
```

---

### Post by checoimg on 2013-06-07
> **slickymaster said:**
> There is probably something messed up with the permissions of find, find is located in **/usr/bin/find.** Check its permissions:```
~$ ls -l /usr/bin/find
```it should return something like this:```
-rwxr-xr-x 1 root root 158364 Out 29  2012 /usr/bin/find
```

ls: cannot access /usr/bin/find: No such file or directory

---

### Post by slickymaster on 2013-06-07
> **checoimg said:**
> ls: cannot access /usr/bin/find: No such file or directory

Can you please post the output of:```
which find
```

---

### Post by checoimg on 2013-06-07
> **slickymaster said:**
> Can you please post the output of:```
which find
```

No output just a New Line

---

### Post by slickymaster on 2013-06-07
> **checoimg said:**
> No output just a New Line

It seems as though you don't have find installed, which is really odd. Please run the following and post the output, please:```
sudo apt-get install --reinstall findutils
```

---

### Post by checoimg on 2013-06-07
> **slickymaster said:**
> It seems as though you don't have find installed, which is really odd. Please run the following and post the output, please:```
sudo apt-get install --reinstall findutils
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 67 not upgraded.
Need to get 389 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) raring/main findutils amd64 4.4.2-5ubuntu1 [389 kB]
Fetched 389 kB in 1s (220 kB/s)     
dpkg: warning: 'find' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by slickymaster on 2013-06-07
> **checoimg said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 67 not upgraded.
Need to get 389 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://do.archive.ubuntu.com/ubuntu/](http://do.archive.ubuntu.com/ubuntu/) raring/main findutils amd64 4.4.2-5ubuntu1 [389 kB]
Fetched 389 kB in 1s (220 kB/s)     
dpkg: warning: 'find' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin
E: Sub-process /usr/bin/dpkg returned an error code (2)

Please post the output of:```
echo $PATH
```

---

### Post by checoimg on 2013-06-07
> **slickymaster said:**
> Please post the output of:```
echo $PATH
```

/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

---

### Post by slickymaster on 2013-06-07
> **checoimg said:**
> /usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

Everything looks alright with your path, also.

Let's us see if we get any feedback of:```
dpkg --get-selections | grep find
```

---

### Post by checoimg on 2013-06-07
> **slickymaster said:**
> Everything looks alright with your path, also.

Let's us see if we get any feedback of:```
dpkg --get-selections | grep find
```

findutils                    install
libconfig-find-perl                install
libfile-find-rule-perl                install
libfindlib-ocaml                install
libfindlib-ocaml-dev                install
ocaml-findlib                    install

---

### Post by slickymaster on 2013-06-07
> **checoimg said:**
> findutils                    install
libconfig-find-perl                install
libfile-find-rule-perl                install
libfindlib-ocaml                install
libfindlib-ocaml-dev                install
ocaml-findlib                    install

At last some news of it. I was starting to exasperate. So you have it installed.
Just one more thing to see if what I'm assuming is correct. Please post the output of:```
ls -l /usr/bin/ | grep find
```

---

### Post by checoimg on 2013-06-07
> **slickymaster said:**
> At last some news of it. I was starting to exasperate. So you have it installed.
Just one more thing to see if what I'm assuming is correct. Please post the output of:```
ls -l /usr/bin/ | grep find
```

-rwxr-xr-x 1 root root       23599 abr 15 11:52 find2perl
-rwxr-xr-x 1 root root        3414 oct 17  2011 findrule
-rwxr-xr-x 1 root root        4603 nov 26  2012 findsmb
-rwxr-xr-x 1 root root       10648 jun 26  2012 gst-typefind-0.10
-rwxr-xr-x 1 root root       10664 abr  5 13:04 gst-typefind-1.0
-rwxr-xr-x 1 root root       10624 abr 21 17:59 hal-find-by-capability
-rwxr-xr-x 1 root root       10656 abr 21 17:59 hal-find-by-property
-rwxr-xr-x 1 root root       10472 may 29 05:40 kiconfinder
-rwxr-xr-x 1 root root       14680 may 29 05:40 kmimetypefinder
-rwxr-xr-x 1 root root      130208 oct 29  2012 locate.findutils
-rwxr-xr-x 1 root root       10336 feb 18 09:46 memdiskfind
-rwxr-xr-x 1 root root      664216 jun  8  2012 ocamlfind
-rwxr-xr-x 1 root root      229944 oct 29  2012 oldfind
-rwxr-xr-x 1 root root      102280 sep 19  2012 sane-find-scanner
-rwxr-xr-x 1 root root        9774 oct 29  2012 updatedb.findutils

---

### Post by slickymaster on 2013-06-07
> **checoimg said:**
> -rwxr-xr-x 1 root root       23599 abr 15 11:52 find2perl
-rwxr-xr-x 1 root root        3414 oct 17  2011 findrule
-rwxr-xr-x 1 root root        4603 nov 26  2012 findsmb
-rwxr-xr-x 1 root root       10648 jun 26  2012 gst-typefind-0.10
-rwxr-xr-x 1 root root       10664 abr  5 13:04 gst-typefind-1.0
-rwxr-xr-x 1 root root       10624 abr 21 17:59 hal-find-by-capability
-rwxr-xr-x 1 root root       10656 abr 21 17:59 hal-find-by-property
-rwxr-xr-x 1 root root       10472 may 29 05:40 kiconfinder
-rwxr-xr-x 1 root root       14680 may 29 05:40 kmimetypefinder
-rwxr-xr-x 1 root root      130208 oct 29  2012 locate.findutils
-rwxr-xr-x 1 root root       10336 feb 18 09:46 memdiskfind
-rwxr-xr-x 1 root root      664216 jun  8  2012 ocamlfind
-rwxr-xr-x 1 root root      229944 oct 29  2012 oldfind
-rwxr-xr-x 1 root root      102280 sep 19  2012 sane-find-scanner
-rwxr-xr-x 1 root root        9774 oct 29  2012 updatedb.findutils

I think we're getting there. Please run the following:```
sudo ln -s /usr/bin/oldfind /usr/bin/find
```and after done that, post the output of```
ls -l /usr/bin/find
```

---

### Post by checoimg on 2013-06-07
> **slickymaster said:**
> I think we're getting there. Please run the following:```
sudo ln -s /usr/bin/oldfind /usr/bin/find
```and after done that, post the output of```
ls -l /usr/bin/find
```

That nailed it. Update was successful after this command. :D Thank you!

---

### Post by slickymaster on 2013-06-07
> **checoimg said:**
> That nailed it. Update was successful after this command. :D Thank you!

You're welcome. Glad that it's now fixed.

---

### Post by checoimg on 2013-06-07
> **slickymaster said:**
> I think we're getting there. Please run the following:```
sudo ln -s /usr/bin/oldfind /usr/bin/find
```and after done that, post the output of```
ls -l /usr/bin/find
```

Her is the output:

lrwxrwxrwx 1 root root 16 jun  7 13:40 /usr/bin/find -> /usr/bin/oldfind

---

### Post by slickymaster on 2013-06-07
> **checoimg said:**
> Her is the output:

lrwxrwxrwx 1 root root 16 jun  7 13:40 /usr/bin/find -> /usr/bin/oldfind

Let's us just correct those permissions so everything stays correct. To do it just reinstall findutils:```
sudo apt-get install --reinstall findutils
```After doing it, if you:```
~$ ls -l /usr/bin/find
```you should have an output like this:```
-rwxr-xr-x 1 root root 158364 Out 29  2012 /usr/bin/find
```

---

### Post by checoimg on 2013-06-07
> **slickymaster said:**
> Let's us just correct those permissions so everything stays correct. To do it just reinstall findutils:```
sudo apt-get install --reinstall findutils
```After doing it, if you:```
~$ ls -l /usr/bin/find
```you should have an output like this:```
-rwxr-xr-x 1 root root 158364 Out 29  2012 /usr/bin/find
```

Looks very alike.

-rwxr-xr-x 1 root root 229944 oct 29  2012 /usr/bin/find

---

### Post by slickymaster on 2013-06-07
> **checoimg said:**
> Looks very alike.

-rwxr-xr-x 1 root root 229944 oct 29  2012 /usr/bin/find

Yes, it's right, now. You're all set. Happy 'buntuing. ;)

---

### Post by checoimg on 2013-06-07
> **slickymaster said:**
> Yes, it's right, now. You're all set. Happy 'buntuing. ;)

Thanks again! :)

---

