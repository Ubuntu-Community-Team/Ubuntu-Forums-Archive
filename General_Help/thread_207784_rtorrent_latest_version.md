---
title: "rtorrent latest version"
date: 2006-07-02
forum: General Help
---

### Post by hikitsu4 on 2006-07-02
Does anyone know where i can find rtorrent 0.5.3 with libtorrent 0.9.3 for dapper 6.06 LTS, in deb format. If nobody knows where to find it can somebody make a deb file for ubuntu then.

---

### Post by hikitsu4 on 2006-07-02
i was able to find the latest version on [http://packages.debian.org/unstable/net/rtorrent](http://packages.debian.org/unstable/net/rtorrent) but then it needs a newer libc6, so it doesnt work.

---

### Post by maagimies on 2006-07-03
I too would like someone to help, because there's certain features in the modern version that I would like.
I'm currently *trying* to make debian packages of libtorrent and rtorrent, and libtorrent's causing me trouble. No matter how I set the configs in the debian directory, the resulting libtorrent and libtorrent-dev packages are always empty. Even though it compiles succesfully.
Why is Debian packaging this ¤%#!% hard :(

---

### Post by Gonzakpo on 2006-07-05
Yes! I also want to try the latest version! 
I'm using the version that apears in the repositories. 

Personally, i couldn't reach reasonable download speeds (with azureus i used to download at 50 kb/s and with rtorrent only at 30kb/s MAX), but i don't complain because, first, I'm not hurried, and, second, it doesn't hang my computer like azureus does! (I'm using it on an old computer).

Well, I hope you can make some deb packages for this (because i have no idea!). Good Luck!

---

### Post by grte on 2006-07-22
I've made some debs of the latest version.  This is my first attempt at letting others use mine, so I have no idea if it will work for you.

Just unzip it.  Debs for both the latest libtorrent and rtorrent are in there.

---

### Post by xtalman on 2006-07-24
grte:

Just tried your debs.  They seem to be working great!  Thanks!

---

### Post by rko618 on 2006-08-06
holly sh** rTorrent rocks!  I'm getting crazy fast download speeds compared to bittornado.

---

### Post by kalle314 on 2006-08-10
Great! Thanks!

I was also using the version in the repositories (0.4.2.), and was missing the functions of the later versions.

It's the best torrent client I've used!
(I've used Azureus, BitTorrent, BitTornado, Freeloader, QTorrent & KTorrent before.)

---

### Post by grte on 2006-09-26
Here's rtorrent 0.6.2 and libtorrent 0.10.2:

---

### Post by kalle314 on 2006-09-30
Thanks!

---

### Post by chomafin on 2006-10-02
> **grte said:**
> Here's rtorrent 0.6.2 and libtorrent 0.10.2:


Hello, I was currious if anyone else was having any issues w/ this version of rTorrent?  I've been using the 0.4.2-1 that is avil on the repositories without any issues, but when I tried updating, I get errors.  Seems whenever rTorrent starts to check the hash of an already downloaded file, it will crash w/ a segmentation fault.

```
Caught Segmentation fault, dumping stack:
0 rtorrent [0x8057601]
1 rtorrent [0x806856c]
2 [0xffffe420]
3 /usr/local/lib/libtorrent.so.9(_ZSt27__stable_partition_adaptiveIN9__gnu_cxx17__normal_iteratorIPPN7torrent13ChunkListNodeESt6vectorIS4_SaIS4_EEEES5_N3rak11not_equal_tIiSt15const_mem_fun_tIiS3_EEEiET_SF_SF_T1_T2_T0_SH_+0x78) [0xb7ec0efc]
4 /usr/local/lib/libtorrent.so.9(_ZSt27__stable_partition_adaptiveIN9__gnu_cxx17__normal_iteratorIPPN7torrent13ChunkListNodeESt6vectorIS4_SaIS4_EEEES5_N3rak11not_equal_tIiSt15const_mem_fun_tIiS3_EEEiET_SF_SF_T1_T2_T0_SH_+0x133) [0xb7ec0fb7]
5 /usr/local/lib/libtorrent.so.9(_ZSt16stable_partitionIN9__gnu_cxx17__normal_iteratorIPPN7torrent13ChunkListNodeESt6vectorIS4_SaIS4_EEEEN3rak11not_equal_tIiSt15const_mem_fun_tIiS3_EEEET_SF_SF_T0_+0x92) [0xb7ec1146]
6 /usr/local/lib/libtorrent.so.9(_ZN7torrent9ChunkList11sync_chunksEi+0x432) [0xb7ec01d8]
7 /usr/local/lib/libtorrent.so.9(_ZN7torrent12ChunkManager8sync_allEiy+0x60) [0xb7ea43fa]
8 /usr/local/lib/libtorrent.so.9(_ZN7torrent12ChunkManager13periodic_syncEv+0x35) [0xb7ea447d]
9 /usr/local/lib/libtorrent.so.9(_ZN7torrent7Manager12receive_tickEv+0x34) [0xb7e9bf9c]
10 /usr/local/lib/libtorrent.so.9(_ZN3rak9mem_fn0_tIN7torrent7ManagerEvEclEv+0x3e) [0xb7e9c6ea]
11 /usr/local/lib/libtorrent.so.9(_ZN7torrent7performEv+0x112) [0xb7eb9594]
12 rtorrent [0x80a2f90]
13 rtorrent [0x8059311]
14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb799bea2]
15 rtorrent(_ZN7torrent18set_max_open_filesEj+0x81) [0x80518a1]

```

Any ideas?

---

### Post by chomafin on 2006-10-02
> **chomafin said:**
> Hello, I was currious if anyone else was having any issues w/ this version of rTorrent?  I've been using the 0.4.2-1 that is avil on the repositories without any issues, but when I tried updating, I get errors.  Seems whenever rTorrent starts to check the hash of an already downloaded file, it will crash w/ a segmentation fault.

```
Caught Segmentation fault, dumping stack:....

```Any ideas?

Hmm, seems reverting back to * rTorrent 0.6.0 - libTorrent 0.10.0 * has fixed my crashes.. Thanks for making the debs :)

---

### Post by grte on 2006-10-02
> **chomafin said:**
> Hmm, seems reverting back to * rTorrent 0.6.0 - libTorrent 0.10.0 * has fixed my crashes.. Thanks for making the debs :)

No problem.

These are all unstable, so if you're having trouble with the latest public release, you might want to try compiling from svn, or just waiting it out for the next release.  The issue may have been solved.

---

### Post by konsole on 2006-10-03
> **grte said:**
> No problem.

These are all unstable, so if you're having trouble with the latest public release, you might want to try compiling from svn, or just waiting it out for the next release.  The issue may have been solved.

Had no luck compiling from svn (c++ compiler cannot create executables error message on ./configure)

Anyway thanks for the rTorrent 0.6.0 & libTorrent 0.10.0 debs. Much appreciated.

---

### Post by kalle314 on 2006-10-06
I have been using rTorrent 0.6.2 for some days now, and I haven't  experienced any trouble. The main difference I have noted is that the hash checking, which was already very fast, is even quicker in 0.6.2.

But the development is really fast! 0.6.2 has only been out for a couple of weeks, and version 0.6.3 is already released!

---

### Post by grte on 2006-10-06
> **kalle314 said:**
> But the development is really fast! 0.6.2 has only been out for a couple of weeks, and version 0.6.3 is already released!

Speaking of which, here are the debs:

---

### Post by konsole on 2006-10-07
Finally got rtorrent 0.6.3 and libtorrent 0.10.3 compiled and installed.

No problems encountered after running for 24 hrs. New view screen is much better. Same good dl/ul performance. Better memory usage.

Worth upgrading if you can.

---

### Post by PaaZe on 2006-10-09
> **grte said:**
> Speaking of which, here are the debs:

Thanks, works great!

---

### Post by Kateikyoushi on 2006-10-09
Thanks grte I really missed some of the new features, now it is really comfy to leave it on and it automatically starts and stops DLs.

---

### Post by Kalden on 2006-10-20
Thanks a lot for de .debs =D>

---

### Post by cybergypsy on 2006-10-23
Yea - thanks for the latest .debs

I tried compiling from CVS but the autotools package is too old :(

---

### Post by nont on 2006-10-29
> **cybergypsy said:**
> Yea - thanks for the latest .debs

I tried compiling from CVS but the autotools package is too old :(

I tried compile the lastest CVS myself too but did not success :)

Thanks a lot  grte !

---

### Post by grte on 2006-10-30
Version 0.6.4:

---

### Post by Cred on 2006-11-11
Nice work.. could you do the work for 64bit too? I'm currently running the repository version, which works just fine, but I'd like to be on the bleeding edge with Edgy.

I tried compiling it my self but missing sigc++ or something caused trouble.

---

### Post by grte on 2006-11-11
Unfortunately, I can't.  I haven't got access to a 64 bit processor, at the moment, so no edgy 64.

For collecting the dependancies you're missing, a useful command is
```
sudo apt-get build-dep <package name>
```

It'll only work if there's some version of the app in the repos already, but as long as there is it will almost always collect all the dependancies you need.

---

### Post by Zetx on 2006-11-13
Could someone compile the svn libtorrent and rtorrent? The stable releases don't support encryption (or the one I compiled myself doesn't o_O).

I tried myself, but for some reason rtorrent demanded .11 of libtorrent and after I bypassed that (edited the configure file) it wouldn't compile (make) properly. ](*,)

Thank you.

---

### Post by konsole on 2006-11-16
> **Zetx said:**
> Could someone compile the svn libtorrent and rtorrent? The stable releases don't support encryption (or the one I compiled myself doesn't o_O).

I tried myself, but for some reason rtorrent demanded .11 of libtorrent and after I bypassed that (edited the configure file) it wouldn't compile (make) properly. ](*,)

Thank you.

Checked out latest revision 804

Get an updated [.rtorrent.rc]("http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=804&format=raw")

Attached are the the debs for libtorrent 0.11.0 and rtorrent 0.7.0

btw... all care but no responsibility etc. :)

K.

---

### Post by patrikC on 2006-11-28
im trying to download the attachment 
File Type: gz 	libtorrent_rtorrent-0.6.4.tar.gz (572.9 KB, 76 views)
but it does not seem to work.
(if you read between the lines you see i'm pretty new at this).
Is there a special way to download attachments other than clicking on them (stupid question maybe, but a logical one during conversion from windows)

I get this message in a pop-up, a little swedish in it so i suspect i have missed something in my swedish installation of ubuntu.

XML-tolkningsfel: ej välformat
Adress: chrome://mozapps/content/downloads/unknownContentType.xul
Radnummer 1, Kolumn 3:  },      
--^

---

### Post by Brokenrgv on 2006-12-11
anyone help with setting up a shedule to stop downloads at a set time and if possible start again at a set time with this program? ,also just curious, whats the highest amount of memory you've seen this program use, only been using this app for a week and allready i love it, got rid of azureus and its hogging ways.

---

### Post by Useff on 2007-01-04
Thanks a lot for these .debs, I appreciate it.

