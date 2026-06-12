---
title: "keepass installation"
date: 2007-02-09
forum: General Help
---

### Post by timjay73 on 2007-02-09
just switched over yesterday and everything has gone as smooth as i expected it to. however, i installed keepass v0.2.2. it installed fine but i cant find it anywhere. i searched for it but nothing came up. i went through file folders and found stuff for it but i couldnt find anything to launch the app. then i went through command line (i think that's what we're calling it) with "keepass" and this came up:

xchech@xchech-laptop:~$ keepass
keepass: error while loading shared libraries: libQtXml.so.4: cannot open shared object file: No such file or directory
xchech@xchech-laptop:~$

so i tried something and got this:

xchech@xchech-laptop:~$ sudo apt-get install libQtXml.so.4
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libQtXml.so.4

i just tried it again and now i get this:

xchech@xchech-laptop:~$ sudo apt-get install libQtXml.so.4
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
xchech@xchech-laptop:~$

now i got nothing left. i am tapped out on searching the forums. any help would be very much appreciated. this is so fun. it's like getting on a computer for the first time again. a madonna song just popped into my head...like a virgin...sorry about that. i digress

---

### Post by timjay73 on 2007-02-11
no one? 

okay i uninstalled what i could findof keepass through synaptic. now when i go into synaptic and search for it to try to reinstall, it is nowhere to be found. i also cant install through terminal either. all of the codes i have found never work. so i'm back to square one.

here's what i've done so far:
D/Led both the application bundle v0.2.2 *and* the DEB binary package v0.2.2. 

now, from what i have read, the application bundle has everything that i need. how do i install it? i cant seem to find anyway to install it. i cant find it through terminal or synaptic (and yes i have both universe and multiverse repositories added). i am at a lost and i really need to have keepass installed/usable b/c all my p/w are saved through it. as of now, everytime i need to get somewhere i have to boot up XP, which is always a joy. 

anyone have a clue about what to do?

---

### Post by Ramses de Norre on 2007-02-11
There is a package *keepassx* in the universe repo, is that the one you're looking for? You'll have to enable universe to make aptitude or synaptic find it.

If that's not it, what format is that application bundle?

---

### Post by timjay73 on 2007-02-11
thank you so much for your help. i have added/enabled all of the repositories in synaptic>settings>repositories (software preferences) just to make sure. i searched for *keepassx* and nothing showed up. 

then i tried this:
xchech@xchech-laptop:~$ sudo apt-get install keepassx
Reading package lists... Done
Building dependency tree... Done
Package keepassx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package keepassx has no installation candidate

that's as far as i got.
the file name for the application bundle that i d/led is KeePassX-02.2-bin.tar.gz
i also d/led DEB binary package KeePassX-02.2.deb

---

### Post by Ramses de Norre on 2007-02-11
Oh now I see, the package is in edgy repos but not in dapper repos.. So I assume you are using dapper?
The best thing probably is to try installing the ubuntu deb package which you can get [here](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fk%2Fkeepassx%2Fkeepassx_0.2.2-0ubuntu1_i386.deb&md5sum=a04b19d5f44e9cfbef37bcd72d4e48d9&arch=i386&type=main).
It's possible that some dependencies can't be resolved with dapper repos, if so you can try your downloaded deb package with ```
sudo dpkg -i KeePassX-02.2.deb
``` in the directory that file is in.
And the last resort would be installing from source with the tarball.
But try the others first.

---

### Post by timjay73 on 2007-02-11
again, thank you for taking time with me. 
1. i downloaded a new keepassx from the link provided. it didnt quite install - Error:Dependency is not satisfiable:libc6

2. so then i did something that i thought/hoped would work - sudo apt-get install libc6. apparently, i already have the newest version. 

3.tried the code you provided and got this:
xchech@xchech-laptop:~$ sudo dpkg -i KeePassX-02.2.deb
dpkg: error processing KeePassX-02.2.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 KeePassX-02.2.deb
xchech@xchech-laptop:~$

---

