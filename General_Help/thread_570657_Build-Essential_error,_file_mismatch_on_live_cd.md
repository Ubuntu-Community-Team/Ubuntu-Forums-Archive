---
title: "Build-Essential error, file mismatch on live cd?"
date: 2007-10-08
forum: General Help
---

### Post by lonrot on 2007-10-08
Ubuntu 704 x64
Clean installation (yesterday)

I'm getting an error message when I try to install build-essential package which is available in the live cd.

I have tried with the following command at the terminal:
```
sudo apt-get install build-essential
```

And also at the package manager, in both cases I get the same error bellow and the installation is cancelled:

```
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-15.27_amd64.deb MD5Sum mismatch
```

Oh, and I don't have internet connection, bear with it.

---

### Post by por100pre1 on 2007-10-08
Try this:

```
gksudo software-properties-gtk
```

remove the CD form the list. Close. Insert the Cd again and try again. You may need to get another CD. :-k

---

### Post by zvacet on 2007-10-08
```
sudo apt-cdrom add
```
```
sudo aptitude install build-essential
```

---

### Post by lonrot on 2007-10-10
> **zvacet said:**
> ```
sudo apt-cdrom add
```
```
sudo aptitude install build-essential
```

```
lonrot@lonrot-desktop:~$ gksudo software-properties-gtk
lonrot@lonrot-desktop:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [3d55ae2f6d901e9f3fc593a8475333e7-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)'
Copying package lists...gpgv: Signature made Sun 15 Apr 2007 07:51:11 AM CST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
lonrot@lonrot-desktop:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7579kB of archives. After unpacking 32.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
E: Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-15.27_amd64.deb: MD5Sum mismatch
lonrot@lonrot-desktop:~$ 

```

I'll have to download another cd, the weird thing is that I just burned that CD a few days ago and even checked the burned image and no errors appeared.

Any other suggestion?

---

### Post by Lary Grant on 2007-10-23
Do:

```
gksudo software-properties-gtk
```

and uncheck the CD.

Do **not** do the "apt-cdrom" step.

Then do:```
sudo aptitude install build-essential
```

What that will do is exclude the CD as a possible source for the packages.  Once the CD is excluded, aptitude will be forced to get the package from the internet.

---

### Post by Lary Grant on 2007-10-23
Oops... I missed the fact that you don't have an internet connection... sorry.

---

### Post by ImpureAscetic on 2008-03-14
Perhaps, but that unchecking the CD option really helped me. Thanks so much, Larry.

---

