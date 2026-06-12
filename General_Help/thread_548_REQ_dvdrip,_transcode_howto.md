---
title: "REQ: dvdrip, transcode howto"
date: 2004-10-14
forum: General Help
---

### Post by rupert on 2004-10-14
Hi,
can someone make an installationhowto for the dvdrip package.
I tried to install it but get the following message when i click transcode:

transcode:
 Hängt ab: libavifile-0.7c102 but it is not installable
 Hängt ab: libjasper-1.701-1 but it is not installable
  Hängt ab: libquicktime1 but 0.9.2release-5 is to be installed 

i use this repository:

[ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)

thx

---

### Post by CbrPad on 2004-10-27
Hi, 

I'm a linux newbie and had the same problem, but I managed to get Transcode installed by doing a Google for those two files and downloading them from some ftp sites where they were found.

Next I did a      dpkg - i name-of-file

This failed because of some dependencies that they needed so I just took note of the deps names and installed them with apt, tried the two files again, and finally Transcode itself and all was sweet.

There's probably a neater way but I don't know it yet.

HTH,
Paddy.

---

### Post by rupert on 2004-10-28
sorry i forgot about this post,
i got everything working fine now.
i can use dvdrip and avidemux without problems.
nice solutions and easy to use.
I post some links for people who wanna know more:

