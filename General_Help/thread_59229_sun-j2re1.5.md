---
title: "sun-j2re1.5"
date: 2005-08-23
forum: General Help
---

### Post by z!cHz@cH on 2005-08-23
I just installed ubuntu on my notebook because its working fine for me on my desktop  
computer. I added the repositories from ubuntuguide.org but i still can't install sun-j2re1.5. I copyd the repositories from my desktop computer to my notebook but i still can't install j2re it worked for my desktop computer. 

Is the j2re packege removed from the server?

How can i fix this problem so i can install j2re1.5?

Thanks.

---

### Post by jasmuz on 2005-08-23
Delete the mirrormax.net servers on your list and add these:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

Save & close, then sudo apt-get update

sudo apt-get install j2re1.5

---

### Post by z!cHz@cH on 2005-08-23
[QUOTE=jasmuz]Delete the mirrormax.net servers on your list and add these:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

Save & close, then sudo apt-get update

sudo apt-get install j2re1.5[/QUOTE]

I tried this but i get the same problem. My laptop is connected tho the internet but it says it cant find the j2re1.5 package. I have another problem trying to install acroread. when i sudo apt-get install acroread it install version 5.10 instead of 7.

---

### Post by topolino on 2005-08-23
Hello,

I exactly face the same problems (acroread and j2re). I installed Ubuntu 5.04 2 days ago.

Is it a repository problem?

Thanks in advance for your help.

---

### Post by 4ebees on 2005-08-23
[QUOTE=topolino]Hello,

I exactly face the same problems (acroread and j2re). I installed Ubuntu 5.04 2 days ago.

Is it a repository problem?

Thanks in advance for your help.[/QUOTE]

Yup,
I have exactly the same problem as both posts describe.

I have 5.04 on my laptop and everything installed. I've just built an old PIII and installed 5.04 and am now having these problems... ???

---

### Post by z!cHz@cH on 2005-08-23
Can i install j2re another way?

I tried this already

download the RPM from java.com

alien jre-blabla.rpm

it created the DEB 

i kan install it. But if i do java --version it says command not found. 

Can someone please help solve this problem?

---

### Post by p1tst0p on 2005-08-23
Same here,

will@ubunlap:~$ sudo apt-get install j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package j2re1.5
will@ubunlap:~$

---

### Post by hagen00 on 2005-08-23
Same problem over here!!!  ](*,) 

Please, Ubuntu, fix this for us.

Enkosi

Hagen

ps When browsing to the repository listed in the guides, sun-j2sdk is there, but apt-get update does not seem to get java specifically. All the other packages in the repository (like real player etc) can be installed fine, the problem seems to be only with Java.

---

### Post by NumbSkullMD on 2005-08-23
Have you tried sudo apt-get install sun-j2re1.5 ?

:?

---

### Post by z!cHz@cH on 2005-08-23
I managed to install j2re. I will write a mini howto:

step

1) Download jre-1_5_0_04-linux-i586.bin from  [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp) to your home directory
download the Linux  (self-extracting file) not the Linux RPM (self-extracting file).

2) Open terminal

3) sudo mkdir /usr/local/java

4) cd /usr/local/java

5) sudo chmod +x /home/%username%/jre-1_5_0_04-linux-i586.bin

6) sudo /home/%username%/jre-1_5_0_04-linux-i586.bin

7) sudo ln -s jre-1_5_0_04-linux-i586.bin current

8) sudo ln -s /usr/local/java/current/bin/java /usr/local/bin/java

9) sudo gedit /etc/environment

10) add the following line at the and of the text file:
JAVA_HOME=/usr/local/java/current

11) sudo ln -s /usr/local/java/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins

note:
replace %usename% with your username.
If you followed these steps azureus and other java apps will work.
Step 11 installs the java plugin for Firefox.

---

### Post by realbt on 2005-08-23
[QUOTE=NumbSkullMD]Have you tried sudo apt-get install sun-j2re1.5 ?

:?[/QUOTE]

Maybe I'm crazy and my repos are messed (I'll gladly post my sources.list), but that package is not available.

```
root@brie:/etc/apt# apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
``` 

Am I crazy?

---

### Post by bored2k on 2005-08-23
[QUOTE=realbt]Maybe I'm crazy and my repos are messed (I'll gladly post my sources.list), but that package is not available.

```
root@brie:/etc/apt# apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
``` 

