---
title: "Can't update/install. Disk seen as full"
date: 2013-05-11
forum: General Help
---

### Post by feddozz on 2013-05-11
hi all,

I have the following problem: update manager suggests to run ```
sudo apt-get install -f
``` because of unresolved dependencies. when i run it i get the following messages```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-41-generic-pae
The following NEW packages will be installed
  linux-headers-3.2.0-41-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 30 not upgraded.
2 not fully installed or removed.
Need to get 0 B/981 kB of archives.
After this operation, 11.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 593409 files and directories currently installed.)
Unpacking linux-headers-3.2.0-41-generic-pae (from .../linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-41-generic-pae/include/config/dvb/firedtv/input.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-41-generic-pae/include/config/dvb/firedtv/input.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

My root partition has 1.5Gb free and the /home partition has 5 Gb free.

Could you please help? Currently I can't update or install anything on my system because of this

Thanks

---

### Post by Hekabe on 2013-05-11
Have you tried manually installing each of the listed packages using apt-get install?

---

### Post by feddozz on 2013-05-11
> **Hekabe said:**
> Have you tried manually installing each of the listed packages using apt-get install?

Just tried and I get exactly the same result above.

---

### Post by Hekabe on 2013-05-11
What does running df -h tell you?

---

### Post by Bashing-om on 2013-05-11
+1 for Hekabe;

The error of "disk full" generally points to a "partition" full and the "df" command indicates where to look for that condition.[INDENT]
just try'n to help

[/INDENT]

---

### Post by feddozz on 2013-05-12
here it is
```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       9.2G  7.3G  1.5G  84% /
udev            743M  4.0K  743M   1% /dev
tmpfs           300M  828K  299M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            750M  268K  750M   1% /run/shm
/dev/sda6        27G   21G  4.9G  81% /home

```

---

### Post by Bashing-om on 2013-05-12
feddozz;
I regret that there was such a long delay in getting back to this thread, busy forum.

I bet that your /boot partition has lots of old kernels and headers. Removing them will free up a lot of space (and inodes as well).

Let's look: Terminal codes:
```
cd /boot
ls -lah
cd # to get back to the home directory
```to identify the files to be removed.[INDENT=2]
regards

[/INDENT]

---

### Post by feddozz on 2013-05-13
> **Bashing-om said:**
> feddozz;
I regret that there was such a long delay in getting back to this thread, busy forum.

I bet that your /boot partition has lots of old kernels and headers. Removing them will free up a lot of space (and inodes as well).

Let's look: Terminal codes:
```
cd /boot
ls -lah
cd # to get back to the home directory
```to identify the files to be removed.[INDENT=2]
regards

[/INDENT]

Yes, my /boot folder has loads of old kernels, I'll remove them.  but bear in mind that it is a folder part of the root partition which has some space left. Do you thing it could solve the problem? Anyway, i'll let you know what happens.

---

### Post by Bashing-om on 2013-05-13
feddozz ; Hi !

Yeah, removing the old kernels images and header files will help a lot.

Are you comforable with your procedure to remove them ? I have the recommended terminal commands handy.
[INDENT=2]
my regards

[/INDENT]

---

### Post by feddozz on 2013-05-13
> **Bashing-om said:**
> feddozz ; Hi !

Yeah, removing the old kernels images and header files will help a lot.

Are you comforable with your procedure to remove them ? I have the recommended terminal commands handy.
[INDENT=2]
my regards

[/INDENT]

Hi, I removed the old kernels and associated files from the /boot folder. it did not solve the problem, tough.

Is there a way of installing those missing packages manually. Not apt-get but really downloading and placing in the right foler. to me it looks like something went wrong during an upgrade and now things are not configure correctly.

---

### Post by Bashing-om on 2013-05-13
feddozz;

There is no better way to administer the packages than with the Debian package management tools, apt-get, dpkg or aptitude, one may use the GUI front ends of these tools but, bottom line apt-get and dpkg get the job done. 
> apt-get clean command clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When APT is used as a dselect method, clean is run automatically. Those who do not use dselect will likely want to run apt-get clean from time to time to free up disk space.

To clear the cache from the command line, type the following:
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
```
Finish up and see what the status is:
```

sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get dist-upgrade ## does a "smart" update and maybe deal with the "linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb"
##/and install held back packages,

```

