---
title: "Limewire Install"
date: 2005-06-06
forum: General Help
---

### Post by fireGrrl on 2005-06-06
Hi All,

Well I've Googled till my eyes bled and I've read everything on the forum, and I still can't get this working. I followed the Ubuntu user's guide for installing Java and Limewire to no avail. I assume it's having a problem with java. Here's what I get:
> 
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading LimeWire:

Exception during runtime initialization
java.lang.NullPointerException
   <<No stacktrace available>>
./runLime.sh: line 86: 10323 Aborted                 ${JAVA_PROGRAM_DIR}java -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. -jar LimeWire.jar

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.4.2"
gcj-4.0 (GCC) 4.0.0 20050301 (prerelease) (Debian 4.0-0pre6ubuntu7)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.




And here is my variables:

tlarrew@ubuntu:/opt/LimeWire$ java -version
java version "1.4.2"
gcj-4.0 (GCC) 4.0.0 20050301 (prerelease) (Debian 4.0-0pre6ubuntu7)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

tlarrew@ubuntu:/opt/LimeWire$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games:/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0
tlarrew@ubuntu:/opt/LimeWire$ echo $JAVA_HOME
/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0
tlarrew@ubuntu:/opt/LimeWire$ ls /usr/lib/j*
j2re1.5-sun/  j2sdk1.5-sun/ jvm/
tlarrew@ubuntu:/opt/LimeWire$ which java
/usr/bin/java



Any suggestions would be greatly appreciated!!!!
Thanks!!!

---

### Post by defkewl on 2005-06-06
Try using JDK from Sun.

---

### Post by bored2k on 2005-06-06
This gets easily solved.

1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
3. sudo apt-get install sun-j2re1.5

---

### Post by xao on 2005-06-07
Instead of Limewire I highly recommend gtk-gnutella. I cannot remember which repository it is in at the moment, but I have enjoyed it much more than Limewire..

---

### Post by bored2k on 2005-06-07
[QUOTE=xao]Instead of Limewire I highly recommend gtk-gnutella. I cannot remember which repository it is in at the moment, but I have enjoyed it much more than Limewire..[/QUOTE]
 I disagree. Limewire Pro is a very robust P2P client. I have not found one I enjoyed more to get some freebie audio files.

---

### Post by xao on 2005-06-07
well far be it from me to argue with a moderator.....

i have jsut had more luck with gtk-gnutella......

---

### Post by DarkManX4lf on 2005-06-27
[QUOTE=bored2k]This gets easily solved.

1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
3. sudo apt-get install sun-j2re1.5[/QUOTE]


i did 1. and 2. fine but when i do 3.

this is what i get


Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

---

### Post by bored2k on 2005-06-27
[QUOTE=DarkManX4lf]i did 1. and 2. fine but when i do 3.

this is what i get


Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5[/QUOTE]
 1. sudo apt-get update
2. sudo apt-get install sun-j2re1.5

I just did that. If you added the repos correctly, it should work.

---

### Post by DarkManX4lf on 2005-06-27
after editing the sources.list 

and typing sudo apt-get update

i notice it hangs a little on this

99% [Connecting to ubuntu-backports.mirrormax.net (66.90.101.204)]

maybe for a min or two and then it continues, but after that when i type

sudo apt-get install sun-j2re1.5

i get the same error, couldnt i just do this in synaptic ? i cant find this package in synaptic tho.

---

### Post by DarkManX4lf on 2005-06-27
bump

---

### Post by bored2k on 2005-06-27
[QUOTE=DarkManX4lf]bump[/QUOTE]
 Until you get 100% in the apt-get update, I don't think you'll be getting any updates. Weird that's happening to you.

---

### Post by Skel on 2005-06-28
I got limwire install seems to work well but i cant get it to go the system tray even tho the settign are on that can anyone help on this problem?

---