Am I crazy?[/QUOTE]
1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
3. sudo apt-get install sun-j2re1.5

---

### Post by NumbSkullMD on 2005-08-23
Here is my sources.list

```
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary main restricted
deb-src http://security.ubuntu.com/ubuntu hoary main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://us.archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary multiverse

deb http://security.ubuntu.com/ubuntu hoary-security multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security multiverse

##Kubuntu
deb http://kubuntu.org/hoary-kde342/ hoary-updates main
deb-src http://kubuntu.org/hoary-kde342/ hoary-updates main

##Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

```

```
$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
sun-j2re1.5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

Not sure why it's not working for you.

:?

---

### Post by realbt on 2005-08-23
[QUOTE=NumbSkullMD]Here is my sources.list[/QUOTE]

I tried replacing mine with yours (which was basically the same from what I could tell). This is now my sources.list. (I took out the cdrom line from yours above.)

```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary main restricted
deb-src http://security.ubuntu.com/ubuntu hoary main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://us.archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary multiverse

deb http://security.ubuntu.com/ubuntu hoary-security multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security multiverse

##Kubuntu
deb http://kubuntu.org/hoary-kde342/ hoary-updates main
deb-src http://kubuntu.org/hoary-kde342/ hoary-updates main

##Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
``` 

root@brie:/etc/apt# apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

Still no luck. I'm losing my mind!

---

### Post by bored2k on 2005-08-23
Okay just forget about the Backported Java and build yer own ! It's just as easy.

1. [https://sdlcweb2d.sun.com/ECom/EComActionServlet;jsessionid=C11696D5A896590EE0E6BF462B33D27F](https://sdlcweb2d.sun.com/ECom/EComActionServlet;jsessionid=C11696D5A896590EE0E6BF462B33D27F)
2.
Download** Linux self-extracting file   	jre-1_5_0_04-linux-i586.bin  	15.83 MB**
3.
sudo apt-get install fakeroot java-package
4.
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
5.
sudo dpkg -i *.deb (whatever the newly Sun- DEBian package is named).

---

### Post by z!cHz@cH on 2005-08-23
[QUOTE=realbt]I tried replacing mine with yours (which was basically the same from what I could tell). This is now my sources.list. (I took out the cdrom line from yours above.)

```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary main restricted
deb-src http://security.ubuntu.com/ubuntu hoary main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://us.archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary multiverse

deb http://security.ubuntu.com/ubuntu hoary-security multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security multiverse

##Kubuntu
deb http://kubuntu.org/hoary-kde342/ hoary-updates main
deb-src http://kubuntu.org/hoary-kde342/ hoary-updates main

##Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
``` 

root@brie:/etc/apt# apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

Still no luck. I'm losing my mind![/QUOTE]

you can install j2re by using the howto on the first page of this topic.

---

### Post by bored2k on 2005-08-23
[QUOTE=z!cHz@cH]you can install j2re by using the howto on the first page of this topic.[/QUOTE]
 I don't think its easier than building your own java package.

---

### Post by realbt on 2005-08-23
[QUOTE=bored2k]Okay just forget about the Backported Java and build yer own ! It's just as easy.[/QUOTE]

I know I can build my own... in fact, I'm going to have to so I can get j2se and eclipse up and running nicely. That's fine. But it's not the point.

I'm more concerned about why I can't fetch it from the repository. I seem to be having [other conflicts](http://ubuntuforums.org/showthread.php?t=59180)  and I'm wondering whether something is screwed up.

---

### Post by NumbSkullMD on 2005-08-23
Did you run "sudo apt-get update" to make sure all the repository packages were fetched.

:?

---

### Post by hod139 on 2005-08-23
[QUOTE=z!cHz@cH]I tried this but i get the same problem. My laptop is connected tho the internet but it says it cant find the j2re1.5 package. I have another problem trying to install acroread. when i sudo apt-get install acroread it install version 5.10 instead of 7.[/QUOTE]

Are you running AMD64?  acroread and sun jre have not been ported yet.

---

### Post by realbt on 2005-08-23
[QUOTE=NumbSkullMD]Did you run "sudo apt-get update" to make sure all the repository packages were fetched.[/QUOTE]

Yup!

```
root@brie:/etc/apt# cat sources.list
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary main restricted
deb-src http://security.ubuntu.com/ubuntu hoary main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://us.archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary multiverse

