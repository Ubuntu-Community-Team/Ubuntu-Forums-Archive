---
title: "Help the newbie please."
date: 2004-11-08
forum: General Help
---

### Post by dubdubdub on 2004-11-08
I have been using Ubuntu for exactly 18 hours now and I love it. First time ever using Linux in fact. I am a little stuck on a couple of things:

Is there anything as easy as DVDXCopy (Windows) to make compressed backups of my dvds? I was able to use 'k3b' to burn some VIDEO_TS and AUDIO_TS folders I had. So burning is not an issue.

How do I get MPEG Files/Quicktime movies to work in Firefox?

Any recommended repositories I can add to Synaptic?

I replaced Windows XP with Ubuntu on my wintel box. I have been a Mac OS user for nearly 12 years now (web/print designer) and needless to say, this is all quite strange...

tia - dub


errr didn't mean to put this post in the wrong section. sorry moderators.

---

### Post by fng on 2004-11-08
hi apple buddy :grin:

here is my /etc/apt/sources.list
```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 

#############Ubuntu Warty##############

deb http://archive.ubuntu.com/ubuntu/ warty main
deb http://archive.ubuntu.com/ubuntu/ warty universe
deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb http://archive.ubuntu.com/ubuntu/ warty restricted

deb-src http://archive.ubuntu.com/ubuntu/ warty main
deb-src http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty restricted


##############Ubuntu Security##############

deb http://security.ubuntu.com/ubuntu/ warty-security main
deb http://security.ubuntu.com/ubuntu/ warty-security restricted
deb http://security.ubuntu.com/ubuntu/ warty-security universe
deb http://security.ubuntu.com/ubuntu/ warty-security multiverse

deb-src http://security.ubuntu.com/ubuntu/ warty-security main
deb-src http://security.ubuntu.com/ubuntu/ warty-security restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security universe
deb-src http://security.ubuntu.com/ubuntu/ warty-security multiverse


##############Ubuntu Warty Updates################
deb http://archive.ubuntu.com/ubuntu/ warty-updates main
deb http://archive.ubuntu.com/ubuntu/ warty-updates restricted
deb http://archive.ubuntu.com/ubuntu/ warty-updates universe
deb http://archive.ubuntu.com/ubuntu/ warty-updates multiverse

deb-src http://archive.ubuntu.com/ubuntu/ warty-updates main
deb-src http://archive.ubuntu.com/ubuntu/ warty-updates restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ warty-updates multiverse


#--------------------------------------------------------------------
#---------------------------Hoary------------------------------------
#############Ubuntu Hoary##############
# deb http://archive.ubuntu.com/ubuntu/ hoary main
# deb http://archive.ubuntu.com/ubuntu/ hoary universe
# deb http://archive.ubuntu.com/ubuntu/ hoary multiverse
# deb http://archive.ubuntu.com/ubuntu/ hoary restricted

# deb-src http://archive.ubuntu.com/ubuntu/ hoary main
# deb-src http://archive.ubuntu.com/ubuntu/ hoary universe
# deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ hoary restricted


##############Ubuntu Security##############
# deb http://security.ubuntu.com/ubuntu/ hoary-security main
# deb http://security.ubuntu.com/ubuntu/ hoary-security restricted
# deb http://security.ubuntu.com/ubuntu/ hoary-security universe
# deb http://security.ubuntu.com/ubuntu/ hoary-security multiverse

# deb-src http://security.ubuntu.com/ubuntu/ hoary-security main
# deb-src http://security.ubuntu.com/ubuntu/ hoary-security restricted
# deb-src http://security.ubuntu.com/ubuntu/ hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu/ hoary-security multiverse


#--------------------------------------------------------------------
#---------------------------Non_Ubuntu------------------------------
###############Debian###############
#deb ftp://ftp.nerim.net/debian-marillat/ testing main 
# deb http://ftp.kulnet.kuleuven.ac.be/debian/ unstable non-free contrib
# deb http://www.getsweaaa.com/~tseng/ubuntu/debs ./

``` 

