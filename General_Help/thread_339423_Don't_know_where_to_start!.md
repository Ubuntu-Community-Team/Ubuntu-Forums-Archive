---
title: "Don't know where to start!"
date: 2007-01-15
forum: General Help
---

### Post by Neil Lundy on 2007-01-15
Hello all,

I recently installed a version of Ubuntu on my machine and am having major problems with it. Basically, I don't know what version it is but I downloaded it about one year ago and at the time it was the current version. The machine that I have installed this on has no built in wireless card, which is a problem as I cant update the version of Ubunto that I have installed. So, I bought a D Link PCMCIA wireless card, inserted it, and nothing happened. It came with a CD but I looked in there and it says nothing about Linux. So basically, I'm stuck. 

If anyone could help me with this problem I would be very greatful as I really don't know what to do next. I have been reading a few posts and have been getting nowhere. I'm new with linux so go easy on me.

Thanks to all in advance!

---

### Post by Choad on 2007-01-15
what version.... godd question!

i think that might be a thus-far overlooked feature

you can find out one way: open a terminal (applications > accessories > terminal) and type in

gedit /etc/apt/sources.list

then have a look through that file. you should see one of the following words crop up repeatedly

hoary
breezy
dapper
edgy

and that will tell you which version. 

heres (a small section of) mine

```
#deb cdrom:[Ubuntu 6.10 **_Edgy** Eft_ - Release i386 (20061025)]/ **edgy** main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ **edgy** main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ **edgy** main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ **edgy**-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ **edgy**-updates main restricted universe multiverse
```
[I]
edit: or read the next post lol[/I]

as for your wireless card, type in to your console

lspcmcia

and post the output here

---

### Post by ardchoille42 on 2007-01-15
> **Neil Lundy said:**
> Hello all,

I recently installed a version of Ubuntu on my machine and am having major problems with it. Basically, I don't know what version it is but I downloaded it about one year ago and at the time it was the current version. The machine that I have installed this on has no built in wireless card, which is a problem as I cant update the version of Ubunto that I have installed. So, I bought a D Link PCMCIA wireless card, inserted it, and nothing happened. It came with a CD but I looked in there and it says nothing about Linux. So basically, I'm stuck. 

If anyone could help me with this problem I would be very greatful as I really don't know what to do next. I have been reading a few posts and have been getting nowhere. I'm new with linux so go easy on me.

Thanks to all in advance!

First of all, you can find which version of Ubuntu it is but opening a terminal and running:

```

lsb_release -a

```

Secondly, I would recommend downloading and installing a more recent version of Ubuntu as it will probably fix a lot of things during the install as well as recognise more hardware.. possibly including your new wireless card.

You can find the download links for Ubuntu here:

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

Is it possible for you to get on another computer and download the latest Ubuntu?

---

### Post by jem7v on 2007-01-15
Ubuntu puts out a new release every 6 months, so if the disk is a year old it's probably already 2 releases out of date.  They (usually) fix a lot of stuff with every new release, so you're probably going to be better off with a more recent release.

However, wireless cards Do have a bit of a reputation of being finicky in Ubuntu, just so you know.

---

### Post by Neil Lundy on 2007-01-16
Thanks guys for all your help,

With your help I found out what release it is and it's 5.10 with codename breezy(whatever that meens).

Yes, I have access to another computer an would be able to download another version of Ubuntu, or would I be better installing something like Suse or Redhat because I seem to be having alot of problems with Ubuntu.

---

### Post by Sef on 2007-01-16
> Yes, I have access to another computer an would be able to download another version of Ubuntu, or would I be better installing something like Suse or Redhat because I seem to be having alot of problems with Ubuntu.

Try a more recent version first.  If you still have problems, then try other distros.  What are you system specs? (ram, MHz/GHz, etc.)

---

### Post by Neil Lundy on 2007-01-16
Ok, Since I've been away I've installed the most recent version of Ubuntu. It's still not picking up my wireless card. Do I really have to have an internet connection to update or will it be ok the way it is?

Any idea's on how to install the card would be very greatful!

Thanks again

---

### Post by hal10000 on 2007-01-16
Do you know the model name of your woreless card?

As told in a posting above, open a terminal window (Apps--->Terminal), type: [COLOR="Red"]lspcmcia [/COLOR]and post the output.

---

### Post by Neil Lundy on 2007-01-16
The Ispcmcia command does not work when I type it into the terminal window.

My wireless card is a D-link airplus DWL-650+

Thanks

---

### Post by blore123 on 2007-01-16
If you have the driver disk for Windows, you can use ndiswrapper like I do. There's a lot of information on the web about ndiswrapper, so searching will help.

The website I used (back in breezy days...) was:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu")

Hope this is helpful - if you can correctly configure and install it, running the card should be really easy from that point.

---

### Post by hal10000 on 2007-01-16
the command is lspcmcia (it's a lower L, not I)

---

### Post by stk47rr on 2007-01-16
i'm having the same problem. i typed the command and got
Socket 0 Bridge:      [yenta_cardbus]                     (bus ID:  0000:02:09.0)
please help. i take my laptop to school everyday and sometimes need to get online.  i'm running the latest version of ubuntu. thanks everyone.

---

