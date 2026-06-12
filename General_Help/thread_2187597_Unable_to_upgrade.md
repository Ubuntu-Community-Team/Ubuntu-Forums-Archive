---
title: "Unable to upgrade"
date: 2013-11-12
forum: General Help
---

### Post by satimis on 2013-11-12
Hi all,

Ubuntu 12.04 desktop

$ sudo apt-get update```

.....
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
N: Ignoring file 'gcl' in directory '/etc/apt/sources.list.d/' as it has no filename extension
N: Ignoring file 'google.OLDlist' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```

$ sudo apt-get upgrade```

......
Preconfiguring packages ...
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libdca0': Is a directory
N: Ignoring file 'gcl' in directory '/etc/apt/sources.list.d/' as it has no filename extension
N: Ignoring file 'google.OLDlist' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'gcl' in directory '/etc/apt/sources.list.d/' as it has no filename extension
N: Ignoring file 'google.OLDlist' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Ran;
$ sudo apt-get clean
$ sudo apt-get autoremove

Problem still remains.

Please help.  Thanks

Rgds
satimis

---

### Post by deadflowr on 2013-11-12
What are the files in the /etc/apt/sources.list.d?

It seems you will either need to fix what is there or remove them.

The gcl has no extension, which means it probably needs the .list extension.
And the google.OLDlist is wrong.
The google one should cut out the OLD part and leave .list..

But you should post what files are in /etc/apt/sources.list.d, so as to confirm what files actually are there.
And if it would be better to remove them then try and fix them.

---

### Post by Bashing-om on 2013-11-12
satimis; Hi !

The package manager is screaming and hollering about invalid control files located at: /etc/apt/sources.list.d/.

For starters show us what the package manager sees, post the out put - between code tags - of terminal code:
```

ls -la /etc/apt/sources.list.d/

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

then we will look at the related files contents and see what is.

