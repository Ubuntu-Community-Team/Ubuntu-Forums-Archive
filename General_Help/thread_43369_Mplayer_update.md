---
title: "Mplayer update"
date: 2005-06-21
forum: General Help
---

### Post by granite230 on 2005-06-21
I cant seem to update Mplayer.

granite@granite:~ $ mplayer --help
MPlayer 1.0pre5-3.3.4 (C) 2000-2004 MPlayer Team

I know there is a new version, but apt-get update / upgrade won't update Mplayer. I think something might be missing in my sources.list but I don't know what.

How can I make this work?

---

### Post by Xian on 2005-06-21
You probably just need to add the backport repos to your /etc/apt/sources.list

```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by granite230 on 2005-06-21
That worked but not completely. It did update a lot but Mplayer is still the old version.
How can I see what each line updates when I open my sources.list... I dont really get that part :P

I cant check my sources.list and immediately see: hey! look at that! deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted and
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted are missing!

How do you know what each line does?

my current version of MPlayer after I restarted Gnome:
MPlayer 1.0pre5-3.3.4 (C) 2000-2004 MPlayer Team

still the old version.

---

### Post by Xian on 2005-06-21
[QUOTE=granite230]That worked but not completely. It did update a lot but Mplayer is still the old version.[/QUOTE]
There could be alot of reasons for this. It is best that we try and eliminate the most obvious ones first. To this end we need to see if the mplayer upgrade is being blocked or obstructed by any local issues. Let's begin by making certain that your entire sources.list is properly setup. Please issue the command below to backup your current list, and then save the example provided as the new /etc/apt/sources.list in a text editor.

```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

#deb http://www.os-works.com/debian testing main
#deb-src http://www.os-works.com/debian testing main
```
Now run the following commands.
Post the output of the second one if mplayer does not update.
Or if it gives you any error messages.
```
$ sudo apt-get update
$ sudo apt-get install mplayer-386
```

---

### Post by granite230 on 2005-06-22
okay, but!

I also have, let say: 
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
in my sources.list. There may be other that are not mentioned in the sources.list example you posted. So that would mean I'm not completely updating everything using that sources.list.

also: 
will a apt-get install mplayer-386 overwrite the older files or do I have to uninstall mplayer first?

I tried it:

granite@granite:~ $ sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
mplayer-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
granite@granite:~ $

Hmz, one of my friends has MPlayer 6-something. I have 5-something. He is also using Ubuntu. My Mplayer sometimes behaves really really strange, spontenous lockups, or hundreds of errors each second making it hard for me to shut down the program. I now use Xine, works a lot better, but a lot of people think MPlayer is the ultimate media player... I cant say I agree with them... yet.

---

### Post by Xian on 2005-06-22
[QUOTE=granite230]
I also have, let say: 
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
in my sources.list. There may be other that are not mentioned in the sources.list example you posted. So that would mean I'm not completely updating everything using that sources.list.

also: 
will a apt-get install mplayer-386 overwrite the older files or do I have to uninstall mplayer first?
[/QUOTE]
I'm not familiar with those sourceforge.net repos.
I've not found any occasion to use them.

You don't have to uninstall a package before upgrading it.
All of that is taken care of automagically.

---

### Post by rudiz on 2005-06-22
mplayer is in multiverse not in the backports

---

### Post by mgoellner on 2005-06-22
I seem to be missing some repositories, mplayer doen't even appear when I do an apt-cache search for it, any ideas why that may be?

here's my sources.list

```
mgoellner@kanrei:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://de.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://de.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://de.archive.ubuntu.com/ubuntu hoary universe
 deb-src http://de.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

mgoellner@kanrei:~$

```

---

### Post by rudiz on 2005-08-22
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary multiverse
 deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary multiverse

ad these lines to ur source.list

---