### Post by Ramses de Norre on 2007-02-11
You need to execute that command in the directory containing the deb file or proceed the filename with the right path to it.
The dependency problems with the edgy package are normal.. I already expected them.

---

### Post by timjay73 on 2007-02-11
and how do i do that? right now the file is on my desktop. how would i write the command?

i tried this and multiple variations that i could think of but with no luck. 

sudo dpkg -i ~/Desktop/KeePassX-0.2.2.deb    ??

you're going to have to really dumb this down for me. and trust me, i need it.

---

### Post by Ramses de Norre on 2007-02-11
You still get the "*No such file or directory*" error?
Try to use tab completion more to be sure you've got the right filename and path.
So type in sudo dpkg -i ~/Desktop/ and double tab to see all available files, now check whether the deb is there too and type the first couple of letters, then press tab to complete.
That way you should have the path and filename correct.

---

### Post by timjay73 on 2007-02-11
did it just like you said and here's what i got:
xchech@xchech-laptop:~$ sudo dpkg -i /home/xchech/Desktop/KeePassX-0.2.2.deb
Password:
Selecting previously deselected package keepassx.
(Reading database ... 86216 files and directories currently installed.)
Unpacking keepassx (from .../Desktop/KeePassX-0.2.2.deb) ...
Setting up keepassx (0.2.2-2) ...
xchech@xchech-laptop:~$ keepass
keepass: error while loading shared libraries: libQtXml.so.4: cannot open shared object file: No such file or directory


i wasnt sure if it was installed b/c i couldnt find it anywhere. that's why i typed in "keepass".
now how do i get it to open or do i need to something with libQtXml.so.4? i tried installing and got this

xchech@xchech-laptop:~$ sudo apt-get install libQtXml.so.4
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libQtXml.so.4
xchech@xchech-laptop:~$

---

### Post by Ramses de Norre on 2007-02-11
```
sudo aptitude install libc6 libgcc1 libqt4-core libqt4-gui libstdc++6 libx11-6 libxtst6
```

---

### Post by llamakc on 2007-02-11
That file is provided by libqt4-core or libqt4-core-kdecopy which you would need to install.

---

### Post by timjay73 on 2007-02-11
now i get this

xchech@xchech-laptop:~$ keepass
keepass: error while loading shared libraries: libpng.so.3: cannot open shared o bject file: No such file or directory

couldnt get it installed either

---

### Post by llamakc on 2007-02-11
apt-get install libpng3

---

### Post by timjay73 on 2007-02-11
YESSSS!!! holy crap it's working great! Thank you so much. Thanks for sticking with me Ramses. also, thanks to you llamakc. that was quite a learning experience.

---

### Post by jorgedlt on 2007-06-04
After your post I was worried that I too would not be able to install the LInux version of Keepass, so I cheated I use the Synaptic GUI Admin tool on my Feisty Fawn Box, and it installed in under one minute, no issues! You might to try that approach, good luck.

---

### Post by napster86 on 2007-06-11
hey yes u cud have used synaptic or add/rem package it wud have done da job in a minute or so..u cud hve done somethin else usefull dont u think so..

---

### Post by TimeSearcher on 2007-07-11
It was very easy for me:

michael@NEO:/usr/bin$ sudo apt-get install keepassx
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libpq4 libqt4-core libqt4-gui libqt4-qt3support libqt4-sql libsqlite0
Suggested packages:
  libqt4-dev
Recommended packages:
  qt4-qtconfig
The following NEW packages will be installed:
  keepassx libpq4 libqt4-core libqt4-gui libqt4-qt3support libqt4-sql libsqlite0
