---
title: "Where can i store files that i can use wget to retrieve them?"
date: 2018-01-25
forum: General Help
---

### Post by eddie552 on 2018-01-25
Just learned about wget and im trying to chain commands together so setting up a new computer is easy to install all my stuff

An example of one of my scripts would be auto installing adobe acrobat

```
[COLOR=#000000][FONT=Arial]WINEARCH=win32 WINEPREFIX=~/.adobe winecfg && wget  [/FONT][/COLOR][[COLOR=#1155CC][FONT=Arial]https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks[/FONT][/COLOR]]("https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks")[COLOR=#000000][FONT=Arial] -P ~/Downloads/ && sudo chmod +x ~/Downloads/winetricks && env WINEPREFIX=~/.adobe sh ~/Downloads/winetricks mspatcha && sudo apt-get install cabextract && wget ftp://[/FONT][/COLOR][[COLOR=#1155CC][FONT=Arial]ftp.adobe.com/pub/adobe/reader/win/AcrobatDC/1502320053/AcroRdrDC1502320053_en_US.exe[/FONT][/COLOR]]("http://ftp.adobe.com/pub/adobe/reader/win/AcrobatDC/1502320053/AcroRdrDC1502320053_en_US.exe")[COLOR=#000000][FONT=Arial] -P ~/Downloads && WINEPREFIX=~/.adobe wine ~/Downloads/[/FONT][/COLOR][[COLOR=#1155CC][FONT=Arial]AcroRdrDC1502320053_en_US.exe[/FONT][/COLOR]]("http://ftp.adobe.com/pub/adobe/reader/win/AcrobatDC/1502320053/AcroRdrDC1502320053_en_US.exe")[COLOR=#000000][FONT=Arial] && WINEPREFIX=~/.adobe wineboot && WINEPREFIX=~/.adobe winecfg[/FONT][/COLOR]
```


Some websites dont let me use wget to download the .deb file
So i am downloading the .deb file and trying to host it somewhere
Apparently i cannot use wget to download files from services such as google drive and mega... so my question where can i store .deb files online that i can use wget to access when using a script.. doesnt have to be private 

Thanks in advance

---

### Post by TheFu on 2018-01-26
wget supports plain http, https and plain ftp, without javascript.

That means you can setup a web server anywhere and store the files there under almost any web-server setup. Just needs to support static files.  That would include any $4/month hosting plan or a raspberry-pi running in your home with a $20 HDD.

Owncloud, Nextcloud can be used too - which you can self-host or use a paid host. Either will run on a $35 raspberry pi for a 5 person setup.

But if you run the system, why not use rsync?  rsync works over ssh or from locally connected storage (like a flash drive). Over the internet, it is secure with ssh-keys (don't use passwords over the internet).  Anything you want to place in the HOME directory on a new system, rsync can pull.  

If you are setting up a system a few times a month, look into Ansible.

wget is pretty nice, BTW.  I use it to get Linux distros from local university online storage.  It can also be used to record TV from an HDHR4 network tuner. ;)

There might be an easier method to keep things updated.

Most places that would have a deb package would provide a PPA.  These integrate into the package management system on your Ubuntu machines.  You can make your own clone of a PPA or even just a local cache using apt-cache-ng (there are a few other options).  That way, the packages are updated as needed, automatically.  I've been running apt-cacheng internally here for many years.  The first time a package is needed, it gets pulled and stored.  Every system uses that cache, so as it is needed over and over, then other systems get it from a local place, just like using the formal repository.  As packages expire, they are removed.  It can be manual or automatic.

For Windows stuff, I've been using ninite as the easier way to keep the most commonly used programs up to date.  It is manual to run the custom ninite package that knows about my 5-10 programs, but they are silent installs and updates.

BTW, you don't need to set WINEPREFIX over and over and over.  Just use **export WINEPRIFIX=** at the start of the script, then run the other commands as normal.

```
export WINEARCH=win32 
export WINEPREFIX=~/.adobe 

```
I'd write the script differently so it was more readable/maintainable too and I'd do all the Linux stuff first, then the WINE stuff.

Actually, I'd try to use Ansible. [https://github.com/ypid/ansible-wine](https://github.com/ypid/ansible-wine)
Getting the current Acrobat reader is something a little harder. I suppose you manually visit the download site and update the file version?  Is having THE approved, exact Acrobat reader really worth the effort?  There are lots of Linux-based options - xournal, evince, and a few others.  If they deal with the PDF standard you need, fine.  Of course, there are times when only the real Reader will do and there isn't much choice, but that hasn't happened much to me the last 5 yrs.

Anyway, just a few other options to consider.  There are hundreds of different ways to solve most things on Linux.

---

### Post by Impavidus on 2018-01-26
Note that you can't simply put someone else's .deb file on a server where everybody can reach it. They may want it to be available only though their own server. So if you want to use wget, use your private server at home without access from outside or you need some authentication. rsync seems easier.

---

### Post by mail-2o on 2018-02-21
> **TheFu said:**
> ...Owncloud, Nextcloud can be used too - which you can self-host or use a paid host. Either will run on a $35 raspberry pi for a 5 person setup.As a recent convert to NextCloud, setup on a Rasp Pi + 1TB Ext drive, in a switch on and ignore location, I would recommend it.

However, for anyone having trouble installing a Nextcloud Client, through Synaptic or apt-get, these tips helped me to get it up and running.
 
On the Nextcloud website ([https://launchpad.net/~nextcloud-devs/+archive/ubuntu/client](https://launchpad.net/~nextcloud-devs/+archive/ubuntu/client)), it isrecommended that you use```
add-apt-repository
```but you will quickly find that that does not work. After a considerable amount of time wasted, searching, I came across this:```
sudo apt-get install software-properties-common

sudo apt-get install python3-software-properties

sudo add-apt-repository ppa:nextcloud-devs/client

sudo apt-get update
```and low and behold, Nextcloud installs and launches perfectly through Synaptic. 

(I&#8217;m using Nextcloud in preference to something like Dropbox because I&#8217;m trying to shrink my desktop by using tiny ARM SBCs and am hitting a few minor problems in doing so, but am getting there. Also Nextcloud keeps your files local, and there appears to be no size restriction. Especially useful if your hard drive fails unexpectedly. They do!)

Trying Elementary OS 16.04 LTS, after a hard drive failure on my laptop.

---

