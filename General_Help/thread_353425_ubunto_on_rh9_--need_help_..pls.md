---
title: "ubunto on rh9 --need help ..pls"
date: 2007-02-04
forum: General Help
---

### Post by ishwar on 2007-02-04
hi ,
i am using rh9 with win xp already on my system  - dual boot( laptop) , i decided to upgrade my laptop with ubuntu 6.10 instead of rh9, so i downloaded the iso files from the ubuntu website using my rh9, and i wrote the file into a disk and everthing went alright , except that the disk is not booting! 

i would like to know how to cheack the integrity of the iso immage files which i downloaded in the rh9 terminal. and how can i cheack weather its right or wrong!!

is it easy to take of rh9 and upgrade to ubuntu if the disk works properly? , 

pls help me, i m very new to linux but love to work in linux its wonderful.. i have been using rh9 for more than 6 month , i could make it work for all my applications(i upgrade using yum and find the patches and deps). but i find ubuntu interesting since its for the begginers, 

my system specs!
40gig HD<
intel -centrino processory (1.6 ghz)
512 ram, i have already done my partion 20gig approx for each. system is working very well as of now! every hardware was recognized without any problem when i installed rh9, so i assume ubuntu will do the same. 
 if any one can help it will be great

thank you:(

---

### Post by taurus on 2007-02-04
You can run this command to check the ISO file before you burn it.

```
md5sum **filename.iso**
```

And make sure you burn it as image file, not data file.  In other words, if you insert the CD into the drive, you would see a bunch of files and directories instead of one big file.

Then, set your BIOS to boot from the CD first instead of the harddrive.

---

### Post by ishwar on 2007-02-04
hi i did use this command !! thanx  a lot,, 
this is the output

[root@localhost ubuntu]# ls
ubuntu-6.10-desktop-i386.iso
[root@localhost ubuntu]# md5sum ubuntu*.iso
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso

is it the right or is it ready to be written on a disk, i already wasted one(which is not booting !),, so i like  to be extra careful before i burn another! 

where can i cheak that . 

thank you for the suggestions. :)

---

### Post by taurus on 2007-02-04
Looks good to me.

```

283158c7da8c0ada74502794fa8745eb  ubuntu-6.10-alternate-amd64.iso
549ef19097b10ac9237c08f6dc6084c6  ubuntu-6.10-alternate-i386.iso
5717dd795bfd74edc2e9e81d37394349  ubuntu-6.10-alternate-powerpc.iso
99c3a849f6e9a0d143f057433c7f4d84  ubuntu-6.10-desktop-amd64.iso
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso
a3494ff33a3e5db83669df5268850a01  ubuntu-6.10-desktop-powerpc.iso
2f44a48a9f5b4f1dff36b63fc2115f40  ubuntu-6.10-server-amd64.iso
cd6c09ff8f9c72a19d0c3dced4b31b3a  ubuntu-6.10-server-i386.iso
6f165f915c356264ecf56232c2abb7b5  ubuntu-6.10-server-powerpc.iso
4971edddbfc667e0effbc0f6b4f7e7e0  ubuntu-6.10-server-sparc.iso

```

---

### Post by ishwar on 2007-02-04
hi thank you for this very fast replies,, 

but still its been a strugle.. i have been working on it. if u r there can u pls have a look at my problem!

i m trying to burn the iso to a disk, for that i need a porgrame , i m trying to install k3b on my rh9.. again dep problems is killing me! i upgraged my yum.. now i m trying to edit my yum.conf file.. all in vein.. can you pls suggest me any command which can do the job through terminal. i am actually determined to make ubuntu work on my sys..tonight!.. sorry to bother u though ..
and its great to get some one helping me like this

i wish to do the same once i learn stuff .. 


thank u again,, i am really impressed.

---

### Post by taurus on 2007-02-04
RedHat 9 is really old.  If you can't install or get k3b to run, try xcdroast.  Again, what's the problem with installing k3b?

```
yum install k3b
```

---

### Post by ishwar on 2007-02-04
hi
this is the problem
[root@localhost rpm]# rpm -ivh --force k3b-0.12.16-0.1.rh9.kde.i386.rpm
warning: k3b-0.12.16-0.1.rh9.kde.i386.rpm: V3 DSA signature: NOKEY, key ID ff6382fa
error: Failed dependencies:
        libkwalletclient.so.1 is needed by k3b-0.12.16-0.1.rh9.kde
        libmusicbrainz.so.4 is needed by k3b-0.12.16-0.1.rh9.kde
        libsamplerate.so.0 is needed by k3b-0.12.16-0.1.rh9.kde
        libsamplerate.so.0(libsamplerate.so.0.0) is needed by k3b-0.12.16-0.1.rh9.kde
        libtag.so.1 is needed by k3b-0.12.16-0.1.rh9.kde