[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

---

### Post by satimis on 2013-11-13
Hi all.

$ ls -la /etc/apt/sources.list.d/```

total 20
drwxr-xr-x 2 root root 4096 Jul  3 14:45 .
drwxr-xr-x 6 root root 4096 Nov 11 16:46 ..
-rw-r--r-- 1 root root  176 Mar 11  2013 gcl
-rw-r--r-- 1 root root   55 Mar 11  2013 google.OLDlist
-rw-r--r-- 1 root root  160 Jul  3 14:45 the-ninja-circus-nudgeremind-precise.list

```

Thanks

satimis

---

### Post by deadflowr on 2013-11-13
What are the contents of both the gcl file and google.OLDlist file.
They should both have entries starting with deb, or #deb.

And how did you add these?

---

### Post by satimis on 2013-11-13
> **deadflowr said:**
> What are the contents of both the gcl file and google.OLDlist file.
They should both have entries starting with deb, or #deb.

And how did you add these?
Sorry, I couldn't recall when and for what purpose I added those files.  This PC has been running for more than 18 months.  It is for virtualization with Oracle VirtualBox installed.

$ cat /etc/apt/sources.list.d/gcl```

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

```

$ cat /etc/apt/sources.list.d/google.OLDlist ```

deb http://dl.google.com/linux/chrome/deb/ stable main

```

$ cat /etc/apt/sources.list.d/the-ninja-circus-nudgeremind-precise.list ```

deb http://ppa.launchpad.net/the-ninja-circus/nudgeremind/ubuntu precise main
deb-src http://ppa.launchpad.net/the-ninja-circus/nudgeremind/ubuntu precise main

```

IIRC most the time I got problem on running;
sudo apt-get update & sudo apt-get upgrade

I have to run;
sudo aptitude update & sudo aptitude upgrade
instead.

But this time the latter didn't work.

satimis

---

### Post by deadflowr on 2013-11-13
You can delete one of those, either the gcl (I'd delete this one) or the google.OLDlist one.
They are the same thing.

Then rename the one you did not delete google-chrome.list and save the run apt-get update again.

You'll need to be root(sudo) to rename and delete.

---

### Post by satimis on 2013-11-13
> **deadflowr said:**
> You can delete one of those, either the gcl (I'd delete this one) or the google.OLDlist one.
They are the same thing.

Then rename the one you did not delete google-chrome.list and save the run apt-get update again.

You'll need to be root(sudo) to rename and delete.
Hi,

Performed following steps;

$ sudo mv /etc/apt/sources.list.d/gcl /home/satimis/

$ sudo mv /etc/apt/sources.list.d/google.OLDlist /etc/apt/sources.list.d/google-chrome.list

$ sudo apt-get update
no complaint

$ sudo apt-get upgrade```

........
The following packages will be upgraded:
  checkbox checkbox-qt duplicity ffmpeg google-chrome-stable libav-tools
  libavcodec-extra-53 libavdevice53 libavfilter2 libavformat53
  libavutil-extra-51 libpostproc52 libswscale2 unzip
  xserver-xorg-video-intel-lts-quantal
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
.....
Preconfiguring packages ...
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libdca0': Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```
Still unable to upgrade

satimis

---

### Post by Bashing-om on 2013-11-13
satimis; Looking better.

Let's locate the entry that the package manager is unhappy with:
```

sudo find / -name libdca0

```
Searching your entire file system will take a bit of time, exercise patience.
And would be nice to know what version that "file" belongs to:
show us what you are running :
```

lsb_release -a
uname -a

```
And I will see what I can find for "libdca0".

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by satimis on 2013-11-13
> **Bashing-om said:**
> satimis; Looking better.

Let's locate the entry that the package manager is unhappy with:
```

sudo find / -name libdca0

```
Searching your entire file system will take a bit of time, exercise patience.
And would be nice to know what version that "file" belongs to:
show us what you are running :
```

lsb_release -a
uname -a

```
And I will see what I can find for "libdca0".

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]
Hi,

$ sudo find / -name libdca0```

/usr/share/doc/libdca0

```

$ sudo ls -la /usr/share/doc/libdca0```

total 96
drwxr-xr-x    2 root root  4096 Feb 22  2013 .
drwxr-xr-x 1513 root root 61440 Nov  8 12:50 ..
-rw-r--r--    1 root root  1485 Apr  6  2007 AUTHORS
-rw-r--r--    1 root root  1697 Oct  6  2011 changelog.Debian.gz
-rw-r--r--    1 root root  1536 Oct  6  2011 copyright
-rw-r--r--    1 root root  3689 Apr  8  2007 libdca.txt.gz
-rw-r--r--    1 root root   502 Apr 10  2007 NEWS.gz
-rw-r--r--    1 root root  2426 Apr  7  2007 README.gz
-rw-r--r--    1 root root   935 Apr  6  2007 TODO

```

$ lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise

```

$ uname -a```

Linux ubuntu 3.5.0-26-generic #42~precise1-Ubuntu SMP Mon Mar 11 22:17:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```


This Ubuntu is the host.  I almost haven't touched it evensince its installation, about 18 month.  All works are done on the VMs.  I have 27 VMs on this PC running CentOS, Ubuntu 12.04, LinuxMint7, WindowsServer 2008, debian 6/7, Windows7 respectively.  Some VMs were imported from another PC.  Each day after booting up the PC I run update and upgrade on the host.  I only use the browsers, Firefox and Chrome on the host.

Edit:
$ cat /etc/apt/sources.list```

deb http://hk.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise main restricted

deb http://hk.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise-updates main restricted

deb http://hk.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise universe
deb http://hk.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise-updates universe

deb http://hk.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://hk.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise-updates multiverse

deb http://hk.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

deb http://download.virtualbox.org/virtualbox/debian precise contrib
deb http://download.virtualbox.org/virtualbox/debian oneiric contrib
deb http://download.virtualbox.org/virtualbox/debian natty contrib
deb http://download.virtualbox.org/virtualbox/debian maverick contrib non-free
deb http://download.virtualbox.org/virtualbox/debian lucid contrib non-free
deb http://download.virtualbox.org/virtualbox/debian karmic contrib non-free
deb http://download.virtualbox.org/virtualbox/debian hardy contrib non-free
deb http://download.virtualbox.org/virtualbox/debian wheezy contrib
deb http://download.virtualbox.org/virtualbox/debian squeeze contrib non-free
deb http://download.virtualbox.org/virtualbox/debian lenny contrib non-free

```

Rgds
satimis

---

### Post by Bashing-om on 2013-11-13
satimis;

The finding of "libdca0" is surprising in that only the documentation files exist (??) Makes one wonder what happened ?

OK, what does the package manager say ?
```

dpkg -l libdca0

```
And is there a listing for it ?
```

ls -la /var/lib/dpkg/info/libdca0.list

```

On another matter;
> 

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) wheezy contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) squeeze contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lenny contrib non-free