For the mpeg/quicktime movies.
First install mplayer :).  You can follow this guide ( [http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94) ).
After mplayer is installed :
```
$> sudo apt-get install mozilla-mplayer
``` 
That should to the trick

---

### Post by wallijonn on 2004-11-08
Always first visit the HOWTO/FAQ section.

When starting a posit state the problem, like 

INQ: DVDXCopy MPeg QTime ?
or
PRB:MPlayer install
or
[error code]:<description>

It's not for you - it's for everybody behind you that has the same inquiry or problem. It'll help when using the search function.

ps, I'm a newbie too.

---

### Post by Rancoras on 2004-11-08
[QUOTE=wallijonn]Always first visit the HOWTO/FAQ section.

When starting a posit state the problem, like 

INQ: DVDXCopy MPeg QTime ?
or
PRB:MPlayer install
or
[error code]:<description>

It's not for you - it's for everybody behind you that has the same inquiry or problem. It'll help when using the search function.

ps, I'm a newbie too.[/QUOTE]

Actually, ubuntu-geek (the site admin) frowns on the use of abbreviations and acronyms.  From the site FAQ:

* Never invent acronyms, use as few acronyms as possible. It's called a problem, not a "pb" and a question, not a "Q".

---

### Post by wallijonn on 2004-11-08
will do. thanks.

---

### Post by dubdubdub on 2004-11-08
> For the mpeg/quicktime movies.
First install mplayer :).  You can follow this guide ( [http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94) ).
After mplayer is installed :
```
$> sudo apt-get install mozilla-mplayer
``` 
That should to the trick

Thanks for all the help. For whatever reason when I got to the step " $ wget [http://ftp5.mplayerhq.hu/mplayer/re...1.0pre5.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...1.0pre5.tar.bz2)
$ wget [http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2)
$ wget [http://ftp5.mplayerhq.hu/mplayer/re...-8859-1.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...-8859-1.tar.bz2)
$ wget http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2" It gave me an error 404 after trying to connect for several minutes. I will try it again later

---

### Post by dubdubdub on 2004-11-08
Nevermind, I am a freaking moron.

I was putting: wget [http://ftp5.mplayerhq.hu/mplayer/re...1.0pre5.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...1.0pre5.tar.bz2)
(which was a copy and paste from the instructions!) 

Instead of: wget [http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre5.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre5.tar.bz2)

I will keep working at it! Thanks again - dub

---

### Post by fng on 2004-11-08
you allready found the solution as i was typing :)

---

### Post by dubdubdub on 2004-11-08
yeah slowly but surely.....has still had to reconnect like 3 times, hasn't finished the first file yet and I am on fast cable modem.

 > 
7% [=>                                   ] 360,552       36.37K/s    ETA 02:09

18:02:39 (35.64 KB/s) - Read error at byte 360552/5072836 (Connection timed out). Retrying.

46% [++==============>                    ] 2,354,448     38.75K/s    ETA 01:06

18:19:37 (40.42 KB/s) - Read error at byte 2354448/5072836 (Connection timed out). Retrying.

Length: 5,072,836 (2,718,388 to go) [application/x-tar]

81% [+++++++++++++++++============>       ] 4,113,768     41.20K/s    ETA 00:23 

I thought it might be my web connection. I am sharing internet connection from my G4/933 through ethernet. The G4 is getting its web connection via airport express.

If I could only get my motorolla 802.11g PCI adaptor to work it would resolve me having to purchase a router (our house is 100% wireless). Any suggestions on that one or should i start a new thread?

thanks-dub

---

### Post by dubdubdub on 2004-11-08
MPlayer installed! That guide was really really helpful. Now if I could only solve my other 2 problems...or is it 3 now? :)

---

### Post by dubdubdub on 2004-11-08
>  dub@ubuntu:~ $ sudo apt-get install mozilla-mplayer
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package mozilla-mplayer


any suggestions now?

---

### Post by Rancoras on 2004-11-08
Keep going in the Multimedia HOWTO thread and it will tell you how to compile and install the plugin you're seeking.

---

