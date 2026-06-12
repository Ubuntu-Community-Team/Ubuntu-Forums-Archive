---
title: "apt-get update errors"
date: 2008-01-08
forum: General Help
---

### Post by kubusiowaty on 2008-01-08
Hi there,

I've been using different Ubuntu distros for about 4 years.
It is the first time I've encountered such a strange problem with apt.

I've recently installed Ubuntu 7.10 x86 on my desktop.
I'm having some serious problems while trying to update repository info with apt-get update:

```

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-pl
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-pl
Pob: 1 http://wine.budgetdedicated.com gutsy Release.gpg [191B]                
Ign http://wine.budgetdedicated.com gutsy/main Translation-pl                 
Traf http://wine.budgetdedicated.com gutsy Release  
B&#322;&#261;d http://wine.budgetdedicated.com gutsy Release
  
Pob: 2 http://wine.budgetdedicated.com gutsy Release [1005B]
Ign http://wine.budgetdedicated.com gutsy Release
Ign http://wine.budgetdedicated.com gutsy/main Packages
Traf http://wine.budgetdedicated.com gutsy/main Sources
Traf ftp://ftp.man.szczecin.pl gutsy-updates Release.gpg
Traf http://wine.budgetdedicated.com gutsy/main Packages
Pob: 3 ftp://ftp.man.szczecin.pl gutsy-updates/main Translation-pl
Ign ftp://ftp.man.szczecin.pl gutsy-updates/main Translation-pl
Pob: 4 ftp://ftp.man.szczecin.pl gutsy-updates/restricted Translation-pl
Ign ftp://ftp.man.szczecin.pl gutsy-updates/restricted Translation-pl
Pob: 5 ftp://ftp.man.szczecin.pl gutsy-updates/universe Translation-pl
Ign ftp://ftp.man.szczecin.pl gutsy-updates/universe Translation-pl
Pob: 6 ftp://ftp.man.szczecin.pl gutsy-updates/multiverse Translation-pl
Ign ftp://ftp.man.szczecin.pl gutsy-updates/multiverse Translation-pl
Traf ftp://ftp.man.szczecin.pl gutsy Release.gpg
Traf ftp://ftp.man.szczecin.pl gutsy/main Translation-pl
Traf ftp://ftp.man.szczecin.pl gutsy/restricted Translation-pl
Traf ftp://ftp.man.szczecin.pl gutsy/universe Translation-pl
Traf ftp://ftp.man.szczecin.pl gutsy/multiverse Translation-pl
Traf ftp://ftp.man.szczecin.pl gutsy-security Release.gpg
Pob: 7 ftp://ftp.man.szczecin.pl gutsy-security/main Translation-pl
Ign ftp://ftp.man.szczecin.pl gutsy-security/main Translation-pl
Pob: 8 ftp://ftp.man.szczecin.pl gutsy-security/restricted Translation-pl
Ign ftp://ftp.man.szczecin.pl gutsy-security/restricted Translation-pl
Pob: 9 ftp://ftp.man.szczecin.pl gutsy-security/universe Translation-pl
Ign ftp://ftp.man.szczecin.pl gutsy-security/universe Translation-pl
Pob: 10 ftp://ftp.man.szczecin.pl gutsy-security/multiverse Translation-pl
Ign ftp://ftp.man.szczecin.pl gutsy-security/multiverse Translation-pl
Pob: 11 ftp://ftp.man.szczecin.pl gutsy-updates Release [58,5kB]
Pob: 12 ftp://ftp.man.szczecin.pl gutsy Release [65,9kB]
Pob: 13 ftp://ftp.man.szczecin.pl gutsy-security Release [51,2kB]              
Traf ftp://ftp.man.szczecin.pl gutsy-updates/main Packages                     
Traf ftp://ftp.man.szczecin.pl gutsy-updates/restricted Packages               
Traf ftp://ftp.man.szczecin.pl gutsy-updates/universe Packages                 
Traf ftp://ftp.man.szczecin.pl gutsy-updates/multiverse Packages               
Traf ftp://ftp.man.szczecin.pl gutsy/main Packages                             
Traf ftp://ftp.man.szczecin.pl gutsy/restricted Packages                       
Pob: 14 ftp://ftp.man.szczecin.pl gutsy/universe Packages [4065kB]             
Traf ftp://ftp.man.szczecin.pl gutsy/multiverse Packages                       
Traf ftp://ftp.man.szczecin.pl gutsy-security/main Packages                    
99% [14 Packages bzip2 3599360]                                      113kB/s 0s
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

```