oneric, natty, maverick, lucid, karmic and hardy no longer exist. The wheezy and  squeeze releases I can not comment on. I can not see any good in keeping old releases - that no longer have support - around.

[INDENT][INDENT]sometimes I wonder, other times I just do not know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-13
satimis;

The finding of "libdca0" is surprising in that only the documentation files exist (??) Makes one wonder what happened ?

OK, what does the package manager say ?
```

dpkg -l libdca0

```
And is there a listing for it ?
```

ls -la /var/lib/dpkg/info/libdca0.list

```

On another matter;
> 

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) wheezy contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) squeeze contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lenny contrib non-free

oneric, natty, maverick, lucid, karmic and hardy no longer exist. The wheezy and  squeeze releases I can not comment on. I can not see any good in keeping old releases - that no longer have support - around.

[INDENT][INDENT]sometimes I wonder, other times I just do not know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-13
satimis;

The finding of "libdca0" is surprising in that only the documentation files exist (??) Makes one wonder what happened ?

OK, what does the package manager say ?
```

dpkg -l libdca0

```
And is there a listing for it ?
```

ls -la /var/lib/dpkg/info/libdca0.list

```

On another matter;
> 

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) wheezy contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) squeeze contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lenny contrib non-free

oneric, natty, maverick, lucid, karmic and hardy no longer exist. The wheezy and  squeeze releases I can not comment on. I can not see any good in keeping old releases - that no longer have supparound.

[INDENT][INDENT]sometimes I wonder, other times I just do not know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-13
satimis;

The finding of "libdca0" is surprising in that only the documentation files exist (??) Makes one wonder what happened ?

OK, what does the package manager say ?
```

dpkg -l libdca0

```
And is there a listing for it ?
```

ls -la /var/lib/dpkg/info/libdca0.list

```

On another matter;
> 

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) wheezy contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) squeeze contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lenny contrib non-free

oneric, natty, maverick, lucid, karmic and hardy no longer exist. The wheezy and  squeeze releases I can not comment on. I can not see any good in keeping old releases - that no longer have supparound.

[INDENT][INDENT]sometimes I wonder, other times I just do not know
[/INDENT][/INDENT]

---

### Post by satimis on 2013-11-13
> **Bashing-om said:**
> satimis;

The finding of "libdca0" is surprising in that only the documentation files exist (??) Makes one wonder what happened ?

OK, what does the package manager say ?
```

dpkg -l libdca0

```
And is there a listing for it ?
```

ls -la /var/lib/dpkg/info/libdca0.list

```

On another matter;

oneric, natty, maverick, lucid, karmic and hardy no longer exist. The wheezy and  squeeze releases I can not comment on. I can not see any good in keeping old releases - that no longer have support - around.

[INDENT][INDENT]sometimes I wonder, other times I just do not know
[/INDENT][/INDENT]
$ dpkg -l libdca0```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libdca0        0.0.5-5        decoding library for DTS Coherent Acoustics 

```

