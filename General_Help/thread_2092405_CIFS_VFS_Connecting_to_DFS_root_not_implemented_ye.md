---
title: "CIFS VFS: Connecting to DFS root not implemented yet"
date: 2012-12-07
forum: General Help
---

### Post by dkarnows on 2012-12-07
Hi,

Trying to mount a CIFS network drive on a new Xubuntu 12.10 installation. This entry used to work fine in the old machine (Xubuntu 12.04) but doesn't on my new machine:

[FONT="Courier New"]$ sudo mount -o username=dkarnowski,credentials=/home/dkarnowski/.smbcredentials,domain=virtu.local,file_mode=0775,dir_mode=0775 //filer1.virtu.local/vfin-public /home/dkarnowski/vfin-public/
mount: wrong fs type, bad option, bad superblock on //filer1.virtu.local/vfin-public,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/FONT]

Here's the corresponding kern.log errors:

[FONT="Courier New"]Dec  7 15:18:56 dkarnowski-Precision-T5600 kernel: [109947.614822] CIFS VFS: Connecting to DFS root not implemented yet
Dec  7 15:18:56 dkarnowski-Precision-T5600 kernel: [109947.615135] CIFS VFS: cifs_mount failed w/return code = -22[/FONT]


There are various references to this on the web and [a patch was released for the 3.4.5 kernel]("http://git.kernel.org/?p=linux/kernel/git/stable/stable-queue.git;a=commitdiff;h=b044f0622abd4abd667bf278d6c0686dd95fca5d#patch46"). I'm currently on 3.5.0-19:

[FONT="Courier New"]$ uname -a
Linux dkarnowski-Precision-T5600 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux[/FONT]

I took a look at the 3.5 kernel source and that patch seems to be in there, so presumably this is something different.

I currently have cifs-utils 2.5.5-1ubuntu1 installed.

Not sure where to look next. Any help appreciated.

---

### Post by cek on 2012-12-09
Same problem here.  #49 from [http://ubuntuforums.org/showthread.php?t=1946145&page=5](http://ubuntuforums.org/showthread.php?t=1946145&page=5) got it working for me.

Short story:

```
sudo apt-get update
sudo apt-get install cifs-utils
```

---

### Post by hamen on 2012-12-10
Thank you @cek

---

### Post by dkarnows on 2012-12-10
> **cek said:**
> 
Short story:

```
sudo apt-get update
sudo apt-get install cifs-utils
```

I already had/have the latest version of cifs-utils installed: 2:5.5-1ubuntu1. Presumably my problem is different from yours.

---

### Post by dkarnows on 2012-12-13
I apt-get removed cifs-utils and then apt-get installed it (same version) and now it works. So weird, but yes, seems  it was cifs-utils related. The removal also removed packages xubuntu-live-settings, lupin-casper, and casper. I didn't reinstall those. So perhaps my problem was related to one of those, perhaps not. But anyway, all is good now for me.

---

### Post by fistikuffs on 2012-12-19
> **cek said:**
> Same problem here.  #49 from [http://ubuntuforums.org/showthread.php?t=1946145&page=5](http://ubuntuforums.org/showthread.php?t=1946145&page=5) got it working for me.

Short story:

```
sudo apt-get update
sudo apt-get install cifs-utils
```
Worked for me on Kubuntu 12.04. Thanks!

---