This problem occurs random. It does not matter what server I use.
My internet connection is fine. Checked on another network card, but still no effect.

Another way the problem shows itself is the fact that whenever I download any packages using synaptic some of them are always corrupted.

Anyone please help.
James

---

### Post by zvacet on 2008-01-08
```
cat /etc/apt/sources.list
```

Did you try to change ftp with http ?

---

### Post by Jussi Kukkonen on 2008-01-08
> **kubusiowaty said:**
> Hi there,

I've been using different Ubuntu distros for about 4 years.
It is the first time I've encountered such a strange problem with apt.

I've recently installed Ubuntu 7.10 x86 on my desktop.
I'm having some serious problems while trying to update repository info with apt-get update:


You use [ftp://ftp.man.szczecin.pl](ftp://ftp.man.szczecin.pl) as your repository and their package list seems to be corrupted. Is there a reason to use that instead of the canonical repo [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) ?

If the repository is reliable and updated the problem will probably be fixed on the next mirror-update, though (maybe tomorrow?)

---

### Post by kubusiowaty on 2008-01-08
Yes I did.

Strange thing happened after 9 or 10 apt-get update he successfully updated the list.
Still thanks for the suggesion.

One problem remains. In My status /var/lib/dpkg/status file there are many symbols like: ```
 ` 
``` which brake dpkg while trying to meet dependencies. This problem is hunting me. No matter what version of Ubunu I install on my machine the status file sooner or later becomes broken. I have standard repositories + winehq.

Any ideas?
Thanks,
James

---

### Post by kubusiowaty on 2008-01-08
> You use [ftp://ftp.man.szczecin.pl](ftp://ftp.man.szczecin.pl) as your repository and their package list seems to be corrupted. Is there a reason to use that instead of the canonical repo [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) ?

The funny thing is that this error existed on all repositories. I've started with [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) and checked few others. I've ended on [ftp://ftp.man.szczecin.pl](ftp://ftp.man.szczecin.pl) because it had less errors then the others.

James

---

### Post by noppengummi on 2008-04-06
I appear to encounter the same problem as kubusiowaty.

The result of "apt-get update" is very random and no server / mirror has so far managed to provide reliable results. It gets worse: when installing software with "apt-get install" downloaded packages tend to get corrupted too - which results in loads of broken dependancies and me deleting the packages from /var/cache/apt/archive.... over and over again until they are downloaded without fault.

I do not believe that either apt-get or dpkg are to blame... it must have something to do with either my hardware or (more likely) the way it is handled. 
More evidence to support this thesis: I had to download the Nvidia-driver at least 3 times before the checksum was alright. Lastly my Bittorrent Downloads show about 5% corrupted packages.
My DSL-Connection can't be blamed, i have 3 other XX-buntu machines running and updating just fine.

This problem persists over Gutsy (7.10 alternate, tried Ubuntu and Kubuntu, cd install as well as netboot) as well as Hardy Beta (8.04 alternate, both Ubuntu and Kubuntu).

My configuration:
Intel E8500 @ standard clocking on Gigabyte GA-P35-DS3P 
Nothing out of the ordinary really, I use the onboard ethernet controller ( RTL 8111B on Intel ICH9R ). 

Any advice would be greatly appreciated...

---