$ ls -la /var/lib/dpkg/info/libdca0.list```

total 312
drwxr-xr-x 2 root root   4096 Nov  8 12:50 .
drwxr-xr-x 4 root root 307200 Nov  8 12:50 ..
lrwxrwxrwx 2 root root     29 Oct 27  2012 bridge -> /lib/bridge-utils/ifupdown.sh
-rwxr-xr-x 2 root root   3839 Dec 18  2009 wireless-tools
lrwxrwxrwx 2 root root     32 Jul  8 23:49 wpasupplicant -> ../../wpa_supplicant/ifupdown.sh

```


> 
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) wheezy contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) squeeze contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lenny contrib non-free 

I have no idea how they are there.  I suppose there were created each time on upgrading VirtualBox.  I'm going to comment out some of them.  Please advise which of them should remain?  Thanks

Rgds
satimis

---

### Post by Bashing-om on 2013-11-14
satimis; Well,

At least we know where the update problem arises.
The " /var/lib/dpkg/info/libdca0.list" should be only a control file, not a directory containing the irrelevant files for wireless !

Those files may be needed, so rather then deleting them .. move them some where safe where you can find them again in the event of need.
Then with that directory out of the way and nothing back in place, let's see if the package manager will rebuild the indexes.
```

sudo apt-get update
sudo apt-get upgrade

```
On that list of obsolete releases, the only 2 that are current are:
> 
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) wheezy contrib

As you say, I would comment out all the others and see what happens.

[INDENT][INDENT]hope all good now 
[/INDENT][/INDENT]

---

### Post by satimis on 2013-11-14
> **Bashing-om said:**
> satimis; Well,

At least we know where the update problem arises.
The " /var/lib/dpkg/info/libdca0.list" should be only a control file, not a directory containing the irrelevant files for wireless !

Those files may be needed, so rather then deleting them .. move them some where safe where you can find them again in the event of need.
Then with that directory out of the way and nothing back in place, let's see if the package manager will rebuild the indexes.
```

sudo apt-get update
sudo apt-get upgrade

```
On that list of obsolete releases, the only 2 that are current are:

As you say, I would comment out all the others and see what happens.

[INDENT][INDENT]hope all good now 
[/INDENT][/INDENT]

$ sudo mv /usr/share/doc/libdca0 Temp_Storage/

and rename the directory as libdca0.OLD

$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.OLD
$ sudo gedit /etc/apt/sources.list
comment out all VirtualBox repositories leaving following 2 behind
```

deb http://download.virtualbox.org/virtualbox/debian precise contrib
deb http://download.virtualbox.org/virtualbox/debian wheezy contrib

```

$ sudo find / -name libdca0
No output

$ sudo apt-get update
No complaint

$ sudo apt-get upgrade```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  checkbox checkbox-qt duplicity ffmpeg flashplugin-installer libav-tools
  libavcodec-extra-53 libavdevice53 libavfilter2 libavformat53
  libavutil-extra-51 libpostproc52 libswscale2 unzip
  xserver-xorg-video-intel-lts-quantal
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/6,918 kB of archives.
After this operation, 12.3 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libdca0': Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Problem still remains

Edit:
I read your advice again;```

....
At least we know where the update problem arises.
The " /var/lib/dpkg/info/libdca0.list" should be only a control file, not a directory containing the irrelevant files for wireless !

```
Whether I need to remove libdca0.list directory plus its files ?


satimis

---

### Post by Bashing-om on 2013-11-14
satimis; Hey, you do good !

Yeah, we want no listing at all in "/var/lib/dpkg/info/" directory for 'libdca0' ! My concern is that those files, copied there by some error, might be of value for the wireless applications. They "might" need to be needed at some point. Be nice to have them handy if and when that need should arise. I suggest a temporary place as anywhere in your /home directory -> out of the way and still handy.

Then let's see if the package manager will replace that missing entry in the  "/var/lib/dpkg/info/" directory :
```

