---
title: "How to repair an erroneous update?"
date: 2013-03-02
forum: General Help
---

### Post by nickdc on 2013-03-02
I think I may have screwed up in my latest update of 12.04. I missed the request to restart during a two batch update and when I restarted after running both consecutively, my boot process hangs with a purple screen. If I attempt recovery mode, it hangs on a black screen post. I can boot fine into the previous version, which is 3.2.0-38 generic, which I'm using now. I've tried completely removing 3.2.0-39 kernel packages in synaptic, expecting after that I'd then automatically boot into 3.2. 0-38 and be able to run the update again, this time more carefully. But maybe I've not removed all I needed to in synaptic, as rebooting produces exactly the same situation as before. And when I run the update manager I'm told that I'm up to date. I've searched on how to re-run an update, but drawn a blank. I'd be very grateful for some assistance and enlightenment.

---

### Post by sudodus on 2013-03-02
If you have not done it, run
```
sudo update-grub
```
and reboot

---

### Post by nickdc on 2013-03-02
Thanks for that, but I'm afraid it hasn't worked; I have exactly as before. I'm pretty sure my attempt to use synaptic to remove 3.2.0-39 packages can't have worked. Is there a terminal command, or series of commands, that I can use from where I am now (3.2.0-38) that will absolutely clear out everything "above" that so I'm back to where I was when I'd just updated to that (however many updates back that may be)? Presumably then I can go through the update process again until I'm current. (I know I could do a fresh install, but that seems a bit drastic, and anyway I like to learn more through dealing with these glitches as they come up from time to time.)

---

### Post by sudodus on 2013-03-02
Quick fix:

It won't purge the system completely from a kernel version, but I think ***sudo update-grub*** can't find it if you remove all '39' files from /boot

So list the files with
```
ls -l /boot
```
and remove those belonging to '39' with

```
sudo rm -i /boot/*-3.2.0-39-*
```
--
Or better:

It should be possible to remove kernels completely using ***Synaptic***, or by removing all packages with names containing the string '3.2.0-39' with
sudo apt-get purge ..., in your case
```
sudo apt-get purge linux-headers-3.2.0-39*
```
and
```
sudo apt-get purge linux-image-3.2.0-39*
```
--
Finally run
```
sudo update-grub
``` to remove the boot option for the '39' kernel version.

---

### Post by nickdc on 2013-03-02
That's worked. Thank you very much, sudodus. It's removed nearly a gigabyte of stuff and put me back to 0-25, but it's booting cleanly now and I can start to re-apply the updates. Many thanks.

---

### Post by nickdc on 2013-03-02
Woops! perhaps I spoke too soon: the update manager is still telling me there are no updates to install. Yet "uname -a" tells me I'm on kernel version 3.2.0-25-generic, when before I was on 3.2.0-38 (and 3.2.0-39 before the erroneous update). "Sudo apt-get update" doesn't do much either. I don't get it!

---

### Post by matt_symes on 2013-03-02
Hi

As it's only the kernel you have manually removed, try just installing that

```
sudo apt-get install --reinstall linux-image
```

You can also specify the specific kernel version to install if required.

```
sudo apt-get install --reinstall linux-image=3.2.0-39
```

Kind regards

---

### Post by sudodus on 2013-03-02
> **nickdc said:**
> Woops! perhaps I spoke too soon: the update manager is still telling me there are no updates to install. Yet "uname -a" tells me I'm on kernel version 3.2.0-25-generic, when before I was on 3.2.0-38 (and 3.2.0-39 before the erroneous update). "Sudo apt-get update" doesn't do much either. I don't get it!

First try according to matt_symes's post, but reinstall '38' not '39' :-)