That I expect to straigten out the package manager's data base and config files. Then If errors still we can look at the individual packages and see what can be done.

Post the errors if any after the "sudo apt-get dist-upgrade" command.[INDENT=2]
just what I think

[/INDENT]

---

### Post by feddozz on 2013-05-14
I tried the commands but it did not work , here is the result
```
 
sudo apt-get autoclean 
Reading package lists... Done
Building dependency tree       
Reading state information... Done

sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-41-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

sudo apt-get clean

sudo apt-get update 
Hit http://gb.archive.ubuntu.com precise Release.gpg
Get:1 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg
Hit http://gb.archive.ubuntu.com precise Release          
Get:2 http://gb.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://gb.archive.ubuntu.com precise-backports Release                     
Hit http://gb.archive.ubuntu.com precise/main Sources     
Hit http://gb.archive.ubuntu.com precise/restricted Sources
Hit http://gb.archive.ubuntu.com precise/universe Sources
Hit http://gb.archive.ubuntu.com precise/multiverse Sources
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex
Get:5 http://gb.archive.ubuntu.com precise-updates/main Sources [383 kB]
Get:6 http://security.ubuntu.com precise-security/main Sources [71.8 kB]
Get:7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:8 http://security.ubuntu.com precise-security/universe Sources [24.4 kB]   
Get:9 http://gb.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]
Get:10 http://security.ubuntu.com precise-security/multiverse Sources [1,380 B]
Get:11 http://security.ubuntu.com precise-security/main i386 Packages [267 kB] 
Get:12 http://gb.archive.ubuntu.com precise-updates/universe Sources [87.1 kB] 
Get:13 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [6,582 B]
Get:14 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [621 kB]
Get:15 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:16 http://security.ubuntu.com precise-security/universe i386 Packages [75.0 kB]
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,375 B]
Get:18 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:19 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:20 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:21 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:22 http://security.ubuntu.com precise-security/main Translation-en [122 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:23 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]
Get:24 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [203 kB]
Get:25 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]
Get:26 http://gb.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:27 http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:28 http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:29 http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://gb.archive.ubuntu.com precise-backports/main Sources  
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/main Translation-en
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 2,013 kB in 2s (857 kB/s)                 
Reading package lists... Done


sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-41-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-41-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

 sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-41-generic-pae
The following NEW packages will be installed
  linux-headers-3.2.0-41-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 36 not upgraded.
2 not fully installed or removed.
Need to get 981 kB of archives.
After this operation, 11.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-41-generic-pae i386 3.2.0-41.66 [981 kB]
Fetched 981 kB in 0s (1,635 kB/s)                          
(Reading database ... 593409 files and directories currently installed.)
Unpacking linux-headers-3.2.0-41-generic-pae (from .../linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.2.0-41-generic-pae/include/config/i2o/lct/notify': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2013-05-14
feddozz; Making good progress.
With the exception of "linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb" all is in good shape. Presently I am a bit uncertain as to what is going on as I am running 12.04 fully updated and my 64 bit version is an older version than what is to be installed on your system (32bit the difference ?). 
> sysop1@1204-a:~$ uname -rm
3.2.0-41-generic x86_64
sysop1@1204-a:~$ 
In any event lets see what version image/architecture you presently have installed;
Please post your out put of :
```
uname -rm
``` before proceeding with removal/(re)install.[INDENT]
regards

[/INDENT]

---

### Post by feddozz on 2013-05-15
there  you go ```
uname -rm
3.2.0-41-generic-pae i686

```

---

### Post by Bashing-om on 2013-05-15
feddozz:
 And here you go ; Terminal codes:
```

sudo dpkg --remove linux-generic-pae
sudo apt-get install linux-generic-pae
sudo apt-get update
sudo apt-get upgrade