sudo apt-get update

```
Data bases are thus synced with the mirror site, and now let's try and update the installed applications:
```

sudo apt-get upgrade

```

[INDENT][INDENT]I anticipate all good at this point
[/INDENT][/INDENT]

---

### Post by satimis on 2013-11-14
> **Bashing-om said:**
> satimis; Hey, you do good !

Yeah, we want no listing at all in "/var/lib/dpkg/info/" directory for 'libdca0' ! My concern is that those files, copied there by some error, might be of value for the wireless applications. They "might" need to be needed at some point. Be nice to have them handy if and when that need should arise. I suggest a temporary place as anywhere in your /home directory -> out of the way and still handy.

Then let's see if the package manager will replace that missing entry in the  "/var/lib/dpkg/info/" directory :
```

sudo apt-get update

```
Data bases are thus synced with the mirror site, and now let's try and update the installed applications:
```

sudo apt-get upgrade

```

[INDENT][INDENT]I anticipate all good at this point
[/INDENT][/INDENT]
removed libdca0.list including files to /home/satimis/Temp_Storage and renamed it libdca0.list.OLD

$ sudo apt-get update
No complaint

$ sudo apt-get upgrade```

.....
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  checkbox checkbox-qt duplicity ffmpeg flashplugin-installer libav-tools
  libavcodec-extra-53 libavdevice53 libavfilter2 libavformat53
  libavutil-extra-51 libpostproc52 libswscale2 unzip
  xserver-xorg-video-intel-lts-quantal
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/6,918 kB of archives.
After this operation, 12.3 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `libdca0' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `klibc-utils' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Still failed

Edit:
I have VMs running Ubuntu 12.04 on this PC.  Just checked on one VM

$ ls -la /var/lib/dpkg/info/libdca0.list ```

-rw-r--r-- 1 root root 348 Feb 23  2013 /var/lib/dpkg/info/libdca0.list

```

libdca0.list directory is needed.

Performed;

$ sudo mkdir /var/lib/dpkg/info/libdca0.list

$ sudo apt-get upgrade```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  checkbox checkbox-qt duplicity ffmpeg flashplugin-installer libav-tools
  libavcodec-extra-53 libavdevice53 libavfilter2 libavformat53
  libavutil-extra-51 libpostproc52 libswscale2 unzip
  xserver-xorg-video-intel-lts-quantal
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/6,918 kB of archives.
After this operation, 12.3 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `klibc-utils' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Still failed

VM
$ lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise

```

$ uname -a```

Linux localhost 3.5.0-43-generic #66~precise1-Ubuntu SMP Thu Oct 24 14:52:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```


satimis

---

### Post by Bashing-om on 2013-11-14
satimis;

I do applaud your trying to understand, however;
I say again .."libdca0.list" is a file. Stand-a-lone, not a directory.
"libdca0.list" is one file of hundreds located in the path /var/lib/dpkg/info/ ...
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
In your example the leading '-' in the permissions field says this entry is a file. For it to be listed as a directory that leading character would be a 'd'.
For clarification, as these are just controls files and as such just scripts, one can see the contents and exactly what any one file is:
```

cat /var/lib/dpkg/info/gedit.list

``` for example.  

If you were to delete that entry, when you run "sudo apt-get update" I expect the package manager to replace that file.
Else, if no, (re-)install the package "libdca0.list". The package manager for sure then will replace that file.

Upon running "sudo apt-get upgrade", I expect all to be hunky dory.

