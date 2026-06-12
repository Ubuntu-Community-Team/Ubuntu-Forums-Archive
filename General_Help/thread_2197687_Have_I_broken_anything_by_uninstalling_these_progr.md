---
title: "Have I broken anything by uninstalling these programs?"
date: 2014-01-05
forum: General Help
---

### Post by West Swan on 2014-01-05
Hello,

I am not a total beginner to Linux and for the most part I know what programs I want and which ones I don't.

I've just done a clean install of Lubuntu 14.04 daily build.  As an aside, with all the updates, this will eventually become exactly the same as what is released in April right?  So I won't have to reinstall at that time.

Ok, what I did once installed is:

[FONT=&quot]    sudo apt-get purge gucharmap libgucharmap-2-90-7 xpad sylpheed sylpheed-doc transmission transmission-common transmission-gtk pidgin pidgin-data abiword abiword-common  libabiword-3.0 gnumeric gnumeric-common audacious audacious-plugins audacious-plugins-data libaudcore1 libaudclient2 Xterm im-config mtpaint lxsession-default-apps usb-creator-common usb-creator-gtk gnome-mplayer libgmlib1 libgmtk1 libgmtk1-data ibus gir1.2-ibus-1.0 libibus-1.0-5    


Everything seems to be working just fine.  I have a US Keyboard and type in English.  Is there anything I have uninstalled that would 'break' my computer that I'm not aware of?


Once I have done this and restarted, I do the following:

[/FONT][FONT=&quot][FONT=&quot]sudo apt-get install libreoffice rgbpaint thunderbird gufw vlc aisleriot


I am doing this for a friend who just uses the computer to browse the web, type a letter and play soliaire pretty much.


Will doing all this uninstalling and installing result in any 'junk' files remaining on the computer which should be removed e.g. with bleachbit for linux?

I know that Linux is a lot better than Windows in this regard and doesn't have a registry but would it help any in terms of performance?

Hope this makes sense,

Cheers,

Paul
[/FONT]

[/FONT]

---

### Post by monkeybrain20122 on 2014-01-05
If you are a 'total beginner" why are you running an alpha version meant only for testers? The latest stable Ubuntu release is 13.10, 12.04 is the LTS.

---

### Post by West Swan on 2014-01-05
I mentioned in the first post that I'm not a total beginner :-)

I have been using Ubuntu and Mint for some time now.

The reason why I am considering putting  14.04 on my friends computer is because I am only visiting them for a couple of weeks and, if I put 13.10 on it, when support for that ends there is no way he could upgrade by himself to 14.04

So yeah, not sure whether to put 13.10 and have him have a period of no security updates or 14.04 and hope nothing goes wrong until April

---

### Post by Bucky Ball on 2014-01-05
*Thread moved to **Ubuntu +1**.*

Welcome. 14.04 LTS is testing, not released until April, only supported on this sub-forum until release, and definitely not the right place to start. 12.04 LTS is the most stable and long-term support. Good place to begin and get to know the OS. 13.10 if you have very new hardware that won't work with 12.04 LTS. 

Both releases are a direct upgrade to 14.04 LTS when it is released next April. That has five years support. 

The interim releases (non-LTS) are supported for nine months and are upgradeable only to the next release, e.g. 12.10>13.04>13.10>14.04 LTS. LTS releases leapfrog this and are upgradeable from one LTS to the next: 12.04 LTS>14.04 LTS>16.04 LTS, etc.

Use 12.04 LTS or 13.10 unless you want a very steep learning curve. Even if you get 14.04 right, there is no guarantee an update is not going to break that. Daily builds are pretty much 'bleeding edge' and unless you know what you're doing (or want that learning curve) you probably don't want to be there. 

Having said this, it might run fine, but be prepared for any eventuality until (and possibly after) release. 

Good luck. ;)

PS: Just realised you are doing this for a friend. Wouldn't go there unless you are going to be readily on hand to fix things. All up to you in the end, of course. This situation more like a production machine that just needs to work and be stable as you are not going to be there 24/7. LTS is designed for this. ;)

PPS: The answer to your original question is no. There should be no junk. after installing, in a terminal, run:

```
sudo apt-get autoremove
```

That will get rid of anything not required or orphaned. It doesn't work like Windows. You do not have to be cleaning things and Bleachbit is not required. Killing a mosquito with an elephant gun. Bleachbit is rarely required and there are other tools besides.

---

### Post by West Swan on 2014-01-05
Wow that is awesome thank you :-)

Yes my friend is not very computer literate so LTS is a better option.

The only thing is that Lubuntu doesn't have an LTS version until April right?

---

### Post by mörgæs on 2014-01-05
Correct, but Xubuntu 12.04 has three years of support.

Moving the thread back.

---

### Post by monkeybrain20122 on 2014-01-05
> **Bucky Ball said:**
> 
PPS: The answer to your original question is no. There should be no junk. after installing, in a terminal, run:

```
sudo apt-get autoremove
```

That will get rid of anything not required or orphaned.


I would also get rid of all the localizations that are not needed.