```
//
> 
 Removing linux-generic will do no harm at all. It is only a "meta-package" depending on linux-image-generic and linux-headers-generic. Those two are themselves meta-packages depending on the respective latest image/headers packages.

You can see this for yourself by issuing apt-cache show linux-generic, apt-cache show linux-image-generic and apt-cache show linux-headers-generic.

The purpose of meta-packages is to pull-in the packages on which they depend, they have no functionality at all. On the other hand removing one will not remove it's dependencies - so no danger to the system.

After having fixed the original issue<which you have done> you can of course install linux-generic again.

I expect all is in good shape now ??[INDENT=2]
still learning after all these years
[/INDENT]

---

### Post by feddozz on 2013-05-17
> **Bashing-om said:**
> feddozz:
 And here you go ; Terminal codes:
```

sudo dpkg --remove linux-generic-pae
sudo apt-get install linux-generic-pae
sudo apt-get update
sudo apt-get upgrade

```
//


I expect all is in good shape now ??[INDENT=2]
still learning after all these years
[/INDENT]

Hi 
still not sorted
```

sudo apt-get install linux-generic-pae

```

complains. I'll post the error messages.

Here you go
```

sudo apt-get install linux-generic-pae 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.43.51) but 3.2.0.41.49 is to be installed
                     Depends: linux-headers-generic-pae (= 3.2.0.43.51) but 3.2.0.41.49 is to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-41-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by feddozz on 2013-05-19
OK it looks like i have found the problem. i run out of inodes although i don't know what they are

```

sudo df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1       610800 609534    1266  100% /
udev            190011    504  189507    1% /dev
tmpfs           191838    422  191416    1% /run
none            191838      3  191835    1% /run/lock
none            191838      4  191834    1% /run/shm
/dev/sda6      1718848  13695 1705153    1% /home

```

Any help?

---

### Post by feddozz on 2013-05-21
I managed to reduce the usage of inodes to 44% using the following 
```
 for i in `find . -type d `; do echo `ls -a $i | wc -l` $i; done | sort -n  
```
I run it first on the root folder /, then i run it in the folder with the largest numer of files 
Is 44% a reasonable level? Or should i keep looking for files to delete. My problem is that I don't know what's needed and what's not.

---

### Post by feddozz on 2013-05-22
here it is

Could you please help?

```

sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-41-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

```
```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-generic-pae
The following packages will be upgraded:
  linux-headers-generic-pae
1 upgraded, 0 newly installed, 0 to remove and 55 not upgraded.
1 not fully installed or removed.
Need to get 0 B/2,478 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-41-generic-pae; however:
  Package linux-headers-3.2.0-41-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                               Errors were encountered while processing:
 linux-headers-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

---

### Post by HiImTye on 2013-05-22
use:
```

sudo apt-get dist-upgrade

```
or install that package directly:
```
dpkg -i linux-headers-3.2.0-41-generic-pae
```
then continue

---

### Post by feddozz on 2013-05-23
ok solved i installed two missing packages and now is all ok. Thanks to all
How do I mark the post as solved?

---

### Post by eddymo on 2013-05-25
I too have the same problem what exactly did you finally do?

Thanks

Ed

---

### Post by feddozz on 2013-05-28
> **eddymo said:**
> I too have the same problem what exactly did you finally do?

Thanks

Ed

Which problem do you exactly  have?

---

### Post by eddymo on 2013-06-01
> **feddozz said:**
> Which problem do you exactly  have?

Thanks for the reply; unmet dependencies, disk-full  I fixed it by increasing root  disk space then running apt-get - f install.

Ed

---

### Post by AgentZ86 on 2013-06-01
Unpacking linux-headers-3.2.0-41-generic-pae (from .../linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.2.0-41-generic-pae/include/config/i2o/lct/notify': No space left on device
No apport report written because the error message indicates a disk full error


OUCH it sort of says it all right here in your initially posted errors

But great you got it worked out

Happy hacking

---