i dont know how to yum these dependencies..


if i try to install using yum this is what happening
[root@localhost rpm]# ls
gcc-3.2.2-5.i386.rpm                      mplayerplug-in-2.50-9.i386.rpm
gftp-2.0.14-2.2.legacy.i386.rpm           opera-9.10-20061214.1-static-qt.i386-en.rpm
i like the way u look.mp3                 r1live.ram
install_flash_player_7_linux              RealPlayer10GOLD.bin
install_flash_player_7_linux.tar.gz       skype-1.3.0.37-1.i386.rpm
k3b-0.12.16-0.1.rh9.kde.i386.rpm          ubuntu
kernel-ntfs-2.4.20-31.9.i386.rpm          xine-0.99.4-5.rh9.rf.i386.rpm
kernel-ntfs-2.4.20-31.9.i686.rpm          yum-2.0.4-1.rh.fr.i386.rpm
mozilla-swfdec-0.3.1-1.1.fc1.fr.i386.rpm  yum-2.0.5-1.noarch.rpm
mplayer-1.0-0.20.pre7.0.rh9.rf.i386.rpm
[root@localhost rpm]# yum install k3b-0.12.16-0.1.rh9.kde*
Gathering header information file(s) from server(s)
Server: Red Hat Linux 9 - i386 - Base
Server: Red Hat Linux 9 - Updates
Finding updated packages
Downloading needed headers
Cannot find a package matching k3b-0.12.16-0.1.rh9.kde.i386.rpm
No actions to take
so i dont know what to do!

---

### Post by taurus on 2007-02-04
If you want to download and install the rpm, then you need to download and install all the dependencies first.  What happens if you run this command from a terminal, as root?

```
yum install k3b
```

---

### Post by ishwar on 2007-02-04
i force installed k3b !! but its not working,,

any ways the dependencies which i need were
[root@localhost rpm]# rpm -Uvh k3b*
warning: k3b-0.12.16-0.1.rh9.kde.i386.rpm: V3 DSA signature: NOKEY, key ID ff6382fa
error: Failed dependencies:
        libkwalletclient.so.1 is needed by k3b-0.12.16-0.1.rh9.kde
        libmusicbrainz.so.4 is needed by k3b-0.12.16-0.1.rh9.kde
        libsamplerate.so.0 is needed by k3b-0.12.16-0.1.rh9.kde
        libsamplerate.so.0(libsamplerate.so.0.0) is needed by k3b-0.12.16-0.1.rh9.kde
        libtag.so.1 is needed by k3b-0.12.16-0.1.rh9.kde
and if i tried thru yum

 yum install k3b-0.12.16-0.1.rh9.kde.i386.rpm
Gathering header information file(s) from server(s)
Server: Red Hat Linux 9 - i386 - Base
Server: Red Hat Linux 9 - Updates
Finding updated packages
Downloading needed headers
Cannot find a package matching k3b-0.12.16-0.1.rh9.kde.i386.rpm

so i dont know really what shld i do! is there any way i could resolve my dep's using yum.. resolve dep is not working in my yum! i tried it!

can u pls suggest me any command which can work in the terminal, that will solve most of my problems
thank u again!

---

### Post by taurus on 2007-02-04
Okay, let's try to get this clear up a little.  The command that I have described has nothing to do with the rpm that you have downloaded.  I am trying to see if you can install k3b using yum, not forcing it with rpm.

So, can you just run this command from a terminal and post the output here?

```
yum install k3b
```

---

### Post by ishwar on 2007-02-04
> **taurus said:**
> Okay, let's try to get this clear up a little.  The command that I have described has nothing to do with the rpm that you have downloaded.  I am trying to see if you can install k3b using yum, not forcing it with rpm.

So, can you just run this command from a terminal and post the output here?

```
yum install k3b
```

hi 
this is what happend
[root@localhost eswar]# yum install k3b
Gathering header information file(s) from server(s)
Server: Red Hat Linux 9 - i386 - Base
Server: Red Hat Linux 9 - Updates
Finding updated packages
Downloading needed headers
Cannot find a package matching k3b
No actions to take

---

### Post by ishwar on 2007-02-04
hi thank u for the responses,,
i got to work tomorrow.. i lost my patience.. i got to hit my bed.
gud night ,, than thanx a million for the help


will catch u tomorrow

---

### Post by ishwar on 2007-02-05
hi .. 
thax ever so much taurus! today morning when i opened my door, i found the miracle, the ubuntu cd which i orders a while ago came . so i installed it, and everything is fine, i m tasting the flavours of ubuntu! 

anyways many more questions to come.. 
thanx a lot,, :guitar: cheers

---

