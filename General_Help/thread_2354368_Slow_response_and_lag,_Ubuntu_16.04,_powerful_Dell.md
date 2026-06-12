---
title: "Slow response and lag, Ubuntu 16.04, powerful Dell laptop 16GB RAM"
date: 2017-03-02
forum: General Help
---

### Post by stephen-direct on 2017-03-02
Hi all,

I've bought a new laptop 6 months ago because I wanted a fast an efficient Ubuntu fresh operating system. I've choosen Dell because they claim to be compatible with Linux, and I've read some good opinions about the brand in the community.

I've choosen a powerful configuration so that Ubuntu can have plenty of resources: Intel i7, 16GB RAM, 17'' screen (it is a touch screen and I've choosen Ubuntu because it is the only Linux distribution with touch support).

The first installation went fine, but after a few months, it started to get very slow, almost unusable. Not only browsers (Firefox and Chromium), but ALL applications.

So I had to do a clean install again. Then everything was fine and fast. But now, after a few months, AGAIN, everything gets slow and very irritating.

Not only browsers but also for instance gThumb: I use it a lot to browser through photos (on my harddrive) and it is slow to display each pic.

There is also a _LAG_ while switching through applications.

Usually I only install programs from the Software Center and I try to keep everything as standard as possible. Recently I've installed Google Earth Pro from a deb file downloaded from the official website (deb for Ubuntu 64 bits).

It seems that my system started to get slower after that install. But I'm not sure. I rarely use GE and the system is slow even though GE is not launched. I tried to uninstall, but uninstall button through Software Center does not work, and I cannot find any "uninstall" file.

How can I identify the cause please? It seems there are blocking processes running in the background.

Yet when I check processes and memory usage % there is plenty of power available...

Thanks.

---

### Post by howefield on 2017-03-02
Google Earth Pro appears to be unsupported on the Linux platform these days so probably not a surprise that it may be giving problems.
> 
Google Earth Pro 6.0 was the last version of Pro created for Linux. Versions of Google Earth Pro 6.0 and earlier are no longer supported on any platform.
If you are a Linux user, you can use the standard version of Google Earth available here, or you can download the latest version of Google Earth Pro for Windows or Mac.

Shrug, having said that the version I've just installed seems to be 7.1

```
apt-cache policy google-earth-pro-stable 
google-earth-pro-stable:
  Installed: 7.1.8.3036-r0
  Candidate: 7.1.8.3036-r0
  Version table:
 *** 7.1.8.3036-r0 100
        100 /var/lib/dpkg/status
```

To uninstall the application try opening a terminal and using..

```
sudo apt purge google-earth-pro-stable
```

---

### Post by stephen-direct on 2017-03-03
Thanks for you suggestion.

I had the same GE version as you and I used your command line to remove it. But after removal, there is still the infamous lag on all applications.

I've noticed there are 2 error messages on startup:

* black screen before Ubuntu login screen, it says "Radeon VCE init Error". I did a bried research on that but could not find something relevant. Usually people have problems with old components not being supported any more, but here it is a standard modern laptop.

* when desktop appears, error message  says "/usr/bin/kded5". Could it be related to KDE desktop environment? Wich could explain why everything graphic is slow (terminal command lines seems to work ok). I'm using Unity and I did not change anything to Ubuntu basic configuration. I haven't even changed the background wallpaper nor the colors.

---

### Post by howefield on 2017-03-03
> **stephen-direct said:**
> * black screen before Ubuntu login screen, it says "Radeon VCE init Error". I did a bried research on that but could not find something relevant. Usually people have problems with old components not being supported any more, but here it is a standard modern laptop.

* when desktop appears, error message  says "/usr/bin/kded5". Could it be related to KDE desktop environment? Wich could explain why everything graphic is slow (terminal command lines seems to work ok). I'm using Unity and I did not change anything to Ubuntu basic configuration. I haven't even changed the background wallpaper nor the colors.

Both of those messages warrant investigation and could be the culprit.

What graphics card are you using in the machine ?

```
lspci | grep VGA
```

and how did the kded5 package get installed, I don't believe it is standard on a default Ubuntu installation ?

---

### Post by stephen-direct on 2017-03-05
Hi,

I've just noticed Ubuntu on my laptop is back to its original speed, no more lag!

So it seems _Google Earth Pro 64bit for Linux_ presence was the problem, even when the app wasn't running. After uninstalling it I rebooted the laptop and it didn't change anything. That's why I posted my former message. But the next day it was OK.

Anyway here is the output of the command line you suggested for the graphic card error message:

00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07)

I'll investigate the error messages even if it's working now. If you think about something with that card please let me know.

About kded5, I think my installation is standard... What kind of installation is kded5 linked to?

Thanks for your help.

---

### Post by howefield on 2017-03-05
> **stephen-direct said:**
> So it seems _Google Earth Pro 64bit for Linux_ presence was the problem, even when the app wasn't running. After uninstalling it I rebooted the laptop and it didn't change anything. That's why I posted my former message. But the next day it was OK.

Hmm.. glad it is working now as expected but odd that a reboot after uninstalling Google Earth didn't resolve, perhaps it needed a "cold" reboot. Time will tell :) 

> About kded5, I think my installation is standard... What kind of installation is kded5 linked to?

It is probably a dependency of a KDE application that you have installed ?

You could try..

```
apt rdepends kded5
```

and have a look through the output of software for applications that you have installed.

---

### Post by HermanAB on 2017-03-05
Google Earth is like EMACS.  It can make any computer slow.  It caused my wife's Macbook Pro to overheat and freeze.

Even when it is not visibly running, there may still be parts running in the background.

Anyhoo, the way to investigate these kind of performance issues, is with a simple little program called 'top'.

---

### Post by stephen-direct on 2017-03-07
I have replied too fast... the lag is back.

The system is yet faster than before (with Google Earth installed), but Firefox and Chromium are stuck all the time. It's impossible to watch a video without interruptions and it's slow. Switching through simple pages takes more seconds.

My internet connexion is fast and I use my latop in different offices with different connexions, always the same.

I've checked the command line "top", but %CPU and RAM aren't no more than 3% .... 

My Linux system looks like now a Windows OS. Full of bugs and lags.

I think I'll have to reinstall AGAIN. 

The output about kded5 is:

apt rdepends kded5
kded5
Reverse Depends:
  Dépend: kded5-dbg (= 5.18.0-0ubuntu1)
  Dépend: plasma-workspace
  Dépend: plasma-desktop
  Dépend: kdenlive
  Dépend: kded5-dev (= 5.18.0-0ubuntu1)



Anyway, thanks for the suggestions.

---

### Post by stephen-direct on 2017-03-24
Update:

My Ubuntu installation is finally running at normal speed, no more lag.

I did not reinstall it, just did daily updates through the update tool. Some core Ubuntu components are listed as being updated and maybe it is tne reason why it helped.

Google Earth Pro uninstallation probably messed with some components, and the general update fixed them OVER  A FEW DAYS and _a few update cycles_. That's why it didn't work immediately.

As of now I've decided to never install again on Ubuntu any software outside the Software Center. In fact I already do it, I only install through it.

But I thought Google Earth would be OK (because it is supposed to be made by qualified people, you know, the geniuses hired in Silicon Valley)... 

So, solved.

---

