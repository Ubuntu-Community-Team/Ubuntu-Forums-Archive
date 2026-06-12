---
title: "Performance problem kubuntu 8.04 [expert/urgent]"
date: 2008-04-24
forum: General Help
---

### Post by macic on 2008-04-24
Hi there!

I'm new but I'm learning quite fast. I'm a PHP Developer and recently installed Kubuntu 8.04 RC, coz my XP was really slow. However I do find all the applications on Kubuntu to load slower than on XP which is quite strange to me.

I believe Kubuntu should be much faster than XP shouldn't it?! Is it for You? Please answer!

My configuration:
2.4 ghz celeron
1256 ram
160 gb disc (30 for linux for now (only 512 swap (installed it when had 256 ram only))
old old 5200 gfx nvidia

I'm not sure but things that may slow down my Kubuntu are:
- wide screen monitor (1440:960 or something like that) resolution? Changing to lower resolution should help?
- swap size? (I don't think so, as when ram is quite free, the applications are still loading slow
- nvidia card drivers? 
- kde is using too much of CPU? (what to turn off and how, what else to try instead of kde and how?)


I will be honest, I love Kubuntu but I want it to work at least as fast as XP. By "to work" I mean: loading applications and working on them.

Im using Eclipse with PDT on LAMP environment and I'm 100000% sure the problem isn't with Eclipse itself. Firefox also is loading like 25-30 seconds before showing the screen which is like 2x slower then on XP (which is 3 years old and barely working!!!!)

I can handle bash commands etc and I'm looking to some EXPERT help. I'm not a computer newbie trust me, but yes I'm an unix newbie.

Really looking for some help as it's important for me to stay at Kubuntu.

---

### Post by ajgreeny on 2008-04-24
Should be faster than that.  How long does it take to load OO.o from a cold start?  That is often a good example of a slow machine.  On mine with gnome ubuntu 7.10 firefox takes about 4 secs and with the quickstart enabled for OO.o it takes only 4 secs as well.  I have a sempron 2400+ and 1GB ram with an ati 9200SE card so it can't be just a hardware problem in your case, I don't think.

---

### Post by macic on 2008-04-24
> **ajgreeny said:**
> Should be faster than that.  How long does it take to load OO.o from a cold start?  That is often a good example of a slow machine.  On mine with gnome ubuntu 7.10 firefox takes about 4 secs and with the quickstart enabled for OO.o it takes only 4 secs as well.  I have a sempron 2400+ and 1GB ram with an ati 9200SE card so it can't be just a hardware problem in your case, I don't think.

Hi,

20-30 secs for OO.o from a cold start. about 10 at xp. What do You think about reasons for working that slow posted by me above?

---

### Post by DMK62 on 2008-04-24
Hi

Are you running the kde 3.5.9 or 4.0 remix version of Kubuntu 8.04 ? 

Have you run the top command from the konsole ( terminal ) ? Try running the command 

top -i 

It will let you know how many processes are running and the amount of resources being used by them. Use just top without the -i if you want a full list of processes.

I am not currently running 8.04 but one thing that did slow things down on 7.10 was the search daemon strigi. It's enabled by default and besides the load on the system when indexing it creates fairly large files. I prefer using kfind for searches. I used the following command in 7.10 to remove it

sudo apt-get remove strigi-*

Dale

---

### Post by macic on 2008-04-24
> **DMK62 said:**
> Hi

Are you running the kde 3.5.9 or 4.0 remix version of Kubuntu 8.04 ? 

Have you run the top command from the konsole ( terminal ) ? Try running the command 

top -i 

It will let you know how many processes are running and the amount of resources being used by them. Use just top without the -i if you want a full list of processes.

I am not currently running 8.04 but one thing that did slow things down on 7.10 was the search daemon strigi. It's enabled by default and besides the load on the system when indexing it creates fairly large files. I prefer using kfind for searches. I used the following command in 7.10 to remove it

sudo apt-get remove strigi-*

Dale

Hi,
While running top -i I got only 3 app and firefox gets: ram 6% and cpu 7% and that's the bigger one. Nothing strange. I've removes strigi anyway:P and guess what, seems a little faster! :D :guitar: Thank You :

---

### Post by macic on 2008-04-24
sry double post

---

### Post by DMK62 on 2008-04-24
Hi

Good to hear that it sped things up a bit.

Have you installed the proprietary nvidia drivers for your card ? The 5200 series is supported by the latest nvidia driver ( glx-new ). If I remember correctly from testing the beta that it can be installed by going to System then Drivers Manager. If not there try System Settings and Monitor and Displays.

You will also want to install nvidia-settings since you have a widescreen monitor.

sudo apt-get install nvidia-settings 

if it has dependencies then install those and then install nvidia-settings.

To launch nvidia-settings use konsole

kdesu nvidia-settings

The proprietary drivers will give you 3d accleration as well as 2d which should make things a lot snappier.

On a side note you may find you prefer Konqueror as your default file manager and dolphin is the default in 7.10 and 8.04. If you want Konqueror to be the default open Konqueror and in the configuration options in Konqueror you will see File Associations and Inode on the right. Expand Inode and select Directory and move up Konqueror to the top of the list. Just my personal opinion but Konqueror is still more powerful than Dolphin.

Dale

---

### Post by macic on 2008-04-24
> **DMK62 said:**
> Hi

Good to hear that it sped things up a bit.

Have you installed the proprietary nvidia drivers for your card ? The 5200 series is supported by the latest nvidia driver ( glx-new ). If I remember correctly from testing the beta that it can be installed by going to System then Drivers Manager. If not there try System Settings and Monitor and Displays.

You will also want to install nvidia-settings since you have a widescreen monitor.

sudo apt-get install nvidia-settings 

if it has dependencies then install those and then install nvidia-settings.

To launch nvidia-settings use konsole

kdesu nvidia-settings

The proprietary drivers will give you 3d accleration as well as 2d which should make things a lot snappier.

On a side note you may find you prefer Konqueror as your default file manager and dolphin is the default in 7.10 and 8.04. If you want Konqueror to be the default open Konqueror and in the configuration options in Konqueror you will see File Associations and Inode on the right. Expand Inode and select Directory and move up Konqueror to the top of the list. Just my personal opinion but Konqueror is still more powerful than Dolphin.

Dale

Hi Dale,

Once again thank You very much. I've done all that and seems that now my kubuntu is faster than xp :)

Radek

---