### Post by bored2k on 2005-06-28
[QUOTE=Skel]I got limwire install seems to work well but i cant get it to go the system tray even tho the settign are on that can anyone help on this problem?[/QUOTE]
 I just installed Java (btw, new java out) and ran it, no tweakings at all were made.

---

### Post by Skel on 2005-06-28
can u point me to this new java maybe that the issue cux its annoying as anything seeing it on my taskbar as i think you would understand :P

---

### Post by DarkManX4lf on 2005-06-28
[QUOTE=bored2k]Until you get 100% in the apt-get update, I don't think you'll be getting any updates. Weird that's happening to you.[/QUOTE]


i just reformatted-reinstalled ubuntu

after waiting a little while it does finish updating from apt-get update

but when i try,

apt-get install sun-j2re1.5 

it still shows the same error the same happens when i try

apt-get install flashplayer-mozilla, and i made sure i edited /etc/apt/sources.list before i did any of this.

---

### Post by Skel on 2005-06-28
## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe



deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main restricted universe multiverse
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main restricted universe multiverse 
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports-staging main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras-staging main universe multiverse restricted
deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/



Those are my sources list put that in and see if u can get the update i got the newest update perfect with that...



Just no try icon  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by DarkManX4lf on 2005-06-28
[QUOTE=Skel]## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe



deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main restricted universe multiverse
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main restricted universe multiverse 
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports-staging main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras-staging main universe multiverse restricted
deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/



Those are my sources list put that in and see if u can get the update i got the newest update perfect with that...



Just no try icon  ](*,)  ](*,)  ](*,)  ](*,)[/QUOTE]
 wow, even with that source list i STILL cant apt-get sun-j2re1.5, it still says

root@ubuntu:~ # apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

i dont get it...

---

### Post by DarkManX4lf on 2005-06-29
bump

---

### Post by DarkManX4lf on 2005-06-29
can anyone else type

sudo apt-get install sun-j2re1.5

and does it work ?

---

### Post by bored2k on 2005-06-29
Remove those backport mirrors and use these (this is my full sources.list):
> [SIZE=1]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
[B]
## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted[/B]
[/SIZE]
> 
reb@noir:~$ apt-cache search sun-j2re1.5
sun-j2re1.5 - Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
 There you go.

---

### Post by manicka on 2005-06-29
[QUOTE=DarkManX4lf]can anyone else type

sudo apt-get install sun-j2re1.5

and does it work ?[/QUOTE]
 It works for me

Why not try Synaptic to install it and see if there's an error there. I use the mirrormax servers and jre is there in backports. I don't use staging but here's my backports settings if it helps

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by DarkManX4lf on 2005-06-29
i have that in my sources.list, i dont nkow why it wont install.....maybe becuase ihave a amd64 version of ubuntu instlaled ?

---

### Post by arnieboy on 2005-06-29
The best way to install limewire is as follows:
install javajre as pointed out in ubuntuguide.
Then grab the latest limewire rpm from [www.limewire.com](www.limewire.com)
from a terminal go the the directory where u download it and do a :
sudo alien "limewhatever"
 this will create a deb package
then do a sudo dpkg -i "limewhatever.deb"
this will install limewire and will also create a menu item under "Internet" and limewire will work like a dream

P.S. "limewhatever" is the name of the rpm file u downloaded without quotes.

---

### Post by manicka on 2005-06-30
[QUOTE=arnieboy]The best way to install limewire is as follows:
install javajre as pointed out in ubuntuguide.
Then grab the latest limewire rpm from [www.limewire.com](www.limewire.com)
from a terminal go the the directory where u download it and do a :
sudo alien "limewhatever"
 this will create a deb package
then do a sudo dpkg -i "limewhatever.deb"
this will install limewire and will also create a menu item under "Internet" and limewire will work like a dream

P.S. "limewhatever" is the name of the rpm file u downloaded without quotes.[/QUOTE]
 Nice tip,thanks.