[http://avidemux.sourceforge.net/](http://avidemux.sourceforge.net/)

[http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)

[http://lpn.rnbhq.org/projects/c/c.shtml](http://lpn.rnbhq.org/projects/c/c.shtml)

everthing else should be avaible on the linked pages.

---

### Post by im_ka on 2004-10-28
i did have the marillat repo in my sources.list, however it was still complaining  about transcode's dependencies.

i've found

libavc
libjasper
libavifile
libquicktime

on [rpmseek](http://www.rpmseek.com) (yes, you can find debs there). installed them with dpkg and apt-geted dvdrip.

---

### Post by im_ka on 2004-10-29
hmm... i think i've ran into a wall trying to rip encrypted dvds.
does any1 know a relatively easy way to do this before i start googleing?

---

### Post by Rule on 2004-11-09
well anyone know why I keep getting this error

  Depends: libpng12-0 but 1.2.5.0-7ubuntu1 is to be installed
  Depends: libquicktime1 but 0.9.2release-5 is to be installed

I have them installed (used google :D)

TIA
Rule

---

### Post by nyn on 2005-01-13
dvdrip depends on transcode, however:
transcode depends on libvorbis0, but lots of other installed stuff (audacity, k3b...) depend on libvorbis0a, which conflicts with libvorbis0
I removed libvorbis0a and installed libvorbis0 to see if transcode would be installable.
I was then informed that transcode depends on liba52-0.7.4, libavcodeccvs, libfame-0.9, liblame0, libpvm3, libdivxdecore0, libdivxencore0, libxvidcore4 and gawk, however:
I could no longer use apt to download anything. I know that the system is broken, but I don't see why that should interfere with apt --download-only. Anyway, I went google-hunting (yuck!) for the required packages, and finally tried to dpkg -i them. I was then informed that libavcodeccvs depends on lots of other packages, including ***libvorbis0a***.
That was the end of the road for me. And there goes another afternoon trying to get some piece of free software to work...	:(

---

### Post by wallijonn on 2005-01-13
The libpng12 needs to be at a cetain version (1.2.8 ) and the Warty lib is at a lower version (1.2.5). Transcode may work better under Hoary. Or you'll have to manually update libpng12. In my case it was [http://debian.goldweb.com.au/debian/pool/main/libp/libpng3/](http://debian.goldweb.com.au/debian/pool/main/libp/libpng3/)

Not that I ever got it to work; there's just too many dependencies and likely to break all sorts of libs.

---

### Post by chele on 2005-01-13
A PPC repository can be found at [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) mplayer/

However, I have not tried to install yet, as apt does not like that line in the sources.list file. I was just going to download all the .debs and install then manually, when I get a chance.

I also have:

deb [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sid main
deb-src [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sid main

which does include some MM PPC binaries, giving things like libdvdcss....

---

### Post by mirtux on 2005-01-24
[QUOTE=nyn]dvdrip depends on transcode, however:
transcode depends on libvorbis0, but lots of other installed stuff (audacity, k3b...) depend on libvorbis0a, which conflicts with libvorbis0
I removed libvorbis0a and installed libvorbis0 to see if transcode would be installable.
I was then informed that transcode depends on liba52-0.7.4, libavcodeccvs, libfame-0.9, liblame0, libpvm3, libdivxdecore0, libdivxencore0, libxvidcore4 and gawk, however:
I could no longer use apt to download anything. I know that the system is broken, but I don't see why that should interfere with apt --download-only. Anyway, I went google-hunting (yuck!) for the required packages, and finally tried to dpkg -i them. I was then informed that libavcodeccvs depends on lots of other packages, including ***libvorbis0a***.
That was the end of the road for me. And there goes another afternoon trying to get some piece of free software to work...	:([/QUOTE]
Hi everybody,
   i would like to install [COLOR=Red]dvdrip[/COLOR] but of course i require [COLOR=Green]transcode[/COLOR]. When i tried to install the last one with synaptic i get the error that it requires

```
transcode:
 Depends: libdvdread2 but it is not installable
 Depends: libvorbis0 but it is not installable
``` 
But i have [COLOR=Blue]libdvdread3[/COLOR] and [COLOR=Blue]libvorbis0a[/COLOR]. Does it make so much difference? Do you know if forcing transcode to install with these packages creates some problem to the system? And finally do you get the system working?

Regards,
MC

---

### Post by chele on 2005-01-25
[QUOTE=chele]A PPC repository can be found at 
[http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) mplayer/

However, I have not tried to install yet, as apt does not like that line in the sources.list file. I was just going to download all the .debs and install then manually, when I get a chance.[/QUOTE]
It now works on Ubuntu PPC. The line in sources.list is:

deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) unstable/

Apt complains of a missing key, but the packages are available and installed on the system.

---

### Post by mirtux on 2005-02-04
One question partly related to Transcode: is it possible in synaptic to force the installation of a program without taking care of dependecies?
 
 Thanks,
 MC

---

### Post by paf on 2005-02-10
Hello,

I manage to install dvdrip and transcode muy easily.

I add a repository of debian sarge (ftp.debian.org/sarge)

I do:

apt-get update
apt-get install dvdrip

It works fine, for me, it just install a few packages i need, without confilct.

Now to avoid destroy my ubuntu, i remove the repository of sarge and I update

---

### Post by psypher on 2005-02-24
I'm sorry but I have searched high and low for the debian sarge repository. What is the exact line u have in your sources.list? when i apt-get update with that repository I get errors that it cannot be found. the folder sarge does not even exist at ftp.debian.org. Please help, it seems you have found the easiest way to get dvdrip on ubuntu without hassles. I'm really keen on trying the grid computer feature of dvdrip. 

thanks

---

### Post by Ste on 2005-02-24
I got transcode working by using the repo listed here
[http://twolife.org/debian/repository.php](http://twolife.org/debian/repository.php)

I needed to cope with some dependencies like libquicktime (the latest is in hoary).
I am now using transocde as part of an app called ldvd -- [http://projects.gff-clan.net/index.php](http://projects.gff-clan.net/index.php)

Said to be like dvdshrink, I'll report back with what it's like.

---

### Post by mirtux on 2005-02-25
Thanks guys... in the meanwhile i've moved to Debian unstable..... i'll have a look at the site you've indicated and i've seen some good stuff!

Thanks
MC

---

### Post by psypher on 2005-02-25
Nope. I'm not satisfied. I love ubuntu and REALLY want to get dvdrip working via apt-get. Apt-get is there for a reason. I'm don't want to compile. Either my system is broken from trying everything everybody has posted about this problem and it's too late. I tried the hoary repository. No luck. 

Let me get it right, you add the hoary by copying all your warty's and renaming all the warty's to hoary? I read that on: [http://www.ubuntuforums.org/showthread.php?t=14024&highlight=dvdrip](http://www.ubuntuforums.org/showthread.php?t=14024&highlight=dvdrip).

 I tried the backports "deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe". No luck. can somebody give an example of what the sources.list should look like if I want to add the backports repository from this page: [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/). And will that work to get transcode and dvdrip on?

I tried the repository suggest above in the thread: [http://twolife.org/debian/repository.php](http://twolife.org/debian/repository.php). No luck.

the sarge repository suggest by Paf does not exist.

Ste says:


I got transcode working by using the repo listed here
[http://twolife.org/debian/repository.php](http://twolife.org/debian/repository.php)

I needed to cope with some dependencies like libquicktime (the latest is in hoary).
I

adding hoary main got me libquicktime1 but no further.

PLEASE SOMEBODY HELP!! I didn't think dependency hell happened with apt-get.  Who has gotten this right with a vanilla install of ubuntu using apt-get. please put some details together and also your sources.list file so we can see where exactly to download this from.

---

### Post by linuxNewb on 2005-04-05
[QUOTE=Ste]I got transcode working by using the repo listed here
[http://twolife.org/debian/repository.php](http://twolife.org/debian/repository.php)

I needed to cope with some dependencies like libquicktime (the latest is in hoary).
I am now using transocde as part of an app called ldvd -- [http://projects.gff-clan.net/index.php](http://projects.gff-clan.net/index.php)

Said to be like dvdshrink, I'll report back with what it's like.[/QUOTE]

Ste, what version of Ubuntu did you get transcode onto? Also, when you say, "I needed to cope with some dependencies..." Do you mean that you had to install them seperately? Please, if you would, rewrite this post as a HOWTO with specific instructions/results as many of us want to get transcode installed without breaking our systems. Thanks in advance.

---

### Post by linuxNewb on 2005-04-06
I've been trying for a week to backup DVDs with my wart install. I just apt-getted dvdbackup and it works GREAT. Forget about dvdrip, transcode, dvddecrypter, etc.

1. Make sure you have all necessary repos ([http://ubuntuguide.org/](http://ubuntuguide.org/))
2. $ sudo apt-get update
3. $ sudo apt-get libdvdcss2
4. $ sudo apt-get dvdbackup
5. $ man dvdbackup

The instructions in the man file is very easy to follow, even for a newb like me :)

---

### Post by Nano on 2005-04-06
I've found some good doc. about it:
[http://www.bunkus.org/dvdripping4linux/single/](http://www.bunkus.org/dvdripping4linux/single/)

---

### Post by sgd2z on 2005-04-13
[QUOTE=mirtux]Hi everybody,
   i would like to install [COLOR=Red]dvdrip[/COLOR] but of course i require [COLOR=Green]transcode[/COLOR]. When i tried to install the last one with synaptic i get the error that it requires

```
transcode:
 Depends: libdvdread2 but it is not installable
 Depends: libvorbis0 but it is not installable
``` 
But i have [COLOR=Blue]libdvdread3[/COLOR] and [COLOR=Blue]libvorbis0a[/COLOR]. Does it make so much difference? Do you know if forcing transcode to install with these packages creates some problem to the system? And finally do you get the system working?

Regards,
MC[/QUOTE]

In synaptic package manger, use Package -> force version to install the one from debian unstable. This worked for me. I have transcode installed and ldvd running. I havent tried actually backing up a dvd yet though!

---

### Post by iomicifikko on 2005-04-14
[QUOTE=sgd2z]In synaptic package manger, use Package -> force version to install the one from debian unstable. This worked for me. I have transcode installed and ldvd running. I havent tried actually backing up a dvd yet though![/QUOTE]
 how install transcode:
1. download libjasper-1.701-1  debian unstable here  [http://packages.debian.org/unstable/libs/libjasper-1.701-1](http://packages.debian.org/unstable/libs/libjasper-1.701-1) (i386 version for usual pc)
2, download libquicktime1 debian unstable here    [http://packages.debian.org/unstable/libs/libquicktime1](http://packages.debian.org/unstable/libs/libquicktime1)  (i386 version for usual pc)
3. install both packages via command line: (go to the folder u downloaded files via terminal and type)
 sudo dpkg -i libquicktime1_0.9.3-2_i386.deb 
 sudo dpkg -i libjasper-1.701-1_1.701.0-2_i386.deb
dont worry about broken dependencies (we are going to fix them)
4. open synaptic and if enabled, disable [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)  stable  main, then refresh. (i have all backports repositories selected,all ubuntu rep selected, also  "deb [http://sh.nu/~crimsun/](http://sh.nu/~crimsun/)  ./" but dunno if this is needed )
5. repair broken dependencies (in modify there is the option or something like that) if u need
6. select transcode et voilat.

the problem is that there are 3 different transcode versions in marillat repositories:stable,unstable,testing (doh). stable (the default choice) needs libdvdread2, but ive read somewhere that is not compatible with libdvdread3 (installed with ubuntu). if u deselect stable the next best choice is the unstable that needs those 2 files not present in ubuntu repositories.

ps: if u simply use "force version" to choose the unstable transcode then synaptic doesn look at the dependecies correctly, thats why i deselect stable repository, now be carefull couse if u add that repository again, synaptic will probably tell u about updates of those files and i dunno what could happend.

byez

---

### Post by mcclane on 2005-04-15
Part of the reason Ubuntu is so great is apt-get install something and it ¨just works¨. 

I´m not been ungrateful for the hard work the developers are putting in but the repositories aren´t exactly bulging at the moment, you´d expect what is there to ¨just work¨.

---

### Post by gcranston on 2005-04-17
Right, I'm on Hoary universe/multiverse sources but have added the marillat unstable sources as well

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main  
(don't worry about public key errors, it works fine)

My big sticking point always was libavcodeccvs.  I had some really fun (read 'unfun') version problems that someone mentioned earlier.  As you can see, libc6 gave me problems and is refered to by a lot of other packages, so dpkg complains a lot when you try to change it.  This is the error I was getting:

```
The following packages have unmet dependencies:
  libavcodeccvs: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
                 Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
E: Broken packages
```

I downloaded the 2.3.2.ds1-21 libc6 packages from:

[http://www.gotom.jp/~gotom/debian/glibc/2.3.2.ds1-21_i386.sched/](http://www.gotom.jp/~gotom/debian/glibc/2.3.2.ds1-21_i386.sched/)

You need to do libc6_2.3.2.ds1-21 first, then the dev, and i686 packages (I assmume most people are running i686, but it may work even if you're not...  I have no idea where to get x64 or ppc sources) I also installed the locales file.  after this, apt got libavcodeccvs and libavcodeccvs-dev just fine, as well as transcode from the marillat sources and dvdread from the multiverse.  The only error was "do you want to install the packages without authenitcation?" (related to public key error).  Just tell it to go ahead.  After that, I took out the marillat sources so as to not break the rest of my computer.  

That's it, just run dvdrip and it launches the preferences gui for configuration.  apt knew about all the programs dvdrip wanted but couldn't find, and then I pointed it in the direction of my dvd drive (/dev/hdc, check /etc/fstab is unsure).  The last tricky part for me was libdvdcss.  If you check the readme at /usr/share/doc/libdvdread3/README.Debian, it tells you how to get it.

There you go. Good luck too all.  I'd be happy to report this is working perfectly if I wasn't having hardware issues from slipping on ice when my laptop was in my backpack.  Time to fight with Dell for replacement parts.

Enjoy...

---

### Post by lovebug356 on 2005-04-24
It work's with me by just comment marillat unstable sources.

---

### Post by RastaMahata on 2005-04-25
[QUOTE=lovebug356]It work's with me by just comment marillat unstable sources.[/QUOTE]
So the only thing you did was to comment out the marillat repositories? and then apt-get install transcode? or dvdrip?
I suppose you have all three marillat repositories in your sources.list (2, after the commenting), and all backports repos too.

You didnt install from anywhere else?

I say this because trying to install from debian repositories, marillat, backports... its all a big mess. I got to a point of downgrading my libc6 package because if you install the newest one from debian, synaptic (apt) complains of broken packages.

I'll get home today and try to do what you said.

Also, if anyone has a good idea of how to do avi2vcd (splitting in to 2+ cds included, and subtitles too), without mencoder (i dont want to use mplayer or anything like that... what about xine...), please tell. :(

---

### Post by gcranston on 2005-05-04
libc6 sources are listed 3 posts above.  That got me around the libc6 problem and it's working fine (hardware issues from above now resolved :))

-Graham

---

### Post by frühstück on 2005-05-04
dvdbackup works without marillat, transcode don't.

---

### Post by jiyuu0 on 2005-05-04
try...

[http://www.ubuntuguide.org/#dvdrip](http://www.ubuntuguide.org/#dvdrip)
can run and rip dvd -> xvid

still don't know how to make it rip dvd -> divx...

---

### Post by MemoryDump on 2005-05-04
[QUOTE=jiyuu0]try...

[http://www.ubuntuguide.org/#dvdrip](http://www.ubuntuguide.org/#dvdrip)
can run and rip dvd -> xvid

still don't know how to make it rip dvd -> divx...[/QUOTE]

this worked like a charm for me.. I got ripdvd working now.. thxs for the info. :)

---

### Post by rwabel on 2005-05-08
[QUOTE=gcranston]Right, I'm on Hoary universe/multiverse sources but have added the marillat unstable sources as well

deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") unstable main  
(don't worry about public key errors, it works fine)

My big sticking point always was libavcodeccvs. I had some really fun (read 'unfun') version problems that someone mentioned earlier. As you can see, libc6 gave me problems and is refered to by a lot of other packages, so dpkg complains a lot when you try to change it. This is the error I was getting:

```
The following packages have unmet dependencies:
  libavcodeccvs: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
                 Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
E: Broken packages
```

I downloaded the 2.3.2.ds1-21 libc6 packages from:

[http://www.gotom.jp/~gotom/debian/glibc/2.3.2.ds1-21_i386.sched/]("http://www.gotom.jp/%7Egotom/debian/glibc/2.3.2.ds1-21_i386.sched/")

You need to do libc6_2.3.2.ds1-21 first, then the dev, and i686 packages (I assmume most people are running i686, but it may work even if you're not... I have no idea where to get x64 or ppc sources) I also installed the locales file. after this, apt got libavcodeccvs and libavcodeccvs-dev just fine, as well as transcode from the marillat sources and dvdread from the multiverse. The only error was "do you want to install the packages without authenitcation?" (related to public key error). Just tell it to go ahead. After that, I took out the marillat sources so as to not break the rest of my computer. 

That's it, just run dvdrip and it launches the preferences gui for configuration. apt knew about all the programs dvdrip wanted but couldn't find, and then I pointed it in the direction of my dvd drive (/dev/hdc, check /etc/fstab is unsure). The last tricky part for me was libdvdcss. If you check the readme at /usr/share/doc/libdvdread3/README.Debian, it tells you how to get it.

There you go. Good luck too all. I'd be happy to report this is working perfectly if I wasn't having hardware issues from slipping on ice when my laptop was in my backpack. Time to fight with Dell for replacement parts.

Enjoy...[/QUOTE]

thanks for the link, that helped me to installed newest amule from amule cvs. cool!

---

### Post by gcranston on 2005-05-08
rwabel:

No problem!  This is actually the first thing I've managed to explain to someone else and have it work.  A momentous day for both of us!

-Graham

---

### Post by spurious on 2005-05-15
First time poster here; I just installed Ubuntu a week ago (went perfectly on a Dell Latitude D600; even the wireless was automatically detected and configured).  I tried installing transcode yesterday, and encountered the dependency conflicts.  I found this thread through Google.

Thanks to all of you for your help.  I found that all I had to do was simply remove the marillat stable and marillat unstable repositories from my sources.list, leaving only the marillat testing.  I then successfully installed transcode and dvdrip without having to download and dpkg -i any third-party *.deb packages.

I posted more details at LinuxQuestions.org, [in this thread](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1644153#post1644153).

---

### Post by Nolgthorn on 2005-06-04
[QUOTE=jiyuu0]try...

[http://www.ubuntuguide.org/#dvdrip](http://www.ubuntuguide.org/#dvdrip)
can run and rip dvd -> xvid

still don't know how to make it rip dvd -> divx...[/QUOTE]
Perfect!! Thanks a lot this got things working. There were a lot of steps in there but I don't mind following them when I know what I'm doing isn't going to be in vain. Again thank you very much this was very helpful.

Signed,
 \\:D/

---

### Post by Raptor Ramjet on 2005-06-24
Getting a working package for DVD:RIP and transcode into Ubuntu should be a priority.  I've currently managed to get 4 people to try out Ubuntu and the main thing they're complaining about is that they can't do any DVD burning.

And beofre anyone starts blabbering on about piracy the reason they all want to backup their DVDs are for one of two reasons.  1 To get rid of all the "non fast forwardable crap" at the beginning or  2 So their kids don't ruin the originals of all their cruddy Disney films.

But apart from that they're all nearly as happy as I am with Ubuntu because SYnaptics so damned good !

---

### Post by Hep on 2005-08-23
Hi Guys,

I can't still install dvdrip. No way to find some good repos for that.
Any news ?

Regards,
Hep

---

### Post by bored2k on 2005-08-23
[http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/](http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/)

---

### Post by bored2k on 2005-08-23
[QUOTE=Hep]Hi Guys,

I can't still install dvdrip. No way to find some good repos for that.
Any news ?

Regards,
Hep[/QUOTE]
1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get install
3. sudo apt-get install dvdrip

---

### Post by pkoufalas on 2005-08-24
[QUOTE=bored2k][http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/](http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/)[/QUOTE]

Yes, found this. Grabbed both the 0.6.x tarball and patch as well as 1.0.0 package while at the office. The 1.0.0 package wanted to upgrade too many packages (I'm only on 56k dialup at home!), so I thought I'd compile 0.6.x to avoid that issue.

Well, dpkg-buildpackage -rfakeroot -b complained about lots of unmet dependencies anyway! So I started to address them using synaptic. The list is down to half a dozen or so remaining, but it is painful and I don't even know if the package will build after that or if I should stick to 1.0.0 instead?

---

