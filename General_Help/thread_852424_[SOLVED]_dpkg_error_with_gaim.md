---
title: "[SOLVED] dpkg error with gaim??"
date: 2008-07-07
forum: General Help
---

### Post by immolo on 2008-07-07
Heya,

I had a file system error a few days ago on my computer and after 'fixing' it I'm having problems using apt I seem to get the same error message no matter what package I try to install does anyone know of a fix this as this seems to be the only problem with the computer now.

The error I get is:

 (Reading database ... 
dpkg: serious warning: files list file for package `gnome-cards-data' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/pidgin_1%3a2.4.1-1ubuntu2_i386.deb (--unpack):
 files list file for package `gaim' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/pidgin_1%3a2.4.1-1ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks for any help you can give on this issue

Immolo

---

### Post by sdennie on 2008-07-07
See if running the following helps:

```

sudo apt-get clean

```

---

### Post by immolo on 2008-07-07
That just runs with no output but still gives an error when I try to install something.

---

### Post by sdennie on 2008-07-07
Does it give the same error?  Can you post the output?

---

### Post by immolo on 2008-07-07
(Reading database ... 
dpkg: serious warning: files list file for package `gnome-cards-data' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/libsilc-1.1-2_1.1.5-1ubuntu1_i386.deb (--unpack):
 files list file for package `gaim' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libsilc-1.1-2_1.1.5-1ubuntu1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

is the new message

---

### Post by forger on 2008-07-07
Are you using ubuntu hardy heron 8.04? If not, **STOP**!

Gaim doesn't exist anymore, **pidgin** is the new package

If you're trying to download/install pidgin from some other source, **STOP**! Use the package from the repositories.

Do you use kde or gnome? libsilc is used by kopete from what I know.

try the following (yes, as they're written)
**[COLOR="Red"]WARNING!! Could break your system, use at your own risk![/COLOR]**

1) ```
sudo apt-get -f install; sudo apt-get update; sudo apt-get upgrade
```

2) If (1) didn't work:
```
sudo dpkg --configure -a; sudo apt-get update; sudo apt-get upgrade
```

3) If (1) and (2) didn't work, do the following commands:
```
cd $HOME; sudo aptitude download libsilc-1.1-2
```
```
sudo rm /var/cache/apt/archives/libsilc-*; sudo dpkg -P --force-depends libsilc-1.1-2; sudo dpkg -i libsilc-1.1-2-*.deb
```

```

sudo apt-get update; sudo apt-get upgrade

```

---

### Post by immolo on 2008-07-08
I am using hardy and I was also wondering about why gaim is being mentioned this system was updated from a gusty install but I'm sure we were using pidgin by then.

As I am using hardy should I use some different commands also I running normal Ubuntu.

---

### Post by iaculallad on 2008-07-08
Try removing/moving gaim.list:

```
sudo mv /var/lib/dpkg/info/gaim.list /var/lib/dpkg/info/gaim.list.bak
```

Then:

```
sudo apt-get remove gaim
```

---

### Post by immolo on 2008-07-08
ok thanks iaclallad that got me further then before but now my new error I getting is this:

 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libpurple0 pidgin pidgin-data
The following packages will be upgraded:
  libnspr4-0d
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
12 not fully installed or removed.
Need to get 0B/122kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 191946 files and directories currently installed.)
Preparing to replace libnspr4-0d 4.7.1+1.9-0ubuntu0.8.04.1 (using .../libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.2_i386.deb) ...
Unpacking replacement libnspr4-0d ...
dpkg: error processing /var/cache/apt/archives/libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libnspr4.so', which is also in package libnspr4
Errors were encountered while processing:
 /var/cache/apt/archives/libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I guessing my filesystem error just killed pidgin and will need to be removed and then reinstalled.

---

### Post by immolo on 2008-07-08
Ok I think I have this fixed now thanks guys for all your help

---