I'll be interested to see how this works in comparison to just downloading the tarball and running Limewire within the extracted directory

---

### Post by manicka on 2005-06-30
Worked like a charm. Thanks again :D

---

### Post by DarkManX4lf on 2005-06-30
[QUOTE=arnieboy]The best way to install limewire is as follows:
install javajre as pointed out in ubuntuguide.
Then grab the latest limewire rpm from [www.limewire.com](www.limewire.com)
from a terminal go the the directory where u download it and do a :
sudo alien "limewhatever"
 this will create a deb package
then do a sudo dpkg -i "limewhatever.deb"
this will install limewire and will also create a menu item under "Internet" and limewire will work like a dream

P.S. "limewhatever" is the name of the rpm file u downloaded without quotes.[/QUOTE]
 yea but i cant get javajre like the ubuntu guide says...

i edit my sources.list like the guide says i do a 

apt-get update

apt-get install sun-j2re1.5

and it says it cant find it....

---

### Post by arnieboy on 2005-06-30
paste the contents of ur /etc/apt/sources.list file

---

### Post by DarkManX4lf on 2005-06-30
here it is, my sources.list


deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by arnieboy on 2005-06-30
alright, ur sources.list file looks in good shape. what I would suggest u shd do is run synpatic and reload ur repositories on synaptic and then search for sun-j2re1.5.  I dont see any reason why u wont find it. Install it from synaptic and then install limewire the way I suggested. 
Also let me know if 
sudo apt-get update
from a terminal throws up any error.

---

### Post by bored2k on 2005-06-30
You could also make a debian package out of the brand new .0.4 JRE that just came out from Sun.

First sudo apt-get install fakeroot java-package, then download teh jre from the sun website. After that, simply do
fakeroot make-jpkg nameofsunpackage.bin
After that's done, sudo dpkg -i newlycreatedjavapackage.deb

Then, simply get the Limewire rpm, sudo alien -d limename.rpm , then sudo dpkg -i newlimename.deb.

---

### Post by arnieboy on 2005-06-30
will this automatically include java in ur .bashrc file? the good thing abt this backports java package was that it removes the necessity to add that extra line for java in ur PATH. I personally do not recommend creating deb packages on ur own every time u get a tarball. Dependency problems often become tantamount.

---

### Post by bored2k on 2005-06-30
[QUOTE=arnieboy]will this automatically include java in ur .bashrc file? the good thing abt this backports java package was that it removes the necessity to add that extra line for java in ur PATH. I personally do not recommend creating deb packages on ur own every time u get a tarball. Dependency problems often become tantamount.[/QUOTE]
 Yes it does. It even adds the corresponding Firefox support. I've been doing it since Warty and everything is automated. I recently stopped doing it because of the backport, but since the backport's version hasn't been updated, I've been using this one. It's harmless. So is limewire to deb install (I just did it on my Limewire Pro).

---

### Post by arnieboy on 2005-06-30
Good to know that. I have been converting the limewire rpms to debs for quite a few versions of limewire now. It's never failed me. That's why I suggested it in the first place.

---

### Post by DarkManX4lf on 2005-06-30
nope its not there, i opened synaptic and then reloaded the packages and sun-j2re1.5 is not there.

---

### Post by arnieboy on 2005-06-30
well in that case they have probably removed the jre package from backports temporarily. U can try bored2k's directions to install java on ur machine.

---

### Post by manicka on 2005-06-30
I have jre installed through an evolutioncolt script that I used the install the latest 1.04 beta. Perhaps making a script from the java install section of the script would work. i.e make a script called jreinstall.sh with this code in it then run the script with the 'sh jreinstall.sh' command in a terminal. You'll need to create directory called openoffice2 in your home folder to get this script to work - or alter the script to your liking.