---

### Post by Bucky Ball on 2014-01-05
This might be a step beyond for the moment, but if you are up for a learning curve, the minimal install can be the slimmest of all the *buntus:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

You add the lightweight desktop environment of your choice (xfce4 or lxde for instance) and only the apps you want/need (sudo apt-get install firefox thunderbird). 

Enjoy.

PS:  
[QUOTE= mörgæs
]Moving the thread back.[/QUOTE]

Good idea and saves me doing it. Thanks. ;)

---

### Post by kansasnoob on 2014-01-05
I happened to notice this while it was in Ubuntu +1 and I noticed a few things worth mentioning:

#1: Since you're talking Lubuntu you are apparently looking for something lightweight.

#2: You're not happy with some of Lubuntu's default apps such as Abiword.

#3: Since the puter is not going to be easily accessible to you for sometime you want an LTS.

This all makes a lot of sense to me because I maintain nearly 50 individual PC's within a 50 mile radius (and I can no longer drive).

So let's consider a few things:

#1: Ubuntu 12.04 (Precise) is [supported for 5 years]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop/UbuntuDesktop-12.04#Support") - until April 2017 - whereas [Lubuntu 12.04 support has already ended]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Lubuntu/Lubuntu-12.04#Support").

#2: Trusty (14.04) is still under construction and there are some changes still coming in regards to GTK and some underlying GNOME infrastructure (versions 3.8 -> 3.10) so breakage is almost inevitable :(

#3: I've found [this Ubuntu 12.04 setup]("http://ubuntuforums.org/showthread.php?t=1966370") to run almost as lightly as either Xubuntu or Lubuntu. And it's [supported by Ebubuntu]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Edubuntu/Edubuntu-12.04#Support").

**[COLOR="#FF0000"]Now stop[/COLOR]** ........ there is more to consider :)

Shortly before Ubuntu dropped interim release support to 9 months they increased LTS support to 5 years but they also introduced the [Hardware Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#LTS_Enablement_Stacks") into the LTS cycles!

So, unless you're working with new hardware that requires the new HES, I highly recommend using the archived 12.04.1 images from here:

[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

I know the web-page is labeled 12.04.2 but please take time to look! You'll find the 12.04.1 images there!

Most likely this image:

[http://old-releases.ubuntu.com/releases/precise/ubuntu-12.04.1-desktop-i386.iso](http://old-releases.ubuntu.com/releases/precise/ubuntu-12.04.1-desktop-i386.iso)

Unless you want amd64????

If any of this is confusing please feel free to send me a PM :D

---

### Post by Elfy on 2014-01-05
>  If any of this is confusing please feel free to send me a PM Confuses me - the thread's about lubuntu :p

---

### Post by vasa1 on 2014-01-05
> **Elfy said:**
> Confuses me - the thread's about lubuntu :p
I think it segued into other flavors/Ubuntu because of OP wanting something like LTS which Lubuntu currently doesn't offer.

---

### Post by kansasnoob on 2014-01-05
> **Elfy said:**
> Confuses me - the thread's about lubuntu :p

And I started off with:

> I happened to notice this while it was in Ubuntu +1 and I noticed a few things worth mentioning:

#1: Since you're talking Lubuntu you are apparently looking for something lightweight.


what's wrong with that?

---

### Post by kansasnoob on 2014-01-05
> **vasa1 said:**
> I think it segued into other flavors/Ubuntu because of OP wanting something like LTS which Lubuntu currently doesn't offer.

Exactly, I was just offering another option :)

And a detailed option to boot.

---

### Post by West Swan on 2014-01-05
Hello,

Nearly bedtime here.  That's right the reason I was looking at Lubuntu for my friend is because he has one of the first generation of Pentium 4 computers 1.3Ghz with 384Mb of RAM.

I tried Xubuntu yesterday but it ran awfully slow.  Today I tried Lubuntu and it runs great.  Even LibreOffice opens reasonably quickly.  He needs that as he has a lot of Powerpoint presentations and even some Publisher stuff.  

I couldn't find a light weight Powerpoint viewer - yeah I know about Wine but I'm trying to wean him off Windows programs and help him to enjoy Linux alternatives  e.g. Aisleriot which is a lot better than the default XP Patience game  :-)

I just tried the minimal install using Virtualbox and it went through quite a ways before an error message "warning couldn't download package dash"  

Tried again with a similar error message.  Then tried using VmWare but that also failed at around the same point.  Will try again tomorrow.

I don't think it would run the 12.04.1 version but I guess it can't hurt to try.  

Thanks very much for everyones good advice.

Regards,

Paul

---

### Post by Bucky Ball on 2014-01-05
Well, sounds like you were installing ubuntu-desktop in the minimal install. That is not the idea. You want just the desktop environment, for you lxde is all you need, and only the packages required. *buntu-desktop anything drags in a HEAP of stuff. 

sudo apt-get install lxde

... is all you need.

If you are trying to run virtual machines on the P4 you are going to run in to a LOT of trouble. There is simply not enough RAM.

---

