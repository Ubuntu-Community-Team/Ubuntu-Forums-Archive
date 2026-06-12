---
title: "Software installation issue"
date: 2017-03-08
forum: General Help
---

### Post by mobileberna on 2017-03-08
Not sure why, but I can't install any of the software. I'm still new to the Ubuntu family and am kind of lost at how this all works. There's two main things I need on my computer: Kodi and Trelby. I'm having issues getting both of these! (though i did manage to get Kodi!!!)

---

### Post by Topsiho on 2017-03-08
According to Wikipedia Trelby is no longer actively developed anymore, and it now is not in the Ubuntu depositories any more. So probably you'll have to look around and find something else. Maybe someone here can tell you more.

Topsiho

---

### Post by Bucky Ball on 2017-03-08
> **Topsiho said:**
> ... the Ubuntu depositories ...

Repositories. :)

Know nothing of Trelby, but Kodi is, of course, alive and kicking.

There are ongoing issues with the package manager that comes default with Ubuntu. Suggest you install Synaptic Package Manager and use that (which many prefer) as that is working fine. To install, open a terminal and:

```
sudo apt update
sudo apt install synaptic
```

You will be asked for your password with the 'sudo' commands. It will be invisible when you type it and that is normal. You can also install kodi via the terminal with:

```
sudo apt install kodi
```

If you have gotten Ubuntu installed and this far with everything working fine apart from this, well done! Nothing's amiss, you look like you have a stable install as the package manager problem is a known issue that has been hanging about for awhile now. 

So nothing to panic about ... yet! :) Install Synaptics and see how that goes. You don't say which release you've installed but 16.04 LTS very stable.

PS: If you have not yet updated your system, you should do so now. You can do that with the 'Software Updater' or via a terminal with:

```
sudo apt update
sudo apt full-upgrade
```

This will NOT upgrade your release to a newer one, just the software you currently have installed in the release you currently have installed.

---

### Post by Topsiho on 2017-03-08
Thanks to Bucky Ball for correcting me :)

It seems that there exist some other "screen writing" programs (whatever they are), and that the one I found which is in the present repositories for Ubuntu is Lyx, while other, mentioned as "the best", unfortunately aren't.
So the OP might try Lyx and see whether that fills his needs. Googling (Duckduckgoing) a bit might help!

I fully support Bucky Balls suggestion to install Synaptic. When you have used it a few times, you'll probably don't want to use anything else!

Topsiho

---

### Post by Bucky Ball on 2017-03-08
> **Topsiho said:**
> I fully support Bucky Balls suggestion to install Synaptic. When you have used it a few times, you'll probably don't want to use anything else!

I haven't used anything else in years. :)

---

### Post by mobileberna on 2017-03-08
Thank you all for the comments! I discovered that Trelby is no longer developed as well...tough pill to swallow! I have Trelby on another device and now i'm going to have to figure out how to convert the formatting or something...idk. Kodi installed wonderfully! However, Kodi runs SLOW when launched...? My system simply sucks and i can accept that; I just need some help in making it suck less. I have the Synaptic and used it...apparently I had a "broken package"...? I'm getting the hang of Lubuntu; it's like Windows meets Apple! I just need to figure out how to navigate that "Terminal" and how to install programs and all that good basic shinnanigans.

I tried installing Lyx, but I'm still having issues installing software :icon_frown:

---

### Post by Bashing-om on 2017-03-08
mobileberna; Hello;

As I pass by;
> 
but I'm still having issues installing software

Let us make sure that the package manager is in a consistent state .
Post back - Between code tags - the outputs of terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

``` 
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
where the data base is sync'd up with mother, check for any packages that can be updated, and check for any packages that need (F)ixing.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by mobileberna on 2017-03-08
I will try that if the problem persists...I may or may not have installed Xubuntu to see if I like it better (I may!).

---

### Post by mobileberna on 2017-03-08
I moved on from Lubuntu to Xubuntu and I think I found my "flavor"! No flickering screen and I was able to install "LyX" from the software. Just when we think my troubles are over, I have one last issue:
"Software" runs EXTREMELY slow! When I installed LyX, I didn't even know it installed! There are 9 updates in "software"  yet I can't install them; "software" just lags and shuts itself off. I ran the terminal and got
```
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [479 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 DEP-11 Metadata [289 kB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main i386 DEP-11 Metadata [54.7 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [184 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [40.7 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/universe i386 DEP-11 Metadata [32.1 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [423 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 DEP-11 Metadata [139 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [169 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 DEP-11 Metadata [2,520 B]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-backports/main i386 DEP-11 Metadata [3,328 B]
Fetched 2,160 kB in 7s (290 kB/s)                                              
Reading package lists... 1%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
mobileberna@DaBer-PC:~$ 
mobileberna@DaBer-PC:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mobileberna@DaBer-PC:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Any suggestions on how to fix the lag in "software"? Maybe a way to speed Xubuntu up all together?

---

### Post by Bucky Ball on 2017-03-08
There is absolutely nothing wrong with your terminal update/upgrade. There are no errors at all so no issue there.

You give no details about the machine you're running, specs etc., so hard to know for sure, but maybe your machine is just 'slow'. 

I haven't used anything but Xubuntu for years, with a caveat. I used to install the minimal install then just add what I needed. This included the xfce4 desktop used by Xubuntu. Nowadays, I install Xubuntu-core which gets me to a place it took awhile to get to when I was installing from scratch with the mini.iso. So, I run a 'stripped down' Xubuntu (on all my machines, not just low spec ones). :)

PS: I also never update through 'Software', don't know what it is, don't have it installed. What is 'Software'?

---

### Post by vasa1 on 2017-03-08
> **Bucky Ball said:**
> ... What is 'Software'?
That seems to be part of a trend.

Nautilus alias Files
Web alias Epiphany
Software alias whatever seems to have replaced Ubuntu Software Center.

---

### Post by mobileberna on 2017-03-08
"Software" is where some apps and, well, software is...software installer i think is the technical name of it? Yes my machine is very likely to be "just slow"! lol

---

### Post by Bucky Ball on 2017-03-09
Ok. Don't use 'Software'. Install and use Synaptic Package Manager (lots of us prefer it anyhow and it used to be the default package manager many moons ago). There are known issues with the default package manager ('Software' apparently) and you may be experiencing a consequence of that.

See if Synaptics is any faster/better. You can install from 'Software' (maybe!) or use the terminal:

```
sudo apt install synaptic
```

---

### Post by mobileberna on 2017-03-10
Hey thanks! I appreciate that. I'm slowly learning the system!

---

### Post by Bucky Ball on 2017-03-10
> **mobileberna said:**
> Hey thanks! I appreciate that. I'm slowly learning the system!

Enjoy that learning curve. :)

Is Synaptics working for you? Please confirm.

---

### Post by mobileberna on 2017-03-12
I don't really understand it completely. I'm not sure what packages I need for what...I got some packages and I'm assuming they did something...lol! After downloading the packages the software program has been working just fine though! I'm figuring out Xubuntu! I've found a few programs that will be able to learn and utilize.

---