```
## Stage 5: Installing the Sun JRE 1.5.0 

cd ~/openoffice2
wget -c http://frankandjacq.com/ubuntuguide/jre-1_5_0_03-linux-i586.bin
sh jre-1_5_0_03-linux-i586.bin
sudo mkdir /usr/java
sudo mv jre1.5.0_03/ /usr/java/
sudo chown -R root:root /usr/java/jre1.5.0_03/
sudo ln -s /usr/java/jre1.5.0_03/bin/java /usr/bin/java
sudo ln -s /usr/java/jre1.5.0_03/bin/java_vm /usr/bin/java_vm
sudo ln -s /usr/java/jre1.5.0_03/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/java/jre1.5.0_03/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/

echo
echo "***Finished! ***"
echo
sleep 2
```

HTH

---

### Post by bored2k on 2005-06-30
[QUOTE=manicka]I have jre installed through an evolutioncolt script that I used the install the latest 1.04 beta. Perhaps making a script from the java install section of the script would work. i.e make a script called jreinstall.sh with this code in it then run the script with the 'sh jreinstall.sh' command in a terminal. You'll need to create directory called openoffice2 in your home folder to get this script to work - or alter the script to your liking.

```
## Stage 5: Installing the Sun JRE 1.5.0 

cd ~/openoffice2
wget -c http://frankandjacq.com/ubuntuguide/jre-1_5_0_03-linux-i586.bin
sh jre-1_5_0_03-linux-i586.bin
sudo mkdir /usr/java
sudo mv jre1.5.0_03/ /usr/java/
sudo chown -R root:root /usr/java/jre1.5.0_03/
sudo ln -s /usr/java/jre1.5.0_03/bin/java /usr/bin/java
sudo ln -s /usr/java/jre1.5.0_03/bin/java_vm /usr/bin/java_vm
sudo ln -s /usr/java/jre1.5.0_03/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/java/jre1.5.0_03/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/

echo
echo "***Finished! ***"
echo
sleep 2
```

HTH[/QUOTE]
 I still prefer the debian package. It's just 3 steps:
1. Get the packages.
2. BIN to DEB
3. Install

---

### Post by DarkManX4lf on 2005-06-30
after i sudo dpkg -i newlycreatedjavapackage.deb

and the limewire deb

what do i do ?

---

### Post by DarkManX4lf on 2005-06-30
[QUOTE=bored2k]You could also make a debian package out of the brand new .0.4 JRE that just came out from Sun.

First sudo apt-get install fakeroot java-package, then download teh jre from the sun website. After that, simply do
fakeroot make-jpkg nameofsunpackage.bin
After that's done, sudo dpkg -i newlycreatedjavapackage.deb

Then, simply get the Limewire rpm, sudo alien -d limename.rpm , then sudo dpkg -i newlimename.deb.[/QUOTE]


this is what i get after i do this fakeroot make-jpkg -i jre-1_5_03-linux-i586.bin 

root@ubuntu:~/Desktop # fakeroot make-jpkg -i jre-1_5_03-linux-i586.bin make-jpkg: missing pathname
Try `make-jpkg --help' for more information.

---

### Post by bored2k on 2005-06-30
[QUOTE=DarkManX4lf]this is what i get after i do this fakeroot make-jpkg -i jre-1_5_03-linux-i586.bin 

root@ubuntu:~/Desktop # fakeroot make-jpkg -i jre-1_5_03-linux-i586.bin make-jpkg: missing pathname
Try `make-jpkg --help' for more information.[/QUOTE]
 You did
dpkg -i java.deb
dpkg -i lime.deb
Succesfully ?

Limewire should be installed. If you type limewire it should open.
Also, if you killall gnome-panel, there should be a limewire entry.

---

### Post by DarkManX4lf on 2005-06-30
[QUOTE=bored2k]You did
dpkg -i java.deb
dpkg -i lime.deb
Succesfully ?

Limewire should be installed. If you type limewire it should open.
Also, if you killall gnome-panel, there should be a limewire entry.[/QUOTE]