deb http://security.ubuntu.com/ubuntu hoary-security multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security multiverse

##Kubuntu
deb http://kubuntu.org/hoary-kde342/ hoary-updates main
deb-src http://kubuntu.org/hoary-kde342/ hoary-updates main

##Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
root@brie:/etc/apt# apt-get update
Get:1 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Ign http://kubuntu.org hoary-updates Release.gpg
Get:3 http://archive.ubuntu.com hoary-backports Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Get:4 http://security.ubuntu.com hoary Release.gpg [189B]
Get:5 http://security.ubuntu.com hoary-security Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Hit http://us.archive.ubuntu.com hoary Release
Ign http://kubuntu.org hoary-updates Release
Get:6 http://archive.ubuntu.com hoary-backports Release [11.3kB]
Hit http://security.ubuntu.com hoary Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Get:7 http://us.archive.ubuntu.com hoary-updates Release [16.8kB]
Ign http://kubuntu.org hoary-updates/main Packages
Get:8 http://security.ubuntu.com hoary-security Release [16.9kB]
Ign http://kubuntu.org hoary-updates/main Sources
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://kubuntu.org hoary-updates/main Packages
Hit http://archive.ubuntu.com hoary-backports/main Packages
Get:9 http://ubuntu-backports.mirrormax.net hoary-backports/main Packages [24.3kB]
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary/multiverse Packages
Hit http://us.archive.ubuntu.com hoary/multiverse Sources
Hit http://kubuntu.org hoary-updates/main Sources
Hit http://security.ubuntu.com hoary/main Packages
Hit http://security.ubuntu.com hoary/restricted Packages
Hit http://security.ubuntu.com hoary/main Sources
Hit http://security.ubuntu.com hoary/restricted Sources
Hit http://archive.ubuntu.com hoary-backports/universe Packages
Hit http://archive.ubuntu.com hoary-backports/multiverse Packages
Hit http://archive.ubuntu.com hoary-backports/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://security.ubuntu.com hoary-security/multiverse Packages
Hit http://security.ubuntu.com hoary-security/multiverse Sources
Get:10 http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages [36.2kB]
Get:11 http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages [438B]
Get:12 http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages [381B]
Get:13 http://ubuntu-backports.mirrormax.net hoary-extras/main Packages [2490B]
Get:14 http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages [2411B]
Get:15 http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages [33B]
Get:16 http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages [4885B]
Fetched 117kB in 2s (42.6kB/s)
Reading package lists... Done
root@brie:/etc/apt# apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
```

---

### Post by realbt on 2005-08-23
[QUOTE=hod139]Are you running AMD64?  acroread and sun jre have not been ported yet.[/QUOTE]

Nope.

Linux brie 2.6.10-5-686 #1 Thu Aug 18 22:39:14 UTC 2005 i686 GNU/Linux

---

### Post by N8MAN1068 on 2005-08-23
GOLDEN.

Thank you for documenting this.

 \\:D/

---

### Post by beaners on 2005-08-23
i'm having the same problem as realbt.  does anyone know what to do about this?  i've tried several different ways to install and the error code is always similar, either couldn't find package, or file does not exist.  if anyone figures this out, please pass the solution along to me.

---

### Post by loon on 2005-08-23
Can't apt-get either.

Neverhad a problem till recently.

When will the be fixed or does anyone know why it was removed?

---

### Post by 4ebees on 2005-08-23
Hi all,

I've tried the two sources.list files that have been suggested and neither have been succesful.

I've used the sources.list from my laptop - which I installed not long ago  - and that's not working either.

More grist for the mill (for those who are kindly working out this problem in the repositories) :)

---

### Post by Koba on 2005-08-24
> **bored2k]Okay just forget about the Backported Java and build yer own ! It's just as easy.

1. [url]https://sdlcweb2d.sun.com/ECom/EComActionServlet said:**
> 
2.
Download** Linux self-extracting file   	jre-1_5_0_04-linux-i586.bin  	15.83 MB**
3.
sudo apt-get install fakeroot java-package
4.
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
5.
sudo dpkg -i *.deb (whatever the newly Sun- DEBian package is named).
 ok first of all, bored2k, thank you soooooo much, i did exactly what you said, i got jre installed, and now i can use limewire, THANKS DUDE YOU ROCK!!!

---

### Post by bored2k on 2005-08-24
[QUOTE=Koba]ok first of all, bored2k, thank you soooooo much, i did exactly what you said, i got jre installed, and now i can use limewire, THANKS DUDE YOU ROCK!!![/QUOTE]
 Heh, glad someone found use for my words :=). You're using Limewire ? Remember, piracy is bad for your soul .. *hides Azureus* ;).

Rock on

---

### Post by Koba on 2005-08-24
[QUOTE=bored2k]Heh, glad someone found use for my words :=). You're using Limewire ? Remember, piracy is bad for your soul .. *hides Azureus* ;).

Rock on[/QUOTE]
 haha, yeah limewire is my friend, i would use bit torrent more often, but it seems everybody has thier seeds turned off, i can't barely ever get a working download for naruto episodes... but yeah, while we are in this topic, i will avoid creating a whole new thread, is there an easy way to access executables in wine? because there are spaces in some of the windows folders, and i can't access those with console...

---

### Post by 4ebees on 2005-08-24
[QUOTE=z!cHz@cH]I managed to install j2re. I will write a mini howto:

step

1) Download jre-1_5_0_04-linux-i586.bin from  [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp) to your home directory
download the Linux  (self-extracting file) not the Linux RPM (self-extracting file).

2) Open terminal

3) sudo mkdir /usr/local/java

4) cd /usr/local/java

5) sudo chmod +x /home/%username%/jre-1_5_0_04-linux-i586.bin

6) sudo /home/%username%/jre-1_5_0_04-linux-i586.bin

7) sudo ln -s jre-1_5_0_04-linux-i586.bin current

8) sudo ln -s /usr/local/java/current/bin/java /usr/local/bin/java

9) sudo gedit /etc/environment

10) add the following line at the and of the text file:
JAVA_HOME=/usr/local/java/current

11) sudo ln -s /usr/local/java/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins

note:
replace %usename% with your username.
If you followed these steps azureus and other java apps will work.
Step 11 installs the java plugin for Firefox.[/QUOTE]


Hey z!cHz@cH,

Other than not being able to pronounce your name :) the instructions in your post worked for me first time. Thanks for that, very much appreciated.

Can I add a comment that it's not clear that the downloaded Java file needs to copied to the /java directory. Other than that, it was of great help.

A very helpful contribution from another helpful Ubuntu community member.

---

### Post by bored2k on 2005-08-24
[QUOTE=Koba]haha, yeah limewire is my friend, i would use bit torrent more often, but it seems everybody has thier seeds turned off, i can't barely ever get a working download for naruto episodes... but yeah, while we are in this topic, i will avoid creating a whole new thread, is there an easy way to access executables in wine? because there are spaces in some of the windows folders, and i can't access those with console...[/QUOTE]
 Actually, create a new thread. We dont like going off topic.

And Naruto eh ? drop the Otakus a line at [http://www.ubuntuforums.org/showthread.php?p=315936&highlight=otaku#post315936](http://www.ubuntuforums.org/showthread.php?p=315936&highlight=otaku#post315936) . We could help you with bittorrent

---

### Post by z!cHz@cH on 2005-08-24
[QUOTE=4ebees]Hey z!cHz@cH,

Other than not being able to pronounce your name :) the instructions in your post worked for me first time. Thanks for that, very much appreciated.

Can I add a comment that it's not clear that the downloaded Java file needs to copied to the /java directory. Other than that, it was of great help.

A very helpful contribution from another helpful Ubuntu community member.[/QUOTE]

It will install java in the directory your in without copy it. But still great it worked for you. Bored2k wrote a few lines about building your own java.deb in this topic this might come handy in the future.

---

### Post by dutler on 2005-08-24
OK, after reading a baker's dozen or so threads on JRE problem and that may more attempts of installing java on my computer, I give.

When install is attempted, I get the following return:
> dutler@nena:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

My sources.list is updated and I have tried several versions of it.
I sudo apt-get update after each sources.list mod
> #deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

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
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multive 

I have also followed two differnt mini how tos to man build instead of the rep and have tried several fresh installs in case i had realy buggered things up.

Any ideas? Im stucker than stuck

---

### Post by topolino on 2005-08-24
First of all, thanks to all for ur solutions and workarounds.

But still I do not understand why I cannot find the j2re package in the repositories.
Was it removed or is there another problem with my repositories' list?

Here it is:

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
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

I also tried the mirrormax backports without any success.

topolino

---

### Post by chiefofthejojos on 2005-08-24
here's why it's broken.  java usually comes in the hoary-extras restricted reposityory ([http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/)](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/)). you can see sun-j2re1.5 and sun-j2sdk1.5 in the list there.  But if you open Packages.gz (dated August 24th) you will see that they aren't in there.
So, if somebody has an old Packages.gz with entries for java we could just add them to our local copy with:
gedit /var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages

Can anyone who sees java in their synaptic check their local packages file for the hoary-extras restricted repository to see if it has entries for sun-j2re1.5 and sun-j2sdk1.5?  :D

---

### Post by topolino on 2005-08-24
Thanks for the explanation!

It is always better to clearly understand what the problem is.

topolino

---

### Post by loon on 2005-08-25
[QUOTE=chiefofthejojos]here's why it's broken.  java usually comes in the hoary-extras restricted reposityory ([http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/)](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/)). you can see sun-j2re1.5 and sun-j2sdk1.5 in the list there.  But if you open Packages.gz (dated August 24th) you will see that they aren't in there.
So, if somebody has an old Packages.gz with entries for java we could just add them to our local copy with:
gedit /var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages

Can anyone who sees java in their synaptic check their local packages file for the hoary-extras restricted repository to see if it has entries for sun-j2re1.5 and sun-j2sdk1.5?  :D[/QUOTE]


Package: sun-j2re1.5
Version: 1.5.0+update04
Priority: optional
Section: non-free/devel
Maintainer: Ubuntu Backports Project <ubuntu-bp-devel@googlegroups.com>
Depends: libasound2 (>> 1.0.8), libc6 (>= 2.3.2.ds1-4), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxi6 | xlibs (>> 4.1.0), libxp6 | xlibs (>> 4.1.0), libxt6 | xlibs (>> 4.1.0), libxtst6 | xlibs (>> 4.1.0)
Recommends: netbase, libx11-6 | xlibs, libasound2, libgtk1.2
Provides: java-common, java-virtual-machine, java-runtime, java2-runtime, java-browser-plugin, j2re1.5
Replaces: sun-j2re1.5debian
Architecture: i386
Filename: dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update04_i386.deb
Size: 30546754
MD5sum: 07cab880de48d0c3605d70c1e3e3f467
Description: Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
 The Java(TM) 2 Runtime Environment contains the Java virtual machine,
 runtime class libraries, and Java application launcher that are
 necessary to run programs written in the Java progamming language
 (this includes the Java 2 Plug-In for Netscape and Mozilla
 browsers). It is not a development environment and doesn't contain
 development tools such as compilers or debuggers. For development
 tools, see the Java 2 SDK, Standard Edition.
 .
 This package has been automatically created with java-package (0.23).
installed-size: 86996

Package: sun-j2sdk1.5
Version: 1.5.0+update04
Priority: optional
Section: non-free/devel
Maintainer: Ubuntu Backports Project <ubuntu-bp-devel@googlegroups.com>
Depends: libasound2 (>> 1.0.8), libc6 (>= 2.3.2.ds1-4), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxi6 | xlibs (>> 4.1.0), libxp6 | xlibs (>> 4.1.0), libxt6 | xlibs (>> 4.1.0), libxtst6 | xlibs (>> 4.1.0)
Recommends: netbase, libx11-6 | xlibs, libasound2, libgtk1.2
Provides: java-common, java-virtual-machine, java-runtime, java2-runtime, java-browser-plugin, java-compiler, java2-compiler, j2sdk1.5, j2re1.5
Replaces: sun-j2sdk1.5debian
Architecture: i386
Filename: dists/hoary-extras/restricted/binary-i386/sun-j2sdk1.5_1.5.0+update04_i386.deb
Size: 65229566
MD5sum: ca9bb9a5babac4ae1fceba6de1808f2a
Description: Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM)
 The Java(TM) 2 SDK is a development environment for building
 applications, applets, and components that can be deployed on the
 Java platform.
 .
 The Java(TM) 2 SDK software includes tools useful for developing and
 testing programs written in the Java programming language and running
 on the Java platform. These tools are designed to be used from the
 command line. Except for appletviewer, these tools do not provide a
 graphical user interface.
 .
 This package has been automatically created with java-package (0.23).
installed-size: 140468


this is in my listings.

edit:  and of course, please replace the  :cool: with 8 )  [with no space]

---

### Post by chiefofthejojos on 2005-08-25
Thanks!  So now, those of us with the bad version have two simple solutions:
1.  Change the packages file for hoary-extras restricted in /var/lib/apt/lists/ and add the java entries after realplayer and before transcode.  Then, without doing a apt-get update, run apt-get install for sun-j2re1.5 and/or sun-j2sdk1.5.
2.  Download the .deb files from [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/) (if you're not on i386, find the appropriate architecture) and run:
dpkg -i *debfilename*.deb
I already followed chose number 2 because I didn't want to wait anymore.

---

### Post by indygreen on 2005-08-25
i'm finding that there are lots of problems within the repositories, at the moment.  i've been unable to install many, many packages after recently rebuilding my laptop.

---

### Post by chiefofthejojos on 2005-08-25
which other ones are you having problems with?
I'm currently rebuilding my laptop as well, but the only ones I've had trouble with so far are the java packages.  Thankfully, all the video codecs are there.
Actually, I did have a problem with acroread getting version 5 instead of 7 but I just manually downloaded the deb from mirrormax as I did with java.

---

### Post by realbt on 2005-08-25
[QUOTE=chiefofthejojos]which other ones are you having problems with?
I'm currently rebuilding my laptop as well, but the only ones I've had trouble with so far are the java packages.  Thankfully, all the video codecs are there.
Actually, I did have a problem with acroread getting version 5 instead of 7 but I just manually downloaded the deb from mirrormax as I did with java.[/QUOTE]

Glad I'm not the only one!

I'm having a problem getting Samba properly installed -- seems there's a conflict. Not sure if this is related or not though. Other people are having the same problem in this thread: [http://ubuntuforums.org/showthread.php?t=59180](http://ubuntuforums.org/showthread.php?t=59180)

---

### Post by Marshalus on 2005-08-25
I'm having the same problems on a fresh install as well, I have both backport servers my source file, and can't find it anywhere. I would perfer not to install it manually, I hope Ubuntu fixes this soon.

---

### Post by skatedawe on 2005-08-25
haha. Im almost crying, :(.  :) 

 I have some reeeealy bad memories of java-installations. I havent get it worked with firefox too. Now i even't got it installed yet.
 
 ( I haven't figurit out yet. )

 I've dont all the extra [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories).

 I've read like 10 threads, i can't get anything out from it. I've tried evrything.

 ```