Then [COLOR=#ff0000]only if necessary[/COLOR] try all of these commands in sequence
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get dist-upgrade
```
--
and finally ```
sudo update-grub
```

---

### Post by nickdc on 2013-03-02
Thanks for the continued help. I've tried your code, matt-symes, but I get an error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version ‘3.2.0-38’ for ‘linux-image’ was not found

 Same for 3.2.0-39

sudodus, if I run the commands you suggest, won't it upgrade to 12.10? I want to avoid that if I can. I'm happy with 12.04 and so far have declined the option to upgrade.

---

### Post by matt_symes on 2013-03-02
Hi

Just realised my previous command would have never worked :D

Try this. Copy and paste into the terminal.

```
sudo apt-get install --reinstall linux-image-3.2.0-38
```

```
sudo apt-get install --reinstall linux-image-extra-3.2.0-38
```

Kind regards

---

### Post by sudodus on 2013-03-02
> **nickdc said:**
> Thanks for the continued help. I've tried your code, matt-symes, but I get an error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version ‘3.2.0-38’ for ‘linux-image’ was not found

 Same for 3.2.0-39

sudodus, if I run the commands you suggest, won't it upgrade to 12.10? I want to avoid that if I can. I'm happy with 12.04 and so far have declined the option to upgrade.

No I use those commands all the time, and my system stays in the same version, 12.04. dist-upgrade means new kernel etc, not new version. See ```
man apt-get
```
The 'only' problem is, that I suspect it would bring you to '39' again, but then there might be infrastructure to install '38', which is the subversion of the kernel, that you want.

---

### Post by nickdc on 2013-03-02
OK, I went through the first "install --reinstall" sequence and that threw up some errors in the process, telling me I needed to install various linux-headers packages. Fortunately it told me what I needed so I was able to install those too. Then I did the "extras" install and that was fine. I was back with 3.2.0-38, but it's "lowlatency-pae". (lowlatency and lowlatency-pae were two of the sets of headers I was told to install). So I tried the "only if necessary" (update>upgrade>dist-upgrade>update-grub) sequence you suggested sudodus., but that didn't produce any change. "uname -a" now produces: "Linux nick-build-1 3.2.0-38-lowlatency-pae #40-Ubuntu SMP PREEMPT Thu Feb 21 00:03:05 UTC 2013 i686 i686 i386 GNU/Linux". I don't know if this matters at all; the computer now boots ok and I guess it's relatively up to date. Presumably things will sort themselves out with future updates? Or are things likely to start going awry? I've recently installed VirtualBox (before all this happened) and I'd hate to have that start playing up.

Again, thanks for all the help. Much appreciated.

---

### Post by matt_symes on 2013-03-02
Hi

Can we take a look at your sources please.

```
grep -vr "^#" /etc/apt/sources.list{,.d/}
```

Kind regards

---

### Post by nickdc on 2013-03-02
Here goes - (I have quite a few media-related sources activated having followed the comprehensive How to on the multimedia forum)

```
nick@nick-build-1:~$ grep -vr "^#" /etc/apt/sources.list{,.d/}
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise main restricted
/etc/apt/sources.list:deb-src http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:deb-src http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise universe
/etc/apt/sources.list:deb-src http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise universe
/etc/apt/sources.list:deb http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-updates universe
/etc/apt/sources.list:deb-src http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise multiverse
/etc/apt/sources.list:deb-src http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise multiverse
/etc/apt/sources.list:deb http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:deb-src http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-security main restricted
/etc/apt/sources.list:deb-src http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-security main restricted
/etc/apt/sources.list:deb http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-security universe
/etc/apt/sources.list:deb-src http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-security universe
/etc/apt/sources.list:deb http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-security multiverse
/etc/apt/sources.list:deb-src http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-security multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ precise partner
/etc/apt/sources.list:deb http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ precise-proposed restricted main multiverse universe
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu precise main #Third party developers repository
/etc/apt/sources.list.d/medibuntu.list:deb http://packages.medibuntu.org/ precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
/etc/apt/sources.list.d/sunab-kdenlive-release-oneiric.list.distUpgrade:deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu oneiric main
/etc/apt/sources.list.d/sunab-kdenlive-release-oneiric.list.distUpgrade:deb-src http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu oneiric main
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/getdeb.list:deb http://archive.getdeb.net/ubuntu precise-getdeb apps
/etc/apt/sources.list.d/lucid-partner.list.distUpgrade:deb http://archive.canonical.com/ubuntu oneiric partner
/etc/apt/sources.list.d/rednotebook-stable-precise.list.save:deb http://ppa.launchpad.net/rednotebook/stable/ubuntu precise main
/etc/apt/sources.list.d/rednotebook-stable-precise.list.save:deb-src http://ppa.launchpad.net/rednotebook/stable/ubuntu precise main
/etc/apt/sources.list.d/rednotebook-stable-precise.list:deb http://ppa.launchpad.net/rednotebook/stable/ubuntu precise main
/etc/apt/sources.list.d/rednotebook-stable-precise.list:deb-src http://ppa.launchpad.net/rednotebook/stable/ubuntu precise main
/etc/apt/sources.list.d/google-talkplugin.list.save:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/webupd8team-puddletag-precise.list:deb http://ppa.launchpad.net/webupd8team/puddletag/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-puddletag-precise.list:deb-src http://ppa.launchpad.net/webupd8team/puddletag/ubuntu precise main
/etc/apt/sources.list.d/alexeftimie-ppa-precise.list.save:deb http://ppa.launchpad.net/alexeftimie/ppa/ubuntu precise main
/etc/apt/sources.list.d/alexeftimie-ppa-precise.list.save:deb-src http://ppa.launchpad.net/alexeftimie/ppa/ubuntu precise main
/etc/apt/sources.list.d/google-talkplugin.list:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/alexeftimie-ppa-precise.list:deb http://ppa.launchpad.net/alexeftimie/ppa/ubuntu precise main
/etc/apt/sources.list.d/alexeftimie-ppa-precise.list:deb-src http://ppa.launchpad.net/alexeftimie/ppa/ubuntu precise main
/etc/apt/sources.list.d/medibuntu.list.save:deb http://packages.medibuntu.org/ precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
nick@nick-build-1:~$ 


```

---

### Post by matt_symes on 2013-03-02
Hi

> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"

I'm pretty sure it picked up the low latency kernel because of this repository and the other media ones.

There is no harm in keeping it if you want. 

Kind regards

---

### Post by sudodus on 2013-03-02
> **matt_symes said:**
> Hi



I'm pretty sure it picked up the low latency kernel because of this repository and the other media ones.

There is no harm in keeping it if you want. 

Kind regards
+1

I have been using low-latency kernels in Ubuntu Studio, and I have had no problems with them. If you have problems, you can switch to the standard ones, but I'd agree which matt_symes: keep it if you want.

---

### Post by nickdc on 2013-03-03
Thanks for your help, guys. I'm reassured, and everything seems ok now. By the way, when I looked yesterday I couldn't see how to mark the thread as solved. It wasn't in the tools menu where it used to be. Has it been lost in the forums upgrade?

---

### Post by sudodus on 2013-03-03
> **nickdc said:**
> Thanks for your help, guys. I'm reassured, and everything seems ok now. By the way, when I looked yesterday I couldn't see how to mark the thread as solved. It wasn't in the tools menu where it used to be. Has it been lost in the forums upgrade?
Yes, it's a known issue, that we can't mark threads as SOLVED now.

And good luck with your Ubuntu system now :-)

---