0 upgraded, 7 newly installed, 0 to remove and 9 not upgraded.
Need to get 8401kB of archives.
After unpacking 20.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libsqlite0 2.8.17-0ubuntu1 [169kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libqt4-core 4.2.0-1ubuntu6 [1172kB]        
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libqt4-sql 4.2.0-1ubuntu6 [333kB]                                                        
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libqt4-qt3support 4.2.0-1ubuntu6 [1227kB]                                                
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libqt4-gui 4.2.0-1ubuntu6 [4879kB]                                                       
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libpq4 8.1.9-0ubuntu0.6.10 [209kB]                                             
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe keepassx 0.2.2-0ubuntu1 [413kB]                                                      
Fetched 8401kB in 47s (176kB/s)                                                                                                    
Preconfiguring packages ...
Selecting previously deselected package libsqlite0.
(Reading database ... 68752 files and directories currently installed.)
Unpacking libsqlite0 (from .../libsqlite0_2.8.17-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-core.
Unpacking libqt4-core (from .../libqt4-core_4.2.0-1ubuntu6_i386.deb) ...
Selecting previously deselected package libpq4.
Unpacking libpq4 (from .../libpq4_8.1.9-0ubuntu0.6.10_i386.deb) ...
Selecting previously deselected package libqt4-sql.
Unpacking libqt4-sql (from .../libqt4-sql_4.2.0-1ubuntu6_i386.deb) ...
Selecting previously deselected package libqt4-qt3support.
Unpacking libqt4-qt3support (from .../libqt4-qt3support_4.2.0-1ubuntu6_i386.deb) ...
Selecting previously deselected package libqt4-gui.
Unpacking libqt4-gui (from .../libqt4-gui_4.2.0-1ubuntu6_i386.deb) ...
Selecting previously deselected package keepassx.
Unpacking keepassx (from .../keepassx_0.2.2-0ubuntu1_i386.deb) ...
Setting up libsqlite0 (2.8.17-0ubuntu1) ...

Setting up libqt4-core (4.2.0-1ubuntu6) ...

Setting up libpq4 (8.1.9-0ubuntu0.6.10) ...

Setting up libqt4-sql (4.2.0-1ubuntu6) ...

Setting up libqt4-gui (4.2.0-1ubuntu6) ...

Setting up libqt4-qt3support (4.2.0-1ubuntu6) ...

Setting up keepassx (0.2.2-0ubuntu1) ...

michael@NEO:/usr/bin$ keepass &
[3] 30106
michael@NEO:/usr/bin$ Kpx: No Translation found for 'English (Canada)'using 'English (UnitedStates)'
Qt: No Translation found for 'English (Canada)'using 'English (UnitedStates)'


(as you can see, I had a minor problem with locale but it ran just fine).

Glad your problem seems to have been resolved...

TIMESEARCHER

---

### Post by AdamFromVancouver on 2007-10-10
Hi everyone.

I was wondering if somebody could help me get keepass working on my system.

I'm using dapper, and have downloaded the ubuntu deb file (keepassx_0.2.2-0ubuntu1_i386.deb).

When I try to install it, this is what I get:

> sudo dpkg -i keepassx_0.2.2-0ubuntu1_i386.deb
Selecting previously deselected package keepassx.
(Reading database ... 85577 files and directories currently installed.)
Unpacking keepassx (from keepassx_0.2.2-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of keepassx:
 keepassx depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.5.
 keepassx depends on libgcc1 (>= 1:4.1.1-12); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 keepassx depends on libqt4-core (>= 4.1.4); however:
  Version of libqt4-core on system is 4.1.2-1ubuntu1.
 keepassx depends on libqt4-gui (>= 4.1.4); however:
  Version of libqt4-gui on system is 4.1.2-1ubuntu1.
 keepassx depends on libstdc++6 (>= 4.1.1-12); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing keepassx (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 keepassx


I have tried using the following to update the dependencies:
> sudo aptitude install libc6 libgcc1 libqt4-core libqt4-gui libstdc++6 libx11-6 libxtst6

This is the result:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  keepassx
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  keepassx: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.5 is installed.
            Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is installed.
            Depends: libqt4-core (>= 4.1.4) but 4.1.2-1ubuntu1 is installed.
            Depends: libqt4-gui (>= 4.1.4) but 4.1.2-1ubuntu1 is installed.
            Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
keepassx

Score is -299

Accept this solution? [Y/n/q/?]


How can I get these packages up to what I need? I have run out of ideas.

---