[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

---

### Post by satimis on 2013-11-15
> **Bashing-om said:**
>  - snip -

If you were to delete that entry, when you run "sudo apt-get update" I expect the package manager to replace that file.
Else, if no, (re-)install the package "libdca0.list". The package manager for sure then will replace that file.

Upon running "sudo apt-get upgrade", I expect all to be hunky dory.

[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

$ sudo rmdir /var/lib/dpkg/info/libdca0.list

$ sudo apt-get install --reinstall libdca0.list```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libdca0.list
E: Couldn't find any package by regex 'libdca0.list'

```

$ sudo apt-get install --reinstall libdca0```

[sudo] password for satimis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 15 not upgraded.
Need to get 109 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://hk.archive.ubuntu.com/ubuntu/ precise/universe libdca0 amd64 0.0.5-5 [109 kB]
Fetched 109 kB in 1s (68.2 kB/s)  
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `klibc-utils' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```


$ sudo find / -name klibc-utils```

/usr/share/doc/klibc-utils
/usr/share/lintian/overrides/klibc-utils

```

$ ls -la /usr/share/doc/klibc-utils```

lrwxrwxrwx 1 root root 8 Feb 22  2013 /usr/share/doc/klibc-utils -> libklibc

```

$ ls -la /usr/share/lintian/overrides/klibc-utils ```

-rw-rw-r-- 1 root root 65 Nov 20  2011 /usr/share/lintian/overrides/klibc-utils

```
 
$ cat /usr/share/lintian/overrides/klibc-utils ```

klibc-utils: statically-linked-binary
klibc-utils: embedded-zlib

```


satimis

---

### Post by satimis on 2013-11-15
Hi folks,

Finally I fixed the problem as follows:-

$ sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.OLD20131115

$ ls -la /var/lib/dpkg/```

total 7808
drwxr-xr-x  8 root root    4096 Nov 15 22:19 .
drwxr-xr-x 61 root root    4096 Mar 26  2013 ..
drwxr-xr-x  2 root root    4096 Nov  8 12:51 alternatives
-rw-r--r--  1 root root 1488516 Nov  8 12:51 available
-rw-r--r--  1 root root 1487316 Nov  5 10:41 available-old
-rw-r--r--  1 root root       8 Feb 14  2013 cmethopt
-rw-r--r--  1 root root    1316 Aug  8 12:19 diversions
-rw-r--r--  1 root root    1362 Aug  8 12:19 diversions-old
drwxr-xr-x  3 root root  307200 Nov 15 17:36 info
-rw-r-----  1 root root       0 Nov 15 22:17 lock
drwxr-xr-x  2 root root    4096 Apr 13  2012 parts
-rw-r--r--  1 root root     135 Feb 14  2013 statoverride
-rw-r--r--  1 root root 1551687 Nov 15 22:17 status
-rw-r--r--  1 root root 1551687 Nov 15 19:54 status-old
-rw-r--r--  1 root root 1551687 Nov 15 22:19 status.OLD20131115
drwxr-xr-x  2 root root    4096 Nov 10 03:09 tmp.ci
drwxr-xr-x  2 root root    4096 Nov  8 12:51 triggers
drwxr-xr-x  2 root root    4096 Nov 15 22:17 updates

```

1)
$ sudo gedit /var/lib/dpkg/status

delete following lines;```

Package: klibc-utils
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 367
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: klibc
Version: 1.5.25-1ubuntu2
Depends: libklibc (= 1.5.25-1ubuntu2)
Description: small utilities built with klibc for early boot
 This package contains a collection of programs that are linked
 against klibc. These duplicate some of the functionality of a
 regular Linux toolset, but are typically much smaller than their
 full-function counterparts.  They are intended for inclusion in
 initramfs images and embedded systems.
Original-Maintainer: maximilian attems <maks@debian.org>

```

$ sudo dpkg --configure -a                                      

$ sudo apt-get -f install```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  klibc-utils
The following NEW packages will be installed:
  klibc-utils
0 upgraded, 1 newly installed, 0 to remove and 15 not upgraded.
Need to get 181 kB of archives.
After this operation, 376 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://hk.archive.ubuntu.com/ubuntu/ precise/main klibc-utils amd64 1.5.25-1ubuntu2 [181 kB]
Fetched 181 kB in 1s (122 kB/s)       
Selecting previously unselected package klibc-utils.
(Reading database ... 
dpkg: warning: files list file for package `libdca0' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `libdirac-encoder0' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```


2)
$ sudo gedit /var/lib/dpkg/status

Removed following lines;```

Package: libdirac-encoder0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 588
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: dirac
Version: 1.0.2-4build1
Replaces: libdirac0, libdirac0c2a
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.4.0)
Conflicts: libdirac0, libdirac0c2a
Description: open and royalty free high quality codec - encoder library
 Dirac is an advanced royalty-free video compression format designed for a wide
 range of uses, from delivering low-resolution web content to broadcasting HD
 and beyond, to near-lossless studio editing.
 .
 This package contains the dirac encoder library.
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Homepage: http://diracvideo.org/