---

### Post by Useff on 2007-01-05
Hey, here are some .debs of the recently released rtorrent 0.7.1 and libtorrent 0.11.1. This is my first time ever trying to build a package, and hopefully they work. If not, I'm sure the more experienced guys will come through with the correct stuff.

---

### Post by kalle314 on 2007-01-06
Useff: It didn't work for me on dapper, but it might very well work on edgy.
When i tried to install the libtorrent deb it complained about the versions of various libraries, so I guess it wanted the edgy versions.

---

### Post by ge5239 on 2007-01-11
same here.. 
since im kinda stupid with these things, anyone else wanna try to make a deb for, ehm, me, and im sure someone else ;)

---

### Post by konsole on 2007-01-12
> **ge5239 said:**
> same here.. 
since im kinda stupid with these things, anyone else wanna try to make a deb for, ehm, me, and im sure someone else ;)

These debs where compiled on Dapper server using svn revision 841. The versions are libtorrent 0.11.2 and rtorrent 0.7.2 and have been behaving very nicely for the past week.

ymmv. good luck.

---

### Post by kalle314 on 2007-01-12
konsole: Many thanks! I'm using it now!

---

### Post by ge5239 on 2007-01-12
thank you from me too :) 
always feels good to be updated ;)

---

### Post by erhell on 2007-01-12
really nice, much appreciated! :)

---

### Post by Brokenrgv on 2007-01-14
awesome thanks again for the updated debs, this is why i love ubuntu, its all about the awesome comunity

---

### Post by XPerienced on 2007-01-21
0.7.2 worked fine to install and start on Dapper server without X. It's hashing now.

XPerienced

---

### Post by freakshow on 2007-01-22
I am confused.  I am using 0.7.2 for about a week.  The site I use, bitmetv, just banned my client saying it was outdated.  I went to rtorrent homepage and they only show release 0.7.1 as being the latest.  What gives?  The .0.7.2 is throwing off bitmetv snice that version hasn't been officially released.
Anyone know of a 0.7.1 release that works on Dapper?

---

### Post by XPerienced on 2007-01-22
Don't use 0.7.2. There a bug. I have alot of trouble with it.

I tried to install 0.7.1, but I couldn't install that. There was problems with dependency.

XPerienced

---

### Post by Freemor on 2007-01-25
thanks for packaging up the .debs Konsole. they are installed and seem to be working fin on my Dapper.

---

### Post by neilp85 on 2007-02-04
> **XPerienced said:**
> Don't use 0.7.2. There a bug. I have alot of trouble with it.

I tried to install 0.7.1, but I couldn't install that. There was problems with dependency.

XPerienced

The bug that I think you are referring to is actually a kernel bug with mmap. Check out these links for more info:

[http://kerneltrap.org/node/7504](http://kerneltrap.org/node/7504)
[http://kerneltrap.org/node/7517](http://kerneltrap.org/node/7517)
[http://kerneltrap.org/node/7529](http://kerneltrap.org/node/7529)

---

### Post by James6380 on 2007-02-08
[COLOR="Red"]**[SIZE="4"]Hi there I am new to all this I am building a server to look after my email and download torrents as windows sucks big time anyway. I am running 1.7ghz / 256 mb ram and 60gb HDD OS: Ubuntu i386 Server 6.10.  Anyway what files do I need to get RTORRENT installed and how do I install it. [/SIZE]**[/COLOR]

:( Sorry if I sound very dump but I have only started on linux like 2 hours ago and just starting to get my head around it all as I really enjoy learning new things.

:guitar: thanks

---

### Post by grte on 2007-02-08
Make sure you're term is currently pointed to the directory where the rtorrent tar.gz file is stored, and try, one line at a time.

```
sudo apt-get build-dep rtorrent
tar -xzf <rtorrent file>.tar.gz
cd <rtorrent file>
./configure
make
sudo make install
```

If you're installing from one of the deb packages above,

```
sudo dpkg -i <package>.deb
```

---

### Post by AnalogRetentive on 2007-03-18
I'm trying to install the latest rtorrent to get the on_start/etc symlinks working. With the previous version of rtorrent as well as the one packaged by Konsole on the previous page, I get this error when starting up rtorrent, if I have the on_start/etc options enabled:

rtorrent: Error in option file: ~/.rtorrent.rc:34: Variable "on_start" does not exist.

I thought upgrading to the latest libtorrent and rtorrent would fix this, but I guess not. Any ideas of what to try next?

---

### Post by konsole on 2007-03-19
> **AnalogRetentive said:**
> I'm trying to install the latest rtorrent to get the on_start/etc symlinks working. With the previous version of rtorrent as well as the one packaged by Konsole on the previous page, I get this error when starting up rtorrent, if I have the on_start/etc options enabled:

rtorrent: Error in option file: ~/.rtorrent.rc:34: Variable "on_start" does not exist.

I thought upgrading to the latest libtorrent and rtorrent would fix this, but I guess not. Any ideas of what to try next?

This looks like an error exists in line 34 of of your .rtorrent.rc file. I haven't heard of on_start maybe you mean load_start?

Why not grab a [new rc]("http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=870&format=raw")  and start from there.

---

### Post by AnalogRetentive on 2007-03-19
> **konsole said:**
> This looks like an error exists in line 34 of of your .rtorrent.rc file. I haven't heard of on_start maybe you mean load_start?

Why not grab a [new rc]("http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=870&format=raw")  and start from there.

[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Createsymboliclinkstoindicatethedownloadstate](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Createsymboliclinkstoindicatethedownloadstate)

Taken right from their wiki page.

---

### Post by konsole on 2007-03-19
> **AnalogRetentive said:**
> [http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Createsymboliclinkstoindicatethedownloadstate](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Createsymboliclinkstoindicatethedownloadstate)

Taken right from their wiki page.

This seems simple enough to set up, so it's likely that your version doesn't support this feature. If you installed from the last tarball then I'd suggest you compile from the latest sources and try again.

I can confirm that this works with rev. 870 which is rTorrent 0.7.3 & libTorrent 0.11.3  Not sure if this is too useful, anyway how are you intending to use this feature?

---

### Post by AnalogRetentive on 2007-03-23
> **konsole said:**
> This seems simple enough to set up, so it's likely that your version doesn't support this feature. If you installed from the last tarball then I'd suggest you compile from the latest sources and try again.

I can confirm that this works with rev. 870 which is rTorrent 0.7.3 & libTorrent 0.11.3  Not sure if this is too useful, anyway how are you intending to use this feature?

It's such a pain in the butt to compile from the sources (ugh, dependencies of dependencies of dependencies) that if I can't get a .deb or grab it on apt-get I'm not going to bother.

As far as intended use ~ I use rTorrent on a remote server, and use apache to download files to my local computer once they are complete. Since it pre-allocates the disk space, file size isn't an indicator of completion... and the only way I can be sure is to SSH in to my server and bring the screen back up to check visually. If I had this symlinking feature working, I would potentially never have to SSH in unless I actually needed to do admin stuff.

---

### Post by stokedfish on 2007-03-23
> **AnalogRetentive said:**
> ugh, dependencies of dependencies of dependencies...
sudo apt-get build-dep rtorrent?   ;)

---

### Post by konsole on 2007-03-24
attached debs where compiled on Dapper server using svn rev. 873. The versions are libtorrent 0.11.3 and rtorrent 0.7.3

ymmv. good luck.

---

### Post by Mateo on 2007-03-25
does anyone know how to use the symlink feature to move files in and out of the watch directory?

[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Createsymboliclinkstoindicatethedownloadstate](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Createsymboliclinkstoindicatethedownloadstate)

---

### Post by ograbah on 2007-04-08
> **James6380 said:**
> [COLOR="Red"]**[SIZE="4"]Hi there I am new to all this I am building a server to look after my email and download torrents as windows sucks big time anyway. I am running 1.7ghz / 256 mb ram and 60gb HDD OS: Ubuntu i386 Server 6.10.  Anyway what files do I need to get RTORRENT installed and how do I install it. [/SIZE]**[/COLOR]

:( Sorry if I sound very dump but I have only started on linux like 2 hours ago and just starting to get my head around it all as I really enjoy learning new things.

:guitar: thanks

The link below guides you through, step by step, without the gui.
[http://news.softpedia.com/news/How-to-Install-the-Latest-Version-of-rTorrent-51166.shtml](http://news.softpedia.com/news/How-to-Install-the-Latest-Version-of-rTorrent-51166.shtml) 

Here is the quick version of what it is saying...

PREQUISITES

Before installing rTorrent, you'll need to clean your system if you have installed the version available in the repository. To do this, open a terminal and type:
```
sudo apt-get remove rtorrent libtorrent7
```

NEXT install the dependencies and prepare your system for compiling:
```
sudo apt-get install build-essential libsigc++-2.0-dev pkg-config comerr-dev libcurl3-openssl-dev libidn11-dev libkadm55 libkrb5-dev libssl-dev zlib1g-dev libncurses5 libncurses5-dev

```

INSTALLING

Now, download the libtorrent and rTorrent source packages and install them in this order. To do this, follow these instructions:
```
cd /tmp
wget http://libtorrent.rakshasa.no/downloads/libtorrent-0.11.1.tar.gz
wget http://libtorrent.rakshasa.no/downloads/rtorrent-0.7.1.tar.gz

tar xfz libtorrent-0.11.1.tar.gz
cd libtorrent-0.11.1
./configure
make
sudo make install

tar xfz rtorrent-0.7.1.tar.gz
cd rtorrent-0.7.1
./configure
make
sudo make install
```

AVOID FIREWALL

On most Linux systems, a firewall blocks if not all, then most of the ports so running a torrent client inside a locked-down machine will result in connectivity loss and low transfer rates. To avoid this, run the following command in a terminal to ensure the ports used by rTorrent will be open:
```
sudo iptables -A INPUT -p tcp --dport 6890-6999 -j ACCEPT
```

There is also a quick guide available at that link.  I am putting it in here twice, since I didn't write the guide, but enjoyed having every command all set up.  I just connected via ssh and installed everything.
[http://news.softpedia.com/news/How-to-Install-the-Latest-Version-of-rTorrent-51166.shtml](http://news.softpedia.com/news/How-to-Install-the-Latest-Version-of-rTorrent-51166.shtml)

---

### Post by Brokenrgv on 2007-04-14
dont suppose someone has done the latest yet 0.7.4 and 0.11.4 ??  if so pretty please :)

---

### Post by cybergypsy on 2007-04-17
First off I want to say thanks to Console for providing the latest rtorrent in easy to install .deb files , I tried building from source originally and had a dependency problems.

anyway

I have just upgraded from libtorrent 0.11.2 and rtorrent 0.7.2  to  libtorrent 0.11.3 and rtorrent 0.7.3 via your .deb files and it seems slower.

I have now reverted back again and its quick again.

Same torrents

Is anyone else getting this ?

---

### Post by konsole on 2007-04-18
> **cybergypsy said:**
> I have just upgraded from libtorrent 0.11.2 and rtorrent 0.7.2  to  libtorrent 0.11.3 and rtorrent 0.7.3 via your .deb files and it seems slower.

I have now reverted back again and its quick again.

Same torrents

Is anyone else getting this ?

0.7.3 is quite old and you should be using the 0.7.4/0.11.4 versions at a minimum. I can upload mine compiled from the stable release off Rakshasa's website if you want to try them.

---

### Post by cybergypsy on 2007-04-18
thanks for the offer , I got it compiled ok myself now , not sure what failing dependency was last time but it was easy this time.

happy days

cybergypsy

---

### Post by Kenzumi on 2007-04-19
Some could make debs for the new rtorrent 0.7.4/libtorrent 0.11.4 please ?

---

### Post by fernando_lopes_jr on 2007-04-19
Could someone post latest version of rtorrent / libtorrent in debian please would be much appreciated.

Thanks

---

### Post by konsole on 2007-04-20
i386 debs for 0.11.4/0.7.4

knock yourself out...

---

### Post by embeemb on 2007-04-20
I downloaded, extracted and installed both included packages. However, upon running rtorrent, i get the following:

> (12:51:45) Could not read resource file: ~/.rtorrent.rc
(12:51:45) Using 'epoll' based polling.
[Throttle off/off KB] [Rate   0.0/  0.0 KB] [Port: 6990] [U 0/0] [S 0/1/768] [F 

Any idea what's up??

---

### Post by cybergypsy on 2007-04-20
have you created a ~/.rtorrent.rc file with your settings in it ?

have a look on the rtorrent site or man page for more details

---

### Post by chomafin on 2007-04-20
> **embeemb said:**
> I downloaded, extracted and installed both included packages. However, upon running rtorrent, i get the following:
Any idea what's up??

You need to create the settings file.  Just go to : 
[http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest](http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest) : and copy the text to a file. Then save it as ~/.rtorrent.rc. Make sure that your not grabbing the numbering when you copy




> **konsole said:**
> i386 debs for 0.11.4/0.7.4

knock yourself out...
Thanks for these, they seem to work out fine on Feisty!

---

### Post by stokedfish on 2007-05-03
Thanks for the debs, works great. No problems with debs either. Schweeeet!  ;(

---

### Post by embeemb on 2007-05-03
Thanks for the help guys. It's working perfectly now. No GUI and insane dl speeds. This is exactly how I want my client to be !!

rtorrent FTW!

---

### Post by hypronix on 2007-05-08
Hey thanks a lot for this! rTorrent is the one tu rule them all [especially since it has encryption, too :) ]

---

### Post by fernando_lopes_jr on 2007-06-04
Just wandering I'm using rtorrent version 0.7.4 have there been any updates to this program, if yes could someone please post the debian. ;)

---

### Post by shirilover on 2007-06-04
0.7.4/0.11.4 are the latest stable releases posted on the rtorrent project page.
However, there are no doubt changes in the svn source.

---

### Post by lmandrake on 2007-08-04
I really love rtorrent, but sometimes all my network connections broke after a while and I can only link this to rtorrent or some nasty trackers hating it :/ Did anybody else experince this?

---

### Post by ljw1 on 2007-08-11
Hopefully someone can help, as enabling encryption gives a weird error message. I have googled the message and it does not appear to be a common problem.

rtorrent: Error in option file: ~/.rtorrent.rc:70: Variable "encryption" does not exist.

I have tried a couple of different config files from the net but the error message about encryption is still there for all of them.

Please help?

---

### Post by shirilover on 2007-08-11
I use encryption without any problems. Below is the section from my .rtorrnetrc

```

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
encryption = allow_incoming,enable_retry,prefer_plaintext

```

---

### Post by ljw1 on 2007-08-12
Tried that but still the same error message. Any other ideas? Maybe some dependencies?

---

### Post by Dmole on 2007-08-13
just incase this helps anyone; here is my rtorrent Ubuntu installation experience:

## Install dependencies (as root)
apt-get remove rtorrent libtorrent9
apt-get install build-essential subversion libtool automake autoconf libssl-dev libsigc++-2.0-dev libcurl3-openssl-dev g++ libncurses5-dev

## make a place for rtorrent svn (as root)
mkdir /opt/rtorrent
cd /opt/rtorrent
svn co svn://rakshasa.no/libtorrent/trunk

## update, make, install rtorrent (as root)
cd /opt/rtorrent/trunk
svn up
cd libtorrent
./autogen.sh
./configure
make
make install
cd ../rtorrent
./autogen.sh
./configure
make
make install

## configure rtorrent (as a user)
cp  /opt/rtorrent/trunk/rtorrent/doc/rtorrent.rc ~/.rtorrent.rc
mkdir ~/rtorrent
mkdir ~/rtorrent/session
#edit .rtorrent.rc to your liking (vim ~/.rtorrent.rc)
# more options at [http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks)

example .rc file:
~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~
# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 100

# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
max_uploads = 2

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
upload_rate = 30

# Default directory to save the downloaded torrents.
directory = /media/sda7/downloading

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = ~/rtorrent/session

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/media/sda7/Torrents/*.torrent
#schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,stop_on_ratio=100,1M,100

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no

# Port range to use for listening.
port_range = 6889-6889

# Start opening ports at a random position within the port range.
#port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
encryption = allow_incoming,enable_retry,require,require_RC4

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10

# Max number of files to keep open simultaniously.
#max_open_files = 128

# Number of sockets to simultaneously keep open.
#max_open_sockets = <no default>


# Example of scheduling commands: Switch between two ip's every 5
# seconds.
#schedule = "ip_tick1,5,10,ip=torretta"
#schedule = "ip_tick2,10,10,ip=lampedusa"

# Remove a scheduled event.
#schedule_remove = "ip_tick1"

##
## extra
##

# When the torrent finishes, it executes "mv -n <base_path> ~/Download/"
# and then sets the destination directory to "~/Download/". (0.7.7+)
on_finished = move_complete,"execute=mv,-n,$get_d_base_path=,/media/sda7/downloaded/ ;set_d_directory=/media/sda7/downloaded/"

#Every day "throttle_1" gets triggered at 01:00 and sets the download rate to unlimited, while "throttle_2" sets it to 25kb at 05:00. Using this the client may be made to perform a somewhat crude form of bandwidth scheduling. 
schedule = throttle_1,23:00:00,24:00:00,dodswnlo ad_rate=0
schedule = throttle_2,07:00:00,24:00:00,download_rate=100 


#[http://libtorrent.rakshasa.no/downloads/rtorrent_fast_resume.pl](http://libtorrent.rakshasa.no/downloads/rtorrent_fast_resume.pl).
#rtorrent_fast_resume.pl [base-directory] < original.torrent > modified.torrent
~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~



## other install guides:
#[http://libtorrent.rakshasa.no/wiki/Install](http://libtorrent.rakshasa.no/wiki/Install)
#[http://ubuntuforums.org/showpost.php?p=2422556&postcount=54](http://ubuntuforums.org/showpost.php?p=2422556&postcount=54)



yay now you (hopefully) have a up to date rtorrent installation!

---

### Post by eriksson25 on 2007-08-13
Hi, I love rtorrent, but I have one problem. When I start it in the terminal I have to use sudo rtorrent otherweise I get "rtorrent: Could not open/bind a port for listening: Permission denied"

can some one help me? Becouse I want to have it auto start and that dont work with it having to be sudo.

---

### Post by eriksson25 on 2007-08-13
> **dimitris103 said:**
> [IMG]http://s4.bitefight.gr/c.php?uid=15686[/IMG]



???????????????? dont get your reply

---

### Post by n2j3 on 2007-08-13
> **Dmole said:**
> just incase this helps anyone 

Yep, I followed your svn installation guide and it worked flawlessly. By the way, if  you already have an .rtorrent.rc configuration file from the repository 0.6.4 version it will still work with 0.7.7. , no need to re-edit anything.

---

### Post by Dmole on 2007-08-14
Some little hacks until rtorrent gains the functionality:

I haven't played with these yet but I expect I'll end up using them.
I plan to edit the webIU to be a "generate on demand" script from PHP.

...Not sure if rtorrent is actually missing anything after these hacks :)


1) rtorrent queue manager
2) rtorrent webIU
3) rtorrent rss

rtorrent queue manager
by: shaundennie at gmail.com (Shaun Dennie) Date: Sat Apr 14 01:48:01 2007 
www: N/A
```
#!/usr/bin/perl
use strict;
use File::stat;
use File::Copy;
#
# Configure for your setup
##########################
my $max_downloads = 2;
my $session_dir = "/your/session/dir";
my $watch_dir = "/your/watch/dir";
my $queue_dir = "/some/directory/to/act/as/a/queue";
##########################
my @downloading;
my $oldest_name;
my $oldest_time;
my $finfo;
while(1)
{
    opendir(SESSION, $session_dir);
    @downloading = grep(/\.torrent$/, readdir(SESSION));
    closedir(SESSION);
    if(@downloading &lt; $max_downloads)
    {
        $oldest_name = "";
        $oldest_time = 0;
        opendir(QUEUE, $queue_dir);
        foreach my $file (grep(/\.torrent$/, readdir(QUEUE)))
        {
            $file = "$queue_dir/$file";
            $finfo = stat($file);
            if($finfo-&gt; atime &lt; $oldest_time || $oldest_name eq "")
            {
                $oldest_name = $file;
                $oldest_time = $finfo-&gt;
                atime;
            }
        }
        closedir(QUEUE);
        move("$oldest_name", $watch_dir) unless($oldest_name eq "");
    }
    sleep 30;
} 

```


rtorrent webIU
by: ?? George Notaras ??
www: [http://www.g-loaded.eu/2007/06/23/rtorstat-a-simple-rtorrent-status-web-page-generator/](http://www.g-loaded.eu/2007/06/23/rtorstat-a-simple-rtorrent-status-web-page-generator/)
```
#! /usr/bin/env python
# -*- coding: utf-8 -*-
#
# rtorstat.py - A simple rtorrent status web page generator.
#
# Copyright (c) George Notaras <gnot [AT] g-loaded [DOT] eu>
#
# Project home: http://www.g-loaded.eu/2007/06/23/rtorstat-a-simple-rtorrent-status-web-page-generator/
#
# License: GPLv2

__version__ = "0.3"

import sys, os.path, glob, datetime
from string import Template

# Requirement
try:
	from bencode import bdecode
except ImportError:
	try:
		from BitTorrent.bencode import bdecode
	except ImportError:
		sys.stderr.write("%s: ERROR: Missing dependency\nbencode.py was not found in current directory or in local BitTorrent Client (Mainline) installation.\n" % sys.argv[0])
		sys.stderr.flush()
		sys.exit(1)


status_page = Template("""<html>
<head>
	<META NAME="GOOGLEBOT" CONTENT="NOARCHIVE">
	<META NAME="ROBOTS" CONTENT="NOINDEX,NOFOLLOW">
	<META HTTP-EQUIV="PRAGMA" CONTENT="NO-CACHE">
	<META HTTP-EQUIV="CACHE-CONTROL" CONTENT="NO-CACHE">
	<META HTTP-EQUIV="EXPIRES" CONTENT="Mon, 22 Jul 2000 01:01:01 GMT">
	<title>rTorrent Status</title>
</head>
<body>
	<div style="margin:20px;">
		<h2>rTorrent Status</h2>
		<pre>${pagehead}</pre>
		<br />
		<strong>Started/Stopped Torrents</strong>
		<pre>${torstarted}</pre>
		<br />
		<strong>Finished Torrents</strong>
		<pre>${torfinished}</pre>
	</div>

	<br /><br />
	<div style="width:200px; margin:20px;">
		<hr />
		<em><span style="font-size:80%;">Created with rtorstat v${version}</span></em>
	</div>

</body>
<head>
	<META NAME="GOOGLEBOT" CONTENT="NOARCHIVE">
	<META NAME="ROBOTS" CONTENT="NOINDEX,NOFOLLOW">
	<META HTTP-EQUIV="PRAGMA" CONTENT="NO-CACHE">
	<META HTTP-EQUIV="CACHE-CONTROL" CONTENT="NO-CACHE">
	<META HTTP-EQUIV="EXPIRES" CONTENT="Mon, 22 Jul 2000 01:01:01 GMT">
</head>
</html>
""")


def sz(size):
	if size < 1024**2:
		return "%.2f Kb" % (float(size)/float(1024))
	else:
		if size < 1024**3:
			return "%.2f MB" % (float(size)/float(1024**2))
		else:
			return "%.2f GB" % (float(size)/float(1024**3))

def started_stopped(state, complete):
	if complete:
		return "FINISHED"
	if state:
		return "STARTED"
	return "STOPPED"

def ignores(ignores_orders):
	if ignores_orders:
		return "(IGNORES ORDERS)"
	return ""

def get_status(torrent):
	file_output = []
	f = open(torrent)
	t_dict = bdecode(f.read())
	f.close()
	#print t_dict['rtorrent']
	#del t_dict['info']['pieces']
	#print t_dict
	t_name = t_dict['info']['name']
	try:
		t_size = sum(int(tfile['length']) for tfile in t_dict['info']['files'])
	except:
		t_size = t_dict['info']['length']	# when there is only one file in the torrent
	t_chunk_len = t_dict['info']['piece length']
	total_downloaded = t_dict['rtorrent']['chunks_done'] * t_chunk_len
	total_uploaded = t_dict['rtorrent']['total_uploaded']
	state_changed = int(t_dict['rtorrent']['state_changed'])
	t_state = t_dict['rtorrent']['state']
	t_complete = t_dict['rtorrent']['complete']
	t_ignores_orders = t_dict['rtorrent']['ignore_commands']
    
	share_ratio = 0
	complete_percent = 0

	if total_uploaded > 0 and total_downloaded > 0:
		share_ratio = float(total_uploaded)/float(total_downloaded)

	if not t_complete and total_downloaded > 0:
		complete_percent = (float(total_downloaded)/float(t_size))*100

	if t_complete:
		complete_percent = 100
		total_downloaded = t_size

	#file_output.append("-"*100)
	file_output.append("%s - %s %s:" % (t_name, started_stopped(t_state, t_complete), ignores(t_ignores_orders)))
	file_output.append( "size: %s - downloaded: %s - uploaded: %s - complete: %.2f%% - ratio: %.2f\n" % \
		( sz(t_size), sz(total_downloaded), sz(total_uploaded), complete_percent, share_ratio ) )

	if t_complete:
		ret_status = "FINISHED"
	else:
		ret_status = None

	return ret_status, "\n".join(file_output)

def add_num_to_list_items(mylist):
	for k in range(len(mylist)):
		mylist[k] = "%d. - %s" % (k+1, mylist[k])
	return mylist

def usage():
	sys.stderr.write("Usage:\n%s /path/to/session/dir/\n\n" % os.path.basename(sys.argv[0]))
	sys.stderr.flush()
	sys.exit(1)

def main():

	if "-h" in sys.argv or "--help" in sys.argv:
		usage()
	elif len(sys.argv) == 2:
		session_dir = sys.argv[1]
		if not os.path.exists(session_dir) or not os.path.isdir(session_dir):
			sys.stderr.write("ERROR: session path does not exist or is not a directory.\n\n")
			sys.stderr.flush()
			usage()
	else:
		usage()

	pagehead = []
	started_list = []
	finished_list = []

	pagehead.append("Last Update: %s\n" % datetime.datetime.now().strftime("%a, %b %d %Y, %H:%M:%S"))

	session_list = glob.glob(os.path.join(session_dir, "*.torrent"))

	for torrent in session_list:
		tor_status, tor_text = get_status(torrent)
		if tor_status == "FINISHED":
			finished_list.append(tor_text)
		else:
			started_list.append(tor_text)

	pagehead = "\n".join(pagehead)
	if started_list:
		started_list = add_num_to_list_items(started_list)
		torstarted = "\n".join(started_list)
	else:
		torstarted = "N/A"
	if finished_list:
		finished_list = add_num_to_list_items(finished_list)
		torfinished = "\n".join(finished_list)
	else:
		torfinished = "N/A"

	sys.stdout.write(status_page.substitute(pagehead=pagehead,
						torstarted=torstarted,
						torfinished=torfinished,
						version=__version__))
	sys.stdout.flush()


if __name__ == '__main__':
	main()

```


rtorrent rss
by: [email]lostnihilist@gmail.com[/email]
www: [http://libtorrent.rakshasa.no/wiki/UtilsRSSDler](http://libtorrent.rakshasa.no/wiki/UtilsRSSDler)
```
#!/usr/bin/python
# RSSDler - RSS Broadcatcher
# Copyright (C) 2007, lostnihilist
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; under version 2 of the license.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# Contact:  lostnihilist <lostnihilist@gmail.com>

import feedparser, mechanize
from BitTorrent.bencode import bdecode
import time, os, socket, cgi, codecs, re, urllib, cookielib, mimetools, mimetypes
import pickle, copy, getopt, sys, ConfigParser
from UserDict import UserDict

# # # # #
# == Globals ==
# # # # #
_VERSION = "0.1"
USER_AGENT = "RSSDler %s" % _VERSION
_configInstance = None
_sharedData = None
action = None
runOnce = None
configFile = 'config.txt'
cj = None
UMASK = 0077
MAXFD = 1024
utfWriter = codecs.getwriter( "utf-8" )
sys.stdout = utfWriter( sys.stdout, "replace" )

helpMessage="""Command Line Options:
	--run/-r: run according to the configuration file
	--runonce/-o: run only once (overrides configuration file, if set to run forever)
	--daemon/-d: run in the background, according to the configuration file (Unix-like only)
	--kill/-k: kill the daemonized instance (Unix like only)
	--config/-c specify a config file (default config.txt).

Non-standard Python libraries used:
	mechanize: http://wwwsearch.sourceforge.net/mechanize/
	feedparser: http://www.feedparser.org/
	BitTorrent: http://www.bittorrent.com (the python reference client)
	For debian based distros: "sudo apt-get install python-feedparser python-mechanize bittorrent"
	
Security Note: There are two 'eval' statements in this program, which will allow running arbitrary code. Make sure only you have write permissions in the directory you run this from/what you set workingDir to. Also make sure only you have write permissions to your configuration file. This should be sufficient protection.

Configuration File:
	There are two types of sections: global and threads. There can be as many thread sections as you wish, but only one global section. global must be named "global." Threads can be named however you wish, except 'global,' and each name should be unique. First the format:
	
	[global]
	option = argument
	option2 = argument
	[feed1]
	option3 = argument
	....
	[feed2]
	....
	
Boolean Options: 'True' is indicated by "True", "yes", or "1". "False" is indicated by "False", "no", or "0" (without the quotes)
Integer Options: Just an integer. 1, 2, 10, 1000, 2348. Not 1.1, 2.0, 999.3 or 'a'.
String Options: any string, should make sense in terms of the option being provided (e.g. a valid file/directory on disk; url to rss feed)

Global Options:
	verbose: A boolean option, defaulting to True. Set to False to disable verbose output.
	downloadDir: A string option, Default is current directory. Set to a directory in which you have write permission where downloaded files will go.
	runOnce: A boolean option, default False. Set to True to force rssdler to exit after it has scanned the configured feeds.
	minSize: An integer option. Default None. Specify, in MB, the minimum size for a download to be. Files less than this size will not be saved to disk.
	maxSize: An integer option. Default None. Specify, in MB, the maximum size for a download to be. Files greater than this size will not be saved to disk.
	log: A boolean option. Default False. Will write to a log file (specified by logFile)
	logFile: A string option. Default downloads.log. Specify a file on disk to write the log to.
	saveFile: A string option. Default savedstate.dat. Specify a file on disk to write the saved state information to. This keeps track of previously downloaded files and other 'state' information necessary to keep the program running coherently, especially between shutdown/startup
	scanMins: An integer option. Default 15. Minimum 10. Values are in minutes. The number of minutes between scans. If a feed uses the <ttl> tag, it will be respected. That is, if you have scanMins set to 10 and the site sets <ttl>900</ttl> (900 seconds; 15 mins); then the feed will be scanned every other time. 
	lockPort: An integer option. Default 8023. The port on which the savedstate.dat file will be locked for writing. Necessary to maintain the integrity of the state information.
	cookieFile: A string option. Default 'cookies.txt'. The file on disk, in Netscape Format (requires headers) that has cookie information for whatever site(s) you have set that require it.
	workingDir: A string option. Default is current directory. Only needed with -d. Set to a directory on disk. Useful to make sure you don't run this from a partition that might get unmounted. If you use the -d switch (to run as a deamon) you must have this set or the program will die.
	daemonInfo: A string option. Default daemon.info. Only needed with -d. Set to a file on disk. Daemon info will be written there so that -k and such will work. (full path over rides workingDir) 
	rss: A python "dictionary" object. Default None. Setting this option properly (that's easy) allows you to create your own rss feed of the objects you have downloaded. It's a basic feed, likely to not include links to the original files. The keys are (all are required):
		length: An integer. How many entries should the RSS feed store before it starts dropping old items. 0 would literally mean to store no items
		title: A string. The title the rss feed will carry.
		link: A string: Where the rss feed can be located. Typically an http link.
		description: A string. A short description of what the feed contains.
		filename: A string. Where to store the feed on disk.
		Example (Note the ' around every 'string' except 20, which needs to be an integer. Only place in the config where quotes of strings are necessary.):
			rss = {'length': 20, 'title': 'Recent Downloads', 'link': 'http://example.com/downloads.xml', 'description': 'Files that have recently been downloaded automatically', 'filename': '/var/www/downloads.xml'}
			
Thread options:
	link: A string option. Link to the rss feed.
	active: A boolean option. Default is True, set to False to disable checking of that feed.
	maxSize: An integer option, in MB. default is None. A thread based maxSize like in global. If set to None, will default to global's maxSize. Other values override global, including 0 to indicate no maxSize.
	minSize: An integer opton, in MB. default is None. A thread based minSize, like in global. If set to None, will default to global's minSize. Other values override global, including 0 to indicate no minSize.
	noSave: A boolean option. Default to False. If true, will remember download objects for the save processor on first run, but does not download.
	directory: A string option. Default to None. If set, overrides global's downloadDir, directory to download download objects to.
	checkTime: A sequence of tuples of three integers. Specifies scan time. Will only scan thread during the time period specified. defaults to None, which means always. 0-6 : Monday-Sunday:: 0-23 : time. Give tuples in a sequence, specified with (), of day; start time, end time.put those in a sequence, specified with [].
		e.g.: check thread only on monday from 5p to 10p: [(0, 17, 22)]
		e.g.: check thread on wednesday from 10p to 11:59p and thursday from 12a to 3a: [(2,22,23),(3,0,3)]
	regExTrue: A string (regex) option. Default None. If specified, will only download if a regex search of the download name (title key in entry dictionary of feedparser instance) returns True. This will be converted to a python regex object. Use all lower case, as the name is converted to all lower case.
	regExTrueOptions: A string option. Default None. Options (like re.IGNORECASE) to go along with regExTrue when compiling the regex object. IGNORECASE is unnecessary however.
	regExFalse: A string (regex) option. Default None. If specified, will only download if a regex search of the download name returns False. This will be converted to a python regex object. Use all lower case, as the name is converted to all lower case.
	regExFalseOptions: A string option. Default None. Options (like re.IGNORECASE) to go along with regExFalse when compiling the regex object
	postDownloadFunction: A string option. Default None. The name of a function, stored in userFunctions.py found in the current working directory (with -d, workingDir, otherwise the directory the program is started from). Must accept the following arguments (of course they can be ignored): directory the file was stored in, the filename, and the feedparser entry for that object.
	"""
		
# # # # #
#Exceptions
# # # # #
class Fatal( Exception ): 
	"""An unrecoverable error occurred, the user will need to take some action before retrying."""
	
class Warning( Exception ):
	"""An error occurred, but no action needs to be taken by the user at this time."""
	
class Locked( Exception ):
	"""An attempt was made to lock() the savefile while it was already locked."""

# # # # #
#HTML/XML/HTTP
# # # # #
def mechRetrievePage(url=None, txdata=None, txheaders=[('User-agent', USER_AGENT)], file='', pageForm='' ):
	"""txdata are either 
			1) sequence of tuples of data to be encoded into a POST request in a raw form
			2) a dictionary, length 1, key being the name of the form we want to fill, the value being like 1);
				must supply a response object to pageForm with that name, or the data will not be transmitted
		txheaders: sequence of tuples of header key, value to manually add to the request object
		files: a file location to add to form response this is untested; submitting a file without a formname in txdata
			assumes the last form on the page is the form you want to fill
		pageForm: a response object containing the page with the form we want to fill in. url argument is ignored, the page will be "clicked'
			depending on which form you tell us to click on
	"""
	global cj, opener, config
	if not cj:
		cj = mechanize.MozillaCookieJar()
		cj.load(getConfig(filename=configFile)['global']['cookieFile'])
		opener = mechanize.build_opener(mechanize.HTTPCookieProcessor(cj), mechanize.HTTPRefreshProcessor(), mechanize.HTTPRedirectHandler(), mechanize.HTTPEquivProcessor())
		mechanize.install_opener(opener)
	if pageForm:
		forms = ClientForm.ParseResponse(pageForm, backwards_compat=False)
		if type(txdata) == type({}):
			formName = txdata.keys()[0]
			txdata = txdata[formName]
			for formTry in forms:
				if formTry.name == formName:	form = formTry
		else: form = forms[-1]
		if file: form.add_file(open(file))
		if txdata:
			for formElem in txdata:
				form[formElem[0]] = formElem[1]
		request = form.click()
		if txheaders:
			for header in txheaders: request.add_header(header[0], header[1])
	elif txdata: 
		txdata = urllib.urlencode(txdata)
		if txheaders: 
			request = mechanize.Request( url, txdata )
			for header in txheaders: request.add_header(header[0], header[1])
	else:
		request = mechanize.Request( url )
		if txheaders:
			for header in txheaders: request.add_header(header[0], header[1])
	response = mechanize.urlopen( request )
	return response

def getFileSize( info, data=None ):
	"""give me the HTTP headers (info) and, if you expect it to be a torrent file, the actual file, i'll return the filesize, of type None if not determined"""
	size = None
	if re.search("torrent", info['content-type']):
		tparse = bdecode(data)
		try: size = int(tparse['info']['length'])
		except:
			try:
				size = int(0)
				for j in tparse['info']['files']:
					size += int(j['length'])
			except: 
				size = None
	else:
		try: size = int(info['content-length'])
		except:	pass
	return size

def getFilenameFromHTTP(info, url):
	"""info is an http header from the download, url is the url to the downloaded file (responseObject.geturl() )"""
	try: filename = re.findall("filename=\"(.*)\"", info['content-disposition'])[0]
	except: 
		filename = re.findall(".*/(.*)", url )[0]
		try: filename = urllib.unquote(filename)
		except: pass
	typeGuess = mimetypes.guess_type(filename)[0]
	if typeGuess in info['content-type']: pass
	else:
		try: filename += mimetypes.guess_extenstion(re.findall("(.*);", info['content-type'])[0])
		except: status("Proper file extension could not be determined for the downloaded file: %s you may need to add an extension to the file for it to work in some programs." % filename )
	return filename

def downloadFile(url, threadName, rssItemNode):
	try: data = mechRetrievePage(url)
	except: 
		return False
	dataPage = data.read()
	dataInfo = data.info()
	# could try to grab filename from ppage item title attribute, but this seems safer for file extension assurance
	filename = getFilenameFromHTTP(dataInfo, data.geturl())
	size = getFileSize(dataInfo, dataPage)
	# check size against configuration options
	if size:
		if getConfig(filename=configFile)['threads'][threadName]['maxSize'] != None: maxSize = getConfig(filename=configFile)['threads'][threadName]['maxSize']
		elif getConfig(filename=configFile)['global']['maxSize'] != None: maxSize = getConfig(filename=configFile)['global']['maxSize']
		else: maxSize = None
		if getConfig(filename=configFile)['threads'][threadName]['minSize'] != None: minSize = getConfig(filename=configFile)['threads'][threadName]['minSize']
		elif getConfig(filename=configFile)['global']['minSize'] != None: minSize = getConfig(filename=configFile)['global']['minSize']
		else: minSize = None
		if maxSize:
			maxSize = maxSize * 1024 * 1024
			if size > maxSize: 
				return True
		if minSize:
			minSize = minSize * 1024 * 1024
			if size <  minSize:
				return True
	filename = str(filename)
	filename = unicode( filename, "utf-8", "replace" )
	if getConfig(filename=configFile)['threads'][threadName]['directory']: directory = getConfig(filename=configFile)['threads'][threadName]['directory']
	else: directory = getConfig(filename=configFile)['global']['downloadDir']
	outfile = open( os.path.join(directory,  filename), "wb" )
	outfile.write( dataPage )
	outfile.close()
	if	getConfig(filename=configFile)['global']['log']:
		try: oldLog = open(getConfig(filename=configFile)['global']['logFile'], 'r').read()
		except: oldLog = ''
		timeCode = "[%4d%02d%02d.%02d:%02d]" % time.localtime()[:5]
		oldLog += "%s%s" % (timeCode, os.linesep)
		oldLog += "\tFilename: %s%s" % (filename, os.linesep)
		oldLog += "\tDirectory: %s%s" % (directory, os.linesep)
		oldLog += "\tFrom Thread: %s%s" % (threadName, os.linesep)
		open(getConfig(filename=configFile)['global']['logFile'], 'w').write(oldLog)
	if rss:
		if rssItemNode.has_key('description'): description = rssItemNode['description']
		else: description = None
		if rssItemNode.has_key('title'): title = rssItemNode['title']
		else: title = None
		pubdate = time.strftime("%a, %d %b %Y %H:%M:%S GMT", time.gmtime())
		itemLoad = {'title':title , 'description':description , 'pubDate':pubdate }
		rss.makeItemNode( itemAttr=itemLoad )
	if getConfig(filename=configFile)['threads'][threadName]['postDownloadFunction']:
		try: eval("""userFunctions.%s("%s", "%s", %s)""" % (getConfig(filename=configFile)['threads'][threadName]['postDownloadFunction'], directory, filename, rssItemNode))
		except: pass
	status( "   * saved to file: %s" % filename)
	return True
	
	
def rssparse(thread, threadName):
	"""Give me a ThreadLink object, including an rss url to a thread, I'll 
	give you back an updated ThreadLink object, and download the appropriate torrents
	based on the configuration.
	assumes feed parser will create the following attributes:
		['entries'][x]['link']
		['entries'][x]['title']
	"""
	#['link']
	ThreadLink = copy.deepcopy(thread)
	try: page = mechRetrievePage(ThreadLink['link'])
	except:	return ThreadLink
	ppage = feedparser.parse(page.read())
	if ppage['feed'].has_key('ttl') and ppage['feed']['ttl'] != '':
		saved.minScanTime[threadName] = (time.time(), int(ppage['feed']['ttl']) )
	for i in range(len(ppage['entries'])):
		#if we have downloaded before, just skip (but what about e.g. multiple rips of about same size/type we might download multiple times)
		if ppage['entries'][i]['link'] in saved.downloads: 
			continue
		# make sure it matches what we want
		if ThreadLink['regExTrue']:
			if ThreadLink['regExTrueOptions']: regExSearch = re.compile(ThreadLink['regExTrue'], eval(ThreadLink['regExTrueOptions']))
			else: regExSearch = re.compile(ThreadLink['regExTrue'])
			if not regExSearch.search(ppage['entries'][i]['title'].lower()):
				continue
		# make sure it doesn't match what we don't want
		if ThreadLink['regExFalse']:
			if ThreadLink['regExFalseOptions']: regExSearch = re.compile(ThreadLink['regExFalse'], eval(ThreadLink['regExFalseOptions']))
			else: regExSearch = re.compile(ThreadLink['regExFalse'])
			if regExSearch.search(ppage['entries'][i]['title'].lower()):
				continue
		# if we matched above, but don't want to download, register as downloaded, and then move on
		if ThreadLink['noSave']:  
			saved.downloads.append(ppage['entries'][i]['link'] )
			continue
		#nonglobaldata: ppage, 
		#make this an if/then
		if downloadFile(ppage['entries'][i]['link'], threadName, ppage['entries'][i]):
			saved.downloads.append( ppage['entries'][i]['link'] )
		else:
			saved.failedDown.append( (ppage['entries'][i]['link'], threadName, ppage['entries'][i]) )
		ThreadLink['nosave'] = False
	return ThreadLink

# # # # #
#Persistence
# # # # #
class makeRss:
	"""returns an xml document (approximately?) in line with the rss2.0 specification
	Give me a channelMeta dictionary with keys in chanMetOpt list
	goes into a dictionary, called channelMeta, that is accessed with keys being the xml element (e.g. "language" in <language>)
	and values being the text for the node. It is up to you to provide legitimate text values
	"""
	def __init__(self, channelMeta={}, load=True):
		global PrettyPrint, minidom
		try:
			if minidom: pass
		except: from xml.dom import minidom
		try:
			if PrettyPrint: pass
		except: from xml.dom.ext import PrettyPrint
		self.chanMetOpt = ['title', 'description', 'link', 'language', 'copyright', 'managingEditor', 'webMaster', 'pubDate', 'lastBuildDate', 'category', 'generator', 'docs', 'cloud', 'ttl', 'image', 'rating', 'textInput', 'skipHours', 'skipDays']
		self.itemMeta = ['title', 'link', 'description', 'author', 'category', 'comments', 'enclosure', 'guid', 'pubDate', 'source']
		self.feed = minidom.Document()
		self.rss = self.feed.createElement('rss')
		self.rss.setAttribute('version', '2.0')
		self.channel = self.feed.createElement('channel')
		self.channelMeta = channelMeta
		self.items = []
		if load == True: self.loadChanOpt()

	def loadChanOpt(self):
		keys = self.channelMeta.keys()
		if 'title' not in keys or 'description' not in keys or 'link' not in keys:
			raise Exception, "channelMeta must specify at least 'title', 'description', and 'link' according to RSS2.0 spec. these are case sensitive"
		for key, value in self.channelMeta.iteritems():
			if key in self.chanMetOpt:
				chanMet = self.makeTextNode(key, value)
				self.channel.appendChild(chanMet)
	
	def makeTextNode(self, nodeName, nodeText, nodeAttributes=[]):
		"""returns an xml text element node, with input being the name of the node, text, and optionally node attributes as a sequence
		of tuple pairs (attributeName, attributeValue)
		"""
		node = self.feed.createElement(nodeName)
		text = self.feed.createTextNode(nodeText)
		node.appendChild(text)
		if nodeAttributes:
			for attribute, value in nodeAttributes: 
				node.setAttribute(attribute, value)
		return node

	def makeItemNode(self, itemAttr={}):
		"""should have an item "child" we will be adding to that"""
		if 'title' in itemAttr.keys() or 'link' in itemAttr.keys(): pass
		else:	raise Exception, "must provide at least a title OR link for each item"
		item = self.feed.createElement('item')
		for key in self.itemMeta:
			if itemAttr.has_key(key):
				itemNode = self.makeTextNode(key, itemAttr[key])
				item.appendChild(itemNode)
		self.items.append(item)
	
	def appendItemNodes(self, pop=False):
		"""adds the items in self.items to self.channel. if pop is True, each item is removed as it is added to channel. starts at the front of the list"""
		if pop:
			while self.items: self.channel.appendChild( self.items.pop(0) )
		else:
			for item in self.items: self.channel.appendChild( item )
	
	def closeFeed(self):
		self.rss.appendChild(self.channel)
		self.feed.appendChild(self.rss)
	
	def parse(self, rawfeed=None, parsedfeed=None):
		"""give parse a raw feed (just the xml/rss file, unparsed) and it will fill in the class attributes, and allow you to modify the feed.
		Or give me a feedparser.parsed feed (parsedfeed) and I'll do the same"""
		global feedparser, time
		try:
			if time: pass
		except: import time
		try:
			if feedparser: pass
		except: import feedparser
		if rawfeed:	p = feedparser.parse(rawfeed)
		elif parsedfeed: p = parsedfeed
		else: raise Exception, "Must give either a rawfeed or parsedfeed"
		# try to make feedparser have the same dictionary items as rss item list (i.e. valid tags for RSS2.0)
		# pubdate turns into updated_parsed / updated
		if p['feed'].has_key('updated'): p['feed']['pubDate'] = p['feed']['pubdate']  = p['feed']['updated']
		elif p['feed'].has_key('updated_parsed'): 
			p['feed']['pubDate'] = p['feed']['pubdate']  = time.strftime("%a, %d %b %Y %H:%M:%S GMT", p['feed']['updated_parsed'])
		for entry in p['entries']:
			if entry.has_key('updated'): entry['pubDate'] = entry['pubdate'] = entry['updated']
			elif entry.has_key('updated_parsed'): 
				entry['pubDate'] = entry['pubdate'] = time.strftime("%a, %d %b %Y %H:%M:%S GMT", entry['updated_parsed'])
			# source, comments don't have a feed (offhand) that has these entries in them, as far as I can tell., that's ok
		for key in self.chanMetOpt:
			# annoyingly, feedparser presents the dictionary with all lower case instead of the standard camelCase.
			if p['feed'].has_key(key.lower()):
				#if key = image, we need to parse this more smartly, this will NOT work
				self.channel.appendChild(self.makeTextNode(key, p['feed'][key.lower()]))
		for entry in p['entries']:	self.makeItemNode(entry)
		
	def write(self, filename=None, file=None):
		"""if fed filename, will write and close self.feed to file at filename.
		if fed file, will write to file, but closing it is up to you"""
		global PrettyPrint
		try:
			if PrettyPrint: pass
		except: from xml.dom.ext import PrettyPrint
		if filename:
			outfile = open(filename, 'w')
			PrettyPrint(self.feed, outfile)
			outfile.close()
		if file:
			PrettyPrint(self.feed, file)

class GlobalOptions(UserDict):
	"""Represents the options for running the program as a dictionary. See helpMessage for appropriate defaults"""
	def __init__(self, verbose=True, downloadDir=os.getcwd(), runOnce=False, minSize=None, maxSize=None, log=False, logFile='downloads.log', saveFile='savedstate.dat', scanMins=15, lockPort=8023, cookieFile='cookies.txt', workingDir=os.getcwd(), daemonInfo = 'daemon.info', rss=None):
		UserDict.__init__(self)
		self['verbose'] = verbose
		self['downloadDir'] = downloadDir
		self['runOnce'] = runOnce
		self['minSize'] = minSize
		self['log'] = log
		self['logFile'] = logFile
		self['saveFile'] = saveFile
		self['scanMins'] = scanMins
		self['lockPort'] = lockPort
		self['cookieFile'] = cookieFile
		self['workingDir'] = workingDir
		self['daemonInfo'] = daemonInfo
		self['rss'] = rss
class ThreadLink(UserDict):
	"""Represents a link to an rss thread and related content. 
	Attributes:
		link: Link to the rss feed. This is the primary tool used to categorize, access threads
		active: default is True, set to False to disable thread checking
		maxSize: default is None, initializer sets to site max
		minSize: default is None, initializer sets to site min
		noSave: remember download objects for the save processor on first run, but do not download
			defaults to False
		directory: directory to download download objects to, default to None, initializer sets to site default
		checkTime: Specifies scan time. Will only scan thread during the time period specified. defaults to None, which means always. 0-6 : Monday-Sunday:: 0-23 : time. Give tuples in a sequence, specified with (), of day; start time, end time.put those in a sequence, specified with [].
			e.g.: check thread only on monday from 5p to 10p: [(0, 17, 22)]
			e.g.: check thread on wednesday from 10p to 11:59p and thursday from 12a to 3a: [(2,22,23),(3,0,3)]
		regExTrue: if specified, will only download if a regex search of the download name returns true. This will be converted to a python regex object
		regExTrueOptions: options (like re.IGNORECASE) to go along with regExTrue when compiling the regex object
		regExFalse: if specified, will only download if a regex search of the download name returns false. This will be converted to a python regex object
		regExFalseOptions: options (like re.IGNORECASE) to go along with regExFalse when compiling the regex object
		postDownloadFunction: the name of a function, stored in userFunctions.py in the installation to be called after download
		
	"""
	def __init__(self, name=None, link=None, active=True, maxSize=None, minSize=None, noSave=False, directory=None, checkTime=None, regExTrue=None, regExTrueOptions=None, regExFalse=None, regExFalseOptions=None, postDownloadFunction=None):
		UserDict.__init__(self)
		self['link'] = link
		self['active'] = active
		self['maxSize'] = maxSize
		self['minSize'] = minSize
		self['noSave'] = noSave
		self['directory'] = directory
		self['checkTime'] = checkTime
		self['regExTrue'] = regExTrue
		self['regExTrueOptions'] = regExTrueOptions
		self['regExFalse'] = regExFalse
		self['regExFalseOptions'] = regExFalseOptions
		self['postDownloadFunction'] = postDownloadFunction

class saveInfo(UserDict):
	def __init__(self, lastChecked=0, downloads=[]):
		UserDict.__init__(self)
		self['lastChecked'] = lastChecked
		self['downloads'] = downloads
		self['minScanTime'] = {}
		self['failedDown'] = []

class saveProcessor:
	def __init__(self, saveFileName="savedstate.dat"):
		"""saveFileName: location where we store persistence data
		lastChecked: seconds since epoch when we last checked the threads
		downloads: a list of download links, so that we do not repeat ourselves
		minScanTime: a dictionary, keyed by rss link aka thread name, with values of tuples (x,y) where x=last scan time for that thread,
			y=min scan time in minutes, only set if ttl is set in rss feed, otherwise respect checkTime and lastChecked
		failedDown: a list of tuples (threadname, link to download). This means that the regex, at the time of parsing, identified this file as worthy of downloading, but there was some failure in the retrieval process. Size will be checked against the configuration state at the time of the redownload attempt, not the size configuration at the time of the initial download attempt (if there is a difference)
		"""
		self.saveFileName = saveFileName
		self.lastChecked = 0
		self.downloads = []
		self.failedDown = []
		self.minScanTime = {}
		self.lockSock = None
	def save(self):
		saveFile = saveInfo()
		saveFile['lastChecked'] = self.lastChecked
		saveFile['downloads'] = self.downloads
		saveFile['minScanTime'] = self.minScanTime
		saveFile['failedDown'] = self.failedDown
		f = open(self.saveFileName, 'wb')
		pickle.dump(saveFile, f, -1)
	def load(self):
		f = open(self.saveFileName, 'rb')
		saveFile = pickle.load(f)
		self.lastChecked = saveFile['lastChecked']
		self.downloads = saveFile['downloads']
		self.minScanTime = saveFile['minScanTime']
		self.failedDown = saveFile['failedDown']
		del saveFile
	def lock( self ):
		"""Portable locking mechanism. Binds to 'lockPort' as defined in config on
		127.0.0.1.
		Raises btrsslib.Locked if a lock already exists.
		"""
		if self.lockSock:
			raise Locked
		try:
			self.lockSock = socket.socket( socket.AF_INET, socket.SOCK_STREAM )
			self.lockSock.setsockopt( socket.SOL_SOCKET, socket.SO_REUSEADDR, 1 )
			self.lockSock.bind( ('127.0.0.1', getConfig(filename=configFile)['global']['lockPort']) )
		except socket.error:
			raise Locked
	def unlock( self ):
		"""Remove an existing lock()."""
		try: self.lockSock.close()
		except socket.error: pass

def getConfig(reload=False, filename='config.txt'):
	"""Return a shared instance of the Config class (creating one if neccessary)"""
	global _configInstance
	if reload: _configInstance = None
	if not _configInstance:
		_configInstance = Config(filename)
	return _configInstance

class Config(ConfigParser.RawConfigParser, UserDict):
	def __init__(self, filename='config.txt'):
		"""
		see helpMessage
		"""
		ConfigParser.RawConfigParser.__init__(self)
		UserDict.__init__(self)
		self.read(filename)
		self['filename'] = filename
		self['global'] = GlobalOptions()
		self['threads'] = {}
		self.parse()
		self.check()
	def parse(self):
		boolOptionsGlobal = ['verbose', 'runOnce', 'log', 'active']
		boolOptionsThread = ['active', 'noSave']
		stringOptionsGlobal = ['downloadDir', 'saveFile', 'cookieFile', 'logFile', 'workingDir', 'daemonInfo']
		stringOptionsThread = ['link', 'directory', 'postDownloadFunction', 'regExTrue', 'regExTrueOptions', 'regExFalse', 'regExFalseOptions']	
		intOptionsGlobal = ['maxSize', 'minSize', 'lockPort', 'scanMins']
		intOptionsThread = ['maxSize', 'minSize']
		for option in boolOptionsGlobal:
			if option.lower() in self.options('global'): 
				try: self['global'][option] = self.getboolean('global', option)
				except: pass
				# now set by GlobalOptions()
				#except: self['global'][option] = None
		for option in stringOptionsGlobal:
			if option.lower() in self.options('global'):
				self['global'][option] = self.get('global', option)
				if self['global'][option] == '' or self['global'][option].lower() == 'none' : self['global'][option] = None
		for option in intOptionsGlobal:
			if option.lower() in self.options('global'):
				try: self['global'][option] = self.getint('global', option)
				except: pass
		if 'rss' in self.options('global'):
			try:
				rss = eval(self.get('global', 'rss') )
				if type(rss) == type( {} ): self['global']['rss'] = rss
			except: pass
		threads = self.sections()
		del threads[threads.index('global')]
		for thread in threads:
			#maybe make UserDict object here instead, so that they don't have to specify non-default values....yes, let's do that
			self['threads'][thread] = ThreadLink()
			for option in boolOptionsThread:
				if option.lower() in self.options(thread):
					try: self['threads'][thread][option] = self.getboolean(thread, option)
					except: pass
					#this is not necessary, because we set our defaults with ThreadLink()
					#except: self['threads'][thread][option] = None
			for option in stringOptionsThread:
				if option.lower() in self.options(thread):
					self['threads'][thread][option] = self.get(thread, option)
					if self['threads'][thread][option] == '' or self['threads'][thread][option].lower() == 'none': self['threads'][thread][option] = None
			for option in intOptionsThread:
				if option.lower() in self.options(thread):
					try: self['threads'][thread][option] = self.getint(thread, option)
					except: pass
					# defaults set by ThreadLink()
					#except: self['threads'][thread][option] = None
			try: 
				if 'checkTime'.lower() in self.options(thread):
					checktimepy = eval(self.get(thread, 'checkTime'))
					if type(checktimepy) == type([]) and type(checktimepy[0]) == type( () ):
						self['threads'][thread]['checkTime'] = checktimepy
			except: pass
	def check(self):
		if not self['global'].has_key('saveFile') or self['global']['saveFile'] == None:
			self['global']['saveFile'] = 'savedstate.dat'
		if not self['global'].has_key('downloadDir') or self['global']['downloadDir'] == None:
			raise Exception, "Must specify downloadDir in [global] config"
		if action == 'daemon':
			if not self['global'].has_key('workingDir') or self['global']['workingDir'] == None:
				raise Exception, "Must specify workingDir in [global] config for daemon"
		if not self['global'].has_key('runOnce') or self['global']['runOnce'] == None:
			self['global']['runOnce'] = False
		if not self['global'].has_key('scanMins') or self['global']['scanMins'] == None:
			self['global']['scanMins'] = 15
		if self['global'].has_key('scanMins') and self['global']['scanMins'] < 10: self['global']['scanMins'] = 15
		if not self['global'].has_key('cookieFile') or self['global']['cookieFile'] == None or self['global']['cookieFile'] == '':
			self['global']['cookieFile'] = 'cookies.txt'
		if not self['global'].has_key('lockPort') or self['global']['lockPort'] == None:
			self['global']['lockPort'] = 8023
		if self['global'].has_key('log') and self['global']['log']:
			if not self['global'].has_key('logFile') or self['global']['logFile'] == None:
				self['global']['logFile'] = 'downloads.log'
	def save(self):
		for key, value in self['global'].iteritems():
			self.set('global', key, value)
		for thread in self['threads'].keys():
			for key, value in self['threads'][thread].iteritems():
				self.set(thread, key, value)
		fd = open(self['filename'], 'w')
		self.write(fd)
		fd.close()



# # # # #
# User/InterProcess Communication
# # # # #
class SharedData:
	"""Mechanism for sharing data. Do not instantiate directly,
	use getSharedData() instead."""
	def __init__( self ):
		self.scanning = False	# True when scan in progress
		self.scanoutput = ""	# output of last scan
		self.exitNow = False	# should exit immediatley if this is set

def getSharedData():
	"""Return a shared instance of SharedData(), creating one if neccessary."""
	global _sharedData
	if not _sharedData:
		_sharedData = SharedData()
	return _sharedData

def getVersion():
        global _VERSION
        return _VERSION

def status( message ):
	"""Log status information, writing to stdout if config 'verbose' option is set."""
	sharedData = getSharedData()
	if getConfig(filename=configFile)['global']['verbose']:
		utfWriter = codecs.getwriter( "utf-8" )
		out = utfWriter( sys.stdout, "replace" )		
		out.write( message )
		out.write( os.linesep )
		out.flush()
	sharedData.scanoutput += message + os.linesep

def killDaemon( pid ):
	while True:
		saved = saveProcessor()
		try:
			saved.lock()
			saved.unlock()
			break
		except:
			del saved
			print "Save Processor is in use, waiting for it to unlock"
			time.sleep(2)
	os.kill(pid,9)

# # # # #
#Daemon
# # # # #
def createDaemon():
	"""Detach a process from the controlling terminal and run it in the
	background as a daemon.
	"""
	try:		pid = os.fork()
	except OSError, e:
		raise Exception, "%s [%d]" % (e.strerror, e.errno)

	if (pid == 0):	# The first child.
		os.setsid()
		try:
			pid = os.fork()	# Fork a second child.
		except OSError, e:
			raise Exception, "%s [%d]" % (e.strerror, e.errno)

		if (pid == 0):	# The second child.
			 os.chdir(getConfig(filename=configFile)['global']['workingDir'])
			 os.umask(UMASK)
		else:
			# exit() or _exit()?  See below.
			 os._exit(0)	# Exit parent (the first child) of the second child.
	else:
		os._exit(0)	
	import resource		# Resource usage information.
	maxfd = resource.getrlimit(resource.RLIMIT_NOFILE)[1]
	if (maxfd == resource.RLIM_INFINITY):
		maxfd = MAXFD
   # Iterate through and close all file descriptors.
	for fd in range(0, maxfd):
		try:
			 os.close(fd)
		except OSError:	# ERROR, fd wasn't open to begin with (ignored)
			pass
	os.open(REDIRECT_TO, os.O_RDWR)	# standard input (0)
	os.dup2(0, 1)			# standard output (1)
	os.dup2(0, 2)			# standard error (2)
	return(0)

def callDaemon():
	retCode = createDaemon()
	
	# The code, as is, will create a new file in the root directory, when
	# executed with superuser privileges.  The file will contain the following
	# daemon related process parameters: return code, process ID, parent
	# process group ID, session ID, user ID, effective user ID, real group ID,
	# and the effective group ID.  Notice the relationship between the daemon's 
	# process ID, process group ID, and its parent's process ID.
	
	procParams = """
return code = %s
process ID = %s
parent process ID = %s
process group ID = %s
session ID = %s
user ID = %s
effective user ID = %s
real group ID = %s
effective group ID = %s
""" % (retCode, os.getpid(), os.getppid(), os.getpgrp(), os.getsid(0),
	os.getuid(), os.geteuid(), os.getgid(), os.getegid())
	
	try: open( os.path.join(getConfig(filename=configFile)['global']['workingDir'], getConfig(filename=configFile)['global']['daemonInfo']), 'w').write(procParams + "\n")
	except: raise Exception, "Could not write to, or not set, daemonInfo"

def signal_handler(signal, frame):
	while True:
		s = saveProcessor()
		try:
			s.lock()
			s.unlock()
			break
		except:
			del s
			status("Save Processor is in use, waiting for it to unlock")
			time.sleep(1)
	sys.exit()

# # # # #
#Running
# # # # #
def checkSleep( totalTime ):
	sharedData = getSharedData()
	steps = totalTime / 10
	for n in xrange( 0, steps ):
		time.sleep( 10 )
		if sharedData.exitNow:
			raise SystemExit

def run():
	"""Provides main functionality -- scans threads."""
	global saved, config, rss
	config = getConfig(filename=configFile, reload=True)
	saved = saveProcessor(getConfig(filename=configFile)['global']['saveFile'])
	try:
		saved.lock()
	except Locked:
		raise Warning, "Savefile is currently in use."
	try: saved.load()
	except: print "didn't load saveProcessor"
	if getConfig(filename=configFile)['global']['runOnce']:
		if saved.lastChecked > ( int(time.time()) - (60*10) ):
			raise Warning, "Minimum 10 minutes between thread scans."
	else:
		if saved.lastChecked > ( int(time.time()) - (getConfig(filename=configFile)['global']['scanMins']*60) ):
			raise Warning, "Threads have already been scanned."
	if saved.failedDown:
		status("Scanning previously failed downloads")
		for failureUrl, failureName, failureRss in  saved.failedDown:
			status("  Attempting to download %s" % failureUrl)
			if downloadFile(failureUrl, failureName, failureRss):
				status("  Success!")
				del saved.failedDown.index[ (failureUrl, failureName, failureRss) ]
			else:
				status("  Failure" % failureUrl)
	status( "Scanning threads" )
	# (dayOfWeek, hour)
	timeTuple = time.localtime().tm_wday, time.localtime().tm_hour
	rss = None
	if getConfig(filename=configFile)['global']['rss']:
		if getConfig(filename=configFile)['global']['rss']['filename']:
			if os.path.isfile( getConfig(filename=configFile)['global']['rss']['filename'] ):
				rss = makeRss(load=False)
				rssDataFile = open( getConfig(filename=configFile)['global']['rss']['filename'], 'r')
				rssData = rssDataFile.read()
				rssDataFile.close()
				rss.parse(rawfeed=rssData)
			else:
				loadRss ={}
				for key, value in getConfig(filename=configFile)['global']['rss'].iteritems():
					if key == 'title' or key == 'description' or key == 'link':
						loadRss[key] = value
				rss = makeRss(channelMeta=loadRss, load=True)
	for key in getConfig(filename=configFile)['threads'].keys():
		if getConfig(filename=configFile)['threads'][key]['active'] == False:	continue	# ignore inactive threads
		# if they specified a checkTime value, make sure we are in the specified range
		if getConfig(filename=configFile)['threads'][key]['checkTime'] != None:
			toContinue = True
			for timeCheck in getConfig(filename=configFile)['threads'][key]['checkTime']:
				timeLess = timeCheck[0], timeCheck[1]
				timeMore = timeCheck[0], timeCheck[2]
				if timeLess <= timeTuple <= timeMore:
					toContinue = False
					break
			if toContinue: continue
		if saved.minScanTime.has_key(key) and saved.minScanTime[key][0]  > ( int(time.time()) - saved.minScanTime[key][1]*60 ):
				status("RSS feed has indicated that we should wait greater than the scan time you have set in your configuration. Will try again at next configured scantime")
				continue
		status( "   * finding new downloads in thread %s" % key )
		if getConfig(filename=configFile)['threads'][key]['noSave'] == True:
			status( "     (not saving to disk)")
		try: config['threads'][key] = rssparse(getConfig(filename=configFile)['threads'][key], threadName=key)	
		except IOError, ioe: raise Fatal, "%s: %s" % (ioe.strerror, ioe.filename)
	if rss:
		while len(rss.items) > int(getConfig(filename=configFile)['global']['rss']['length']):
			rss.items.pop(0)
		rss.appendItemNodes()
		rss.closeFeed()
		rss.write(filename=getConfig(filename=configFile)['global']['rss']['filename'])
	saved.lastChecked = int(time.time()) -30
	saved.save()
	saved.unlock()
	config.save()

def main( runOnce=False ):
	config = getConfig(filename=configFile)
	sharedData = getSharedData()
	sharedData.scanoutput = ""
	if not runOnce:
		runOnce = getConfig(filename=configFile)['global']['runOnce']
	while True:
		try:
			sharedData.scanoutput += os.linesep * 2
			sharedData.scanning = True
			status( "[Waking up] %s" % time.asctime() )
			startTime = time.time()
			run()
			status( "Processing took %d seconds" % (time.time() - startTime) )
		except Warning, (message,):
			status( u"Warning: %s" % message )
		except Fatal, (message,):
			status( u"Error: %s" % message )
			sharedData.scanning = False
			raise SystemExit
		sharedData.scanning = False
		if runOnce:
			status( "[Complete] %s" % time.asctime() )
			break
		status( "[Sleeping] %s" % time.asctime() )
		elapsed = time.time() - saved.lastChecked
		#checkSleep has a 10 second resolution, let's sleep for 9, just to be on the safe side
		time.sleep(9)
		if  getConfig(filename=configFile)['global']['scanMins'] * 60 < time.time() - saved.lastChecked: checkSleep ( getConfig(filename=configFile)['global']['scanMins'] * 60 - elapsed )
		else: checkSleep( getConfig(filename=configFile)['global']['scanMins'] * 60 )
	
	

#if we lock saved before calling kill, it will be locked and we will never get to an unlock state which is our indicator that it is ok to kill.
try: 
	(argp, list) =  getopt.gnu_getopt(sys.argv[1:], "drokc:h", longopts=["daemon", "run", "runonce", "kill", "config=", "help"])
except	getopt.GetoptError:
		sys.stderr.write(helpMessage)
		sys.exit(1)

for param, argum in argp:
	if param == "--daemon" or param == "-d":	action = "daemon"		
	elif param == "--run" or param == "-r": action = "run"
	elif param == "--runonce" or param == "-o":
		action = "run"
		runOnce = True
	elif param == "--kill" or param == "-k":
		action = "kill"
		killData = open(os.path.join(getConfig(filename=configFile)['global']['workingDir'], getConfig(filename=configFile)['global']['daemonInfo']), 'r')
		for pidWanted in killData.readlines():
			pidWanted = pidWanted.strip()
			if pidWanted.startswith('process ID ='):
				pid = int(pidWanted.split('=')[-1].strip())
				break
		killDaemon(pid)
		open(os.path.join(getConfig(filename=configFile)['global']['workingDir'], getConfig(filename=configFile)['global']['daemonInfo']), 'w').write('')
		sys.exit()
	elif param == "--config" or param == "-c": configFile = argum
	elif param == "--help" or param == "-h": print helpMessage


if action == "run":
	status( "--- RssDler %s" % getVersion() )
	if os.getcwd() != getConfig(filename=configFile)['global']['workingDir']: os.chdir(getConfig(filename=configFile)['global']['workingDir'])
	try: import userFunctions
	except: userFunctions = None
	#this just isn't working quite right. PROBABLY (maybe?) has something to do with the "run twice" problem that i understand not at all.
##	import signal
##	signal.signal(signal.SIGINT, signal_handler)
	if runOnce != None:
		main(runOnce)
	else: main()
elif action == "daemon":
	#call daemon
	if (hasattr(os, "devnull")):
		REDIRECT_TO = os.devnull
	else:
		REDIRECT_TO = "/dev/null"
	config = getConfig(filename=configFile)
	status( "--- RssDler %s" % getVersion() )
	if os.getcwd() != getConfig(filename=configFile)['global']['workingDir']: os.chdir(getConfig(filename=configFile)['global']['workingDir'])
	callDaemon()
	try: import userFunctions
	except: userFunctions = None
##	import signal
##	signal.signal(signal.SIGINT, signal_handler)
	main()

```

---

### Post by Dmole on 2007-08-14
> **n2j3 said:**
> no need to re-edit anything.

well that is unless you want to use a new feature... which would be the main reason for upgrading in my case (I wanted to add the moving on completion feature).

Glad it worked for you :)

---

### Post by Brokenrgv on 2007-08-14
anyone got the latest debs out for the last stable release ?

---

### Post by fernando_lopes_jr on 2007-08-17
Does anyone have the the latest debs of rtorrent    
* libtorrent-0.11.6.tar.gz
* rtorrent-0.7.6.tar.gz  
Could you please share it?

---

### Post by Aberrix on 2007-08-20
^ Yes, debs for the current version would be highly, HIGHLY appreciated!

thanks in advance.

**update:** nevermind, used [this guide](http://ubuntuforums.org/showthread.php?p=3221915) to get the the newest stable version, worked flawless!

---

### Post by eriksson25 on 2007-08-22
Hi, cant get my move on complete to work, get this error

Download event action failed: Command "set_d_directory" does not exist.


This is my .rc

```

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 300
upload_rate = 30

# Default directory to save the downloaded torrents.
directory = /home/eriksson25/Temp/torrents/downloads

# Default session directory.
session = /home/eriksson25/Temp/torrents/sessions

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/eriksson25/Temp/torrents/torrentfiles/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
schedule = low_diskspace,5,60,close_low_diskspace=100M

#Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,stop_on_ratio=200,200M,2000

# Port range to use for listening.
port_range = 500-510

# Start opening ports at a random position within the port range.
port_random = no

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

# When the torrent finishes, it executes "mv -n <base_path> ~/Download/"
# and then sets the destination directory to "~/Download/". (0.7.7+)
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/eriksson25/Temp/torrents/Done/ ;set_d_directory=/home/eriksson25/Temp/torrents/Done/"
```

Can any one help me?

---

### Post by shirilover on 2007-08-22
> **eriksson25 said:**
> Hi, cant get my move on complete to work, get this error

Download event action failed: Command "set_d_directory" does not exist.


Can any one help me?

[quote=http://libtorrent.rakshasa.no/]Renamed all commands from e.g "get_d_*" to "d.get_*".[/quote]

try renaming set_d_directory to d.set_directory

---

### Post by ge5239 on 2007-09-01
> **Aberrix said:**
> ^ Yes, debs for the current version would be highly, HIGHLY appreciated!

thanks in advance.

**update:** nevermind, used [this guide](http://ubuntuforums.org/showthread.php?p=3221915) to get the the newest stable version, worked flawless!

./me 's asking too, again (did once before ;D).

anyone, by any chance, that could help with making debs ?

edit; nevermind, decided to try that guide and what?! It was actually easy doing it ;) 
thankles, and please ignore my post.

---

### Post by chomafin on 2007-09-13
I'm Looking around at the various web GUI's for rTorrent, and i ran across this one.
RTC: 
[[IMG]http://img501.imageshack.us/img501/4066/rtorrentim3.th.png[/IMG]]("http://img501.imageshack.us/img501/4066/rtorrentim3.png")

[http://img501.imageshack.us/img501/4066/rtorrentim3.png](http://img501.imageshack.us/img501/4066/rtorrentim3.png)


Does anyone know anything about it?  I came across it on a german forum (and I don't speak german) but they simply post the name RTC and a screen shot.. no link.  Has anyone else ran across this?

The German post for reference : [http://www.vdr-portal.de/board/thread.php?postid=641823#post641823](http://www.vdr-portal.de/board/thread.php?postid=641823#post641823)

Thanks

---

### Post by C01eMaN on 2007-10-13
> **eriksson25 said:**
> Hi, I love rtorrent, but I have one problem. When I start it in the terminal I have to use sudo rtorrent otherweise I get "rtorrent: Could not open/bind a port for listening: Permission denied"

can some one help me? Becouse I want to have it auto start and that dont work with it having to be sudo.

i wrecked my brains about that for about a week...

just use a port above 1024

its so simple:lolflag:

Mr.C

---

### Post by karvec on 2007-11-13
[http://folk.ntnu.no/alexanbj/linux/](http://folk.ntnu.no/alexanbj/linux/)

Latest version of rTorrent + libTorrent, used checkinstall to create them..

May have to install libcurl-openssl-dev to install, otherwise you should be good to go.

(sudo apt-get install libcurl-openssl-dev)

Mmkay.

Hope you guys like em, it's based on unstable .7.9 and .11.9

---

### Post by Dmole on 2008-01-08
rtorrent 7.9 went and put stuff in the wrong place

so do this:

```
sudo cp -rf /usr/local/bin/*  /usr/bin/
sudo cp -rf /usr/local/include/torrent  /usr/include/
sudo cp -rf /usr/local/lib/*  /usr/lib/
sudo cp -rf /usr/local/share/man/man1/rtorrent.1  /usr/share/man/man1/

```

after the normal (as root):

```
apt-get -y autoremove
apt-get -y install libncurses5-dev automake libsigc++-2.0-dev libcurl4-openssl-dev libtool
apt-get -y remove rtorrent libtorrent
mkdir /opt/rtorrent
svn co svn://rakshasa.no/libtorrent/trunk
cd /opt/rtorrent/trunk
svn up
cd ./libtorrent
./autogen.sh
./configure
make clean
nice -n 19 make
make install
cd ../rtorrent
./autogen.sh
./configure
make clean
nice -n 19 make
make install

```

---

### Post by stokedfish on 2008-02-21
no reliable debs for newest version?

---

### Post by Borbus on 2008-02-21
rtorrent is so easy to build yourself... But I could supply x86 debs from a Debian box... should work with Ubuntu.

---