no i did not

---

### Post by DarkManX4lf on 2005-06-30
> Originally Posted by bored2k
You could also make a debian package out of the brand new .0.4 JRE that just came out from Sun.

First sudo apt-get install fakeroot java-package, then download teh jre from the sun website. After that, simply do
fakeroot make-jpkg nameofsunpackage.bin
After that's done, sudo dpkg -i newlycreatedjavapackage.deb

Then, simply get the Limewire rpm, sudo alien -d limename.rpm , then sudo dpkg -i newlimename.deb.

that step is after fakeroot make-jpkg nameofsunpackage.bin

---

### Post by bored2k on 2005-06-30
[QUOTE=DarkManX4lf]that step is after fakeroot make-jpkg nameofsunpackage.bin[/QUOTE]
 That's not very helpful.. what did you do exactly ?

1. Install java-package fakeroot
2. Download the jre.bin from Sun
3. fakeroot make-jpkg whatever.bin
4. sudo dpkg -i whatever.deb
5. java -v should work
6. Download limewire.rpm
7. Repeat the process.

---

### Post by DarkManX4lf on 2005-06-30
i did exactly what you said to do in  your post to install java jre

 Originally Posted by bored2k
You could also make a debian package out of the brand new .0.4 JRE that just came out from Sun.

First sudo apt-get install fakeroot java-package, then download teh jre from the sun website. After that, simply do
fakeroot make-jpkg nameofsunpackage.bin
After that's done, sudo dpkg -i newlycreatedjavapackage.deb

Then, simply get the Limewire rpm, sudo alien -d limename.rpm , then sudo dpkg -i newlimename.deb

---

### Post by bored2k on 2005-06-30
[QUOTE=DarkManX4lf]i did exactly what you said to do in  your post to install java jre

 Originally Posted by bored2k
You could also make a debian package out of the brand new .0.4 JRE that just came out from Sun.

First sudo apt-get install fakeroot java-package, then download teh jre from the sun website. After that, simply do
fakeroot make-jpkg nameofsunpackage.bin
After that's done, sudo dpkg -i newlycreatedjavapackage.deb

Then, simply get the Limewire rpm, sudo alien -d limename.rpm , then sudo dpkg -i newlimename.deb[/QUOTE]
 What's the error you get. Did you even get an error ?

---

### Post by DarkManX4lf on 2005-06-30
ok to be more clear here is what i did

sudo apt-get install fakeroot java-package


downloaded jre-1_5_0_03-linux-i586.bin

fakeroot make-jpkg jre-1_5_0_03-linux-i586.bin

but now im NOT logged in as root and i am a regular user now when i do this


fakeroot make-jpkg jre-1_5_0_03-linux-i586.bin

i get this error 

darkmanx4lf@ubuntu:~$ fakeroot make-jpkg jre-1_5_0_03-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXRWJJYX
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done




if i am logged in as root i get this error


You are real root -- unfortunately, some Java distributions have
install scripts that directly manipulate /etc, and may cause some
inconsistencies on your system. Instead, you should become a
non-root user and run:

fakeroot make-jpkg jre-1_5_0_03-linux-i586.bin

which will allow no damage to be done to your system files and
still permit the Java distribution to successfully extract.

Aborting.

---

### Post by DarkManX4lf on 2005-06-30
bump

---

### Post by zab on 2005-07-01
FYI:  our latest RPM is much more alien-friendly.  It used to have some crazy libstdc++ dependencies which are now gone.  You can get it at  [http://www9.limewire.com/beta/LimeWireLinux.rpm](http://www9.limewire.com/beta/LimeWireLinux.rpm)

---

### Post by DarkManX4lf on 2005-07-01
thanks now only to get java properly installed

---

### Post by DarkManX4lf on 2005-07-06
well i realized in order to get sun-j2re to even show up in synapitc you ned the 386/686 kernel !!!

so problem solved here.

---