```

$ sudo dpkg --configure -a                                      

$ sudo apt-get -f install```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  klibc-utils libav-tools libavcodec-extra-53 libavdevice53 libavfilter2
  libavformat53 libavutil-extra-51 libdirac-encoder0 libpostproc52 libswscale2
Suggested packages:
  libfaad0
The following NEW packages will be installed:
  klibc-utils libdirac-encoder0
The following packages will be upgraded:
  libav-tools libavcodec-extra-53 libavdevice53 libavfilter2 libavformat53
  libavutil-extra-51 libpostproc52 libswscale2
8 upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
Need to get 243 kB/4,798 kB of archives.
After this operation, 992 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://hk.archive.ubuntu.com/ubuntu/ precise/universe libdirac-encoder0 amd64 1.0.2-4build1 [243 kB]
Fetched 243 kB in 2s (113 kB/s)             
(Reading database ... 
dpkg: warning: files list file for package `libdca0' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `krb5-locales' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

3)
$ sudo gedit /var/lib/dpkg/status

Again removed following lines;```

Package: krb5-locales
Status: install ok installed
Multi-Arch: foreign
Priority: standard
Section: localization
Installed-Size: 1516
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: krb5
Version: 1.10+dfsg~beta1-2ubuntu0.3
Description: Internationalization support for MIT Kerberos
 Kerberos is a system for authenticating users and services on a network.
 Kerberos is a trusted third-party service.  That means that there is a
 third party (the Kerberos server) that is trusted by all the entities on
 the network (users and services, usually called "principals").
 .
 This is the MIT reference implementation of Kerberos V5.
 .
 This package contains internationalized messages for MIT Kerberos.
Homepage: http://web.mit.edu/kerberos/
Original-Maintainer: Sam Hartman <hartmans@debian.org>

```

$ sudo dpkg --configure -a                                      

$ sudo apt-get -f install
This time no complaint

$ sudo apt-get install klibc-utils libdirac-encoder0 krb5-locales
No complaint

Now I can run;
$ sudo apt-get update && sudo apt-get upgrade

without problem

It tooks a long way to fix the problem.  Otherwise I have to reinstall Ubuntu 12.04

(I found the solution on searching;
dpkg: unrecoverable fatal error, aborting:
[http://ubuntuforums.org/archive/index.php/t-1232143.html](http://ubuntuforums.org/archive/index.php/t-1232143.html) )

I have no idea how can I render into this problem.  This is the Host of VirtualBox.  I only run Firefox and Google Chrome on it.  All works are done on VMs.

Anyway lot of thanks for your support.

A further question in case of failure, in the worst case, can I copy;
/var/lib/dpkg/*
from a Ubuntu 12.04 VM to the Host?

Rgds
satimis

---

### Post by Bashing-om on 2013-11-15
satimis; Good deal !

Pleased you stuck with it and have resolution .
As to copying " /var/lib/dpkg/*" ---NO, not in it's entirety as that directory is tailored to that particular install per the package management system.
One may - if the versions are the same - copy individual files and most likely will be good. However I always endorse utilizing the package managements tools and try not to circumvent the checks and balances that are in-place. But, there are those times when it is needful to give the package manager a helping hand, as you have discovered.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