Sudo apt-get install sun-j2re1.5
```

 I get this; 
 
 ```
Läser paketlistor... Färdig
Bygger beroendeträd... Färdig
E: Kunde inte hitta paketet sun-j2re1.5
``` 

 Im going nuts. haha.  ](*,) 

 I thought ubuntu would make me happy.  :)  Plz. help.

---

### Post by positive waves on 2005-08-25
I am also having problems with installing sun java. 

If one of you kind souls who have it working could tell us exactly which folder to put the sun jre---.bin file into, so the root terminal could find it easily,, and if any other steps need to be done before we try to do it that would help alot...

I've tried both the 1st page instructions from z! and the fakeroot istructions from bored2k, and arrive at the same place, couldn't find ...(in the fakeroot case it was
"couldn't find java-package. :mad: :???:

---

### Post by chiefofthejojos on 2005-08-25
I think the easiest way is to download java here:
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update04_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update04_i386.deb)
and type:
dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb

If you're using amd64 or powerpc, change the i386 part of the url to amd64 or powerpc.

---

### Post by mallternative on 2005-08-25
[QUOTE=chiefofthejojos]I think the easiest way is to download java here:
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update04_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update04_i386.deb)
and type:
dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb

If you're using amd64 or powerpc, change the i386 part of the url to amd64 or powerpc.[/QUOTE]

That worked for me! Firefox plugin too! Thanks for the pointer!

---

### Post by positive waves on 2005-08-26
Thanks for the easy step!

After I figured out that it has to be in the /home folder,   
it looks like it actually worked!  \\:D/ WooHoo!

Here's what happened:

Selecting previously deselected package sun-j2re1.5.
(Reading database ... 58151 files and directories currently installed.)
Unpacking sun-j2re1.5 (from sun-j2re1.5_1.5.0+update04_i386.deb) ...
Setting up sun-j2re1.5 (1.5.0+update04) ...

Does this look like it worked, or is there something else that needs to happen here?

---

### Post by chiefofthejojos on 2005-08-26
to check that java is installed simply run:
java -version
and you should see something like this:
```
ubuntu@ubuntu:~/playpen$ java -version
java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) Client VM (build 1.5.0_04-b05, mixed mode, sharing)
``` 

and to check that the firefox plugin is installed correctly, just type:
about:plugins
in the address bar and java should be listed there.

---

### Post by ekravche on 2005-08-26
[QUOTE=chiefofthejojos]I think the easiest way is to download java here:
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update04_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update04_i386.deb)
and type:
dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb

If you're using amd64 or powerpc, change the i386 part of the url to amd64 or powerpc.[/QUOTE]

Great this solution worked like a charm. Thank you

---

### Post by positive waves on 2005-08-26
Yep, it checks out...Thanks !

---

### Post by FLeiXiuS on 2005-08-26
Just be sure you have all of the repositories.  The backports for me are always slow, I'm currently using:
```
deb http://acm.cs.umn.edu/ubp/ hoary-extras main universe multiverse restricted
```

apt-get update; apt-get install sun-j2re1.5

---

### Post by homekorva on 2005-08-26
is there guide howto get javac work in unbuntu?

---

### Post by skatedawe on 2005-08-26
[QUOTE=chiefofthejojos]I think the easiest way is to download java here:
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update04_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update04_i386.deb)
and type:
dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb

If you're using amd64 or powerpc, change the i386 part of the url to amd64 or powerpc.[/QUOTE]

 Thank you so much for your support. You dont understand how much this meant to me.

 I did as you said + "sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins"

   :grin:

---

### Post by bonjun on 2005-08-26
[QUOTE=z!cHz@cH]I managed to install j2re. I will write a mini howto:

step

1) Download jre-1_5_0_04-linux-i586.bin from  [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp) to your home directory
download the Linux  (self-extracting file) not the Linux RPM (self-extracting file).

2) Open terminal

3) sudo mkdir /usr/local/java

4) cd /usr/local/java

5) sudo chmod +x /home/%username%/jre-1_5_0_04-linux-i586.bin

6) sudo /home/%username%/jre-1_5_0_04-linux-i586.bin

7) sudo ln -s jre-1_5_0_04-linux-i586.bin current

8) sudo ln -s /usr/local/java/current/bin/java /usr/local/bin/java

9) sudo gedit /etc/environment

10) add the following line at the and of the text file:
JAVA_HOME=/usr/local/java/current

11) sudo ln -s /usr/local/java/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins

note:
replace %usename% with your username.
If you followed these steps azureus and other java apps will work.
Step 11 installs the java plugin for Firefox.[/QUOTE]
 this works for me...

thanks z!cHz@cH

---

### Post by hod139 on 2005-08-26
[QUOTE=homekorva]is there guide howto get javac work in unbuntu?[/QUOTE]

You'll want to install sun-j2sdk1.5, not the jre.  That will install Sun's development kit, which includes javac (along with all the other development tools).

---

### Post by chiefofthejojos on 2005-08-26
homekorva, just take my guide and change the "sun-j2re"s to "sun-j2sdk"s liks so:

download the sdk here:
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/sun-j2sdk1.5_1.5.0+update04_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/sun-j2sdk1.5_1.5.0+update04_i386.deb)
find it in terminal and type:
dpkg -i sun-j2sdk1.5_1.5.0+update04_i386.deb

If you're using amd64 or powerpc, change the i386 part of the url to amd64 or powerpc.

---

### Post by chiefofthejojos on 2005-08-26
[QUOTE=skatedawe] I did as you said + "sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins"[/QUOTE]

That's odd, I thouth my java plugin was installed without needing to do that.  :?

---

### Post by homekorva on 2005-08-26
thanks hod139 and chiefofthejojos.
no I can start again make some code. \\:D/

---

### Post by sjmoore on 2005-08-26
[QUOTE=z!cHz@cH]I managed to install j2re. I will write a mini howto:
7) sudo ln -s jre-1_5_0_04-linux-i586.bin current

[/QUOTE]

Thanks, helped me get this setup, spotted a typo tho.

Step 7 should be

7) *** sudo ln -s jre1.5.0_04/ current*** 

Also for some reason the AMD64 release doesn't appear to have any plugins!  ](*,)

---

### Post by Nego on 2005-08-27
I read through the post, but it doesnt seem like the original problem was fixed. I can't download TONS of stuff off apt-get, I'm using the repositories off [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) and I have done apt-get update. It doesnt find any of the packages I want, even when I do a smart upgrade it doesnt find them. Has this been fixed? THIS IS DRIVING ME NUTS!  ](*,)

---

### Post by Muffe on 2005-08-27
I also have alaptop with a fresh Ununtu install, and have all the same problems as you have.

---

### Post by Muffe on 2005-08-27
I also have a laptop with a fresh Ubuntu install, and cannot instal all the packages that I know are in the repositories.

---

### Post by Muffe on 2005-08-27
I also have a laptop with a fresh Ubuntu install, and cannot instal all the packages that I know are in the repositories... Very annoying.

---

### Post by Muffe on 2005-08-27
I also have a laptop with a fresh Ubuntu install, and the same problems with apt-get as described previously. Verry annoying.

---

### Post by Muffe on 2005-08-27
I also have a PC (Acer Travelmate 3000) with a fresh Ununtu install, and cannot get all the repositories working. Anyone found a solution yet?

---

### Post by hagen00 on 2005-08-29
Just a final note on this. It seems the backports are working again. So before any of you try the other solutions, just put the normal ubuntu backports into your sources.list. 
```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by h17m4n on 2005-09-02
So I got java installed following z!cHz@cH's howto:
> x@ubuntu:~$ java -version
java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_04-b05, mixed mode)

But I can't follow step 11: > sudo ln -s /usr/local/java/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins

The plug-in is not there, and I'm using the AMD64 version of jre from sun's page. Also I had to replace the "current" from "/usr/local/java/current" with "jre1.5.0_04".

Any howtos on this?

---

### Post by Copter on 2005-09-24
[QUOTE=z!cHz@cH]I managed to install j2re. I will write a mini howto:

step

1) Download jre-1_5_0_04-linux-i586.bin from  [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp) to your home directory
download the Linux  (self-extracting file) not the Linux RPM (self-extracting file).

2) Open terminal

3) sudo mkdir /usr/local/java

4) cd /usr/local/java

5) sudo chmod +x /home/%username%/jre-1_5_0_04-linux-i586.bin

6) sudo /home/%username%/jre-1_5_0_04-linux-i586.bin

7) sudo ln -s jre-1_5_0_04-linux-i586.bin current

8) sudo ln -s /usr/local/java/current/bin/java /usr/local/bin/java

9) sudo gedit /etc/environment

10) add the following line at the and of the text file:
JAVA_HOME=/usr/local/java/current

11) sudo ln -s /usr/local/java/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins

note:
replace %usename% with your username.
If you followed these steps azureus and other java apps will work.
Step 11 installs the java plugin for Firefox.[/QUOTE]it worked great on my computer. thnx z!cHz@cH. aliening .rpm file was bad idea after all :).

copter :]

EDIT: h17m4n - i folowed this howto _exacly_ how it was written and it works great here.

---

### Post by Strangerdave on 2005-09-24
Just to let those in power know, I just did a fresh install and still can not get java.  I have updated the repositories and even tried some of the ones suggested here.  I will try to build it as outlined earlier, but the original problem still exits.

-SD-

---

### Post by bigears on 2005-09-30
Well, I'm still pretty new to linux and Ubuntu, but I've followed every single piece of info I've found on this site, and even others.  I still can't seem to get j2re1.5 to install properly in Breezy.  I've run across some websites that just won't load correctly using the older java.  Any progress on this topic?

---

### Post by Ubunted on 2005-09-30
1. [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)

2. Download Linux self-extracting file jre-1_5_0_04-linux-i586.bin (or whatever the file is) 15.83 MB

3.
```
sudo apt-get install fakeroot java-package
```


4.
```
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
```
or
```
fakeroot make-jpkg jre-*
```
or
```
fakeroot make-jpkg jdk-*
```


5.
```
sudo dpkg -i *.deb
```

---

### Post by bored2k on 2005-09-30
That above looks like something I'd write *LOL*.

It works. I'm sure of it ;). BTW, we already posted that here.

[http://ubuntuforums.org/showthread.php?p=315154&highlight=make-jpkg#post315154](http://ubuntuforums.org/showthread.php?p=315154&highlight=make-jpkg#post315154)
[http://ubuntuforums.org/showthread.php?t=70428&highlight=make-jpkg](http://ubuntuforums.org/showthread.php?t=70428&highlight=make-jpkg)

---

### Post by Ubunted on 2005-09-30
Just spreading the love is all.

---

