---
title: "Pi 400 Firefox stops responding"
date: 2022-03-07
forum: General Help
---

### Post by WacoJohn on 2022-03-07
Raspberry Pi 400 running their version of Ubuntu -64 and Firefox 97.0.1 Snap for Ubuntu canonical-002 - 1.0

The machine has only 4GB of memory and FF constantly (very frequently) stops responding.  Betting 4Gb is the problem, but not an expert.
Is anyone having or had the same problem and can give advice?  I have to admit, keeping it down to 1 tab prevents the problem.  I really don't like Chromium.  Thank you in advance.

(Didn't know whether to go to Raspberry forum or a FF forum.  Forgive if I am in the wrong place).

---

### Post by him610 on 2022-03-07
> Betting 4Gb is the problem
Probably not. 
IMHO: Most likely, it is **Snap**.

---

### Post by WacoJohn on 2022-03-07
> [COLOR=#000000]IMHO: Most likely, it is [/COLOR]**Snap.**

OF COURSE!!  I SHOULD HAVE KNOWN!  Could you possibly be a bit more precise?  Maybe give some direction on what I can do?  Thanks for your time and attention.

---

### Post by Holger_Gehrke on 2022-03-08
Actually, **both** the major browser are real pigs as far as memory use is concerned, with Chrome/Chromium being (very) slightly worse. I had similar problems on a laptop with 4GB. Those problems went away when I upgraded it to 8GB. Back then Firefox still had an option to limit the number of content processes it would start, which reduced the memory footprint a bit. That option isn't there anymore. The settings in about:config that were changed by that option are still there in my configuration, but it seems like they aren't doing a thing (I had the number of processes set to two instead of the default four, but I regularly see more than two processes for Firefox when using 'ps').

What I would try in this situation: start with the server image and install a lighter desktop environment. Gnome is another ram hungry system, using another desktop might free up enough RAM that Firefox can have enough to work more reliably.

Firefox installed as a snap might not exactly help with the situation. snap is a newer way of installing programs. A snap package is basically a compressed file system image which gets unpacked on the fly as you're running the program. It avoids the necessity to have the right versions of any libraries the program uses installed in the system by bringing all the libraries along inside the package. This means that you're going to have two slightly different versions of some libraries in RAM when running a snap, so it doesn't exactly help. But Firefox brings along its own libraries anyway (look in /usr/lib/firefox and compare the files there to /usr/lib/x86_64-linux-gnu/ on a PC) so that is probably not the main problem. You could try to remove the snap (run 'snap list' to see the exact name of the firefox snap, the run 'sudo snap remove *name_of_firefox_snap*') and install firefox as a conventional .deb package ('sudo apt install firefox').

Holger

---

### Post by ActionParsnip on 2022-03-08
If you use a lighter browser like Midori does the same thing happen?

---

### Post by WacoJohn on 2022-03-08
> [COLOR=#000000]Actually, [/COLOR]**both the major browser are real pigs **

What a gentleman!!  Thank you for such an informative reply .... the kind that teaches AND helps.  A little technical for a 51 Beaner, but gives me a lot to work with.  THANK YOU!!

> [COLOR=#000000]If you use a lighter browser like Midori does the same thing happen?[/COLOR]

I used Midori years ago.  It it is/was(?) so minimal, I dumped it.  For testing, it would have some value.  I will keep that in mind.  Thank you for pointing out the option.

Guess I may have to go to Raspian Bullseye and either Chromium (ugh) or FF 32bit.

I just now went to look for Midori with Ubuntu Software utility, and Ubuntu says there is a FF 97.0 update available.  When I try to update it, I get

> Unable to install updates: snap has no updates available

So I went to terminal and did sudo apt update, and sudo apt upgrade.  Here is the output:

> [FONT=Arial]sudo apt update[/FONT]
[FONT=Arial][sudo] password for owner:[/FONT]
[FONT=Arial]Hit:1 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish InRelease[/FONT]
[FONT=Arial]Get:2 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-updates InRelease [115 kB][/FONT]
[FONT=Arial]Get:3 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-backports InRelease [101 kB][/FONT]
[FONT=Arial]Get:4 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-security InRelease [110 kB][/FONT]
[FONT=Arial]Get:5 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-updates/main arm64 DEP-11 Metadata [25.8 kB][/FONT]
[FONT=Arial]Get:6 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-updates/universe arm64 Packages [106 kB][/FONT]
[FONT=Arial]Get:7 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-updates/universe Translation-en [41.5 kB][/FONT]
[FONT=Arial]Get:8 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-updates/universe arm64 DEP-11 Metadata [35.5 kB][/FONT]
[FONT=Arial]Get:9 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-updates/universe arm64 c-n-f Metadata [3,728 B][/FONT]
[FONT=Arial]Get:10 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-updates/multiverse arm64 Packages [1,076 B][/FONT]
[FONT=Arial]Get:11 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-backports/universe arm64 Packages [4,856 B][/FONT]
[FONT=Arial]Get:12 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-backports/universe arm64 DEP-11 Metadata [16.4 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-security/main arm64 DEP-11 Metadata [11.6 kB][/FONT]
[FONT=Arial]Get:14 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-security/universe arm64 Packages [62.3 kB][/FONT]
[FONT=Arial]Get:15 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-security/universe Translation-en [26.3 kB][/FONT]
[FONT=Arial]Get:16 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-security/universe arm64 DEP-11 Metadata [2,608 B][/FONT]
[FONT=Arial]Get:17 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] impish-security/universe arm64 c-n-f Metadata [3,024 B][/FONT]
[FONT=Arial]Fetched 667 kB in 3s (267 kB/s)    [/FONT]
[FONT=Arial]Reading package lists... Done[/FONT]
[FONT=Arial]Building dependency tree... Done[/FONT]
[FONT=Arial]Reading state information... Done[/FONT]
[FONT=Arial]All packages are up to date.[/FONT]
[FONT=Arial]owner@pi400:~$ sudo apt upgrade[/FONT]
[FONT=Arial]Reading package lists... Done[/FONT]
[FONT=Arial]Building dependency tree... Done[/FONT]
[FONT=Arial]Reading state information... Done[/FONT]
[FONT=Arial]Calculating upgrade... Done[/FONT]
[FONT=Arial]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]
[FONT=Arial]owner@pi400:~$[/FONT]

but I don't see any upgrades ... much less for FF.  Thank you all again.

EDIT:

Here is what I get from Midori:

[https://app.box.com/s/rkmezr587726ciij7s9nz3hf46ao2u75](https://app.box.com/s/rkmezr587726ciij7s9nz3hf46ao2u75)

---

### Post by Holger_Gehrke on 2022-03-08
apt / deb packages and snap are almost completely separate. The GUI Software application makes them seem like they are joined in some way but they aren't. If I run 'snap info firefox' it tells me that the latest firefox on the channel "stable" is 98.0-3 and the newest on the channel "edge" is 99.0a1. The version of Firefox that I got through an "apt upgrade" a few days ago is 97.0.2.

The great advantage of snap for developers is that you only need to build one package for all systems that support snap while you have to make separate packages for each version of each Linux distribution for deb or other traditional packages. That's why there's a snap version that's quite a bit newer than the current version available through apt. The advantages of snap for users are not quite as great. You get the latest and greatest sooner, but snaps are slow to start the first time you run them in a session and thanks to all the duplicate files they take up more space. Also they are sandboxed so they can't access any files unless they are stored in the current users $HOME or on external media mounted in /media/$USER/.

Holger

---

### Post by MAFoElffen on 2022-03-08
I have a Raspberry Pi4B (8GB) with Ubuntu 20.04.4. Fast response. Not the best graphics in the way of Video and streaming, but that is not it's niche. That I installed from Server Edition, then added Desktop.

Mine has twice the memory. I run FireFox installed from Repo, not Snap. I sort of try to avoid Snaps. Every once in a while I'll get a Browser lockup, but that is usually when Firefox updates their browser, and it needs to be restarted. But that happens on my Desktop also... So a FireFox thing.

On my Rasp Pi, I do most of my DEV coding and initial testing on it. I run KVM on it and some VM Guests. Mostly it is inexpensive, small and portable. Mostly it lives in my Living Room. 

I run and test lot of Ubuntu VM's with only 4GB... Even though Ubuntu says 2GB is a minimum for full Ubuntu Desktop, I would say 4GB. I can run Ubuntu VM's in 2GB, but those are not running browsers in them. I can see my resource monitors being pegged sometimes in my tests if I only give them 2GB. Sometimes still with 4GB RAM. I usually give those 6-8GB of Swap, for some buffer space.

Chrome and Chromium use a lot of memory. Then FireFox. Besides FireFox, I usually use Tor and Lynx... 

For the Ama-Gi LiveCD I chose Lynx as the Console based Web Browser and Ice Weasel as the Lightweight Desktop Browser... But it is not meant to be High Rez. The Ama-Gi LiveCd is mean to be  lightweight, and concentrate on diagnostics. So there aren't many frills,. Not meant for on-line gaming, watching videos, or anything close to those... Just to be functional. I will say, that in putting the Ama-GI LiveCD together, even though Ubuntu Cored based, I have gone out of my way to stay away from Snaps on it, to the point of having to compile some of the LiveCD's suite app's myself, instead of using Snaps. But that was my choice.

I have heard a lot of good things about Midori, but I haven't tested it yet...

---

### Post by WacoJohn on 2022-03-08
> **Holger_Gehrke said:**
> apt / deb packages and snap are almost completely separate. The GUI Software application makes them seem like they are joined in some way but they aren't. If I run 'snap info firefox' it tells me that the latest firefox on the channel "stable" is 98.0-3 and the newest on the channel "edge" is 99.0a1. The version of Firefox that I got through an "apt upgrade" a few days ago is 97.0.2.

The great advantage of snap for developers is that you only need to build one package for all systems that support snap while you have to make separate packages for each version of each Linux distribution for deb or other traditional packages. That's why there's a snap version that's quite a bit newer than the current version available through apt. The advantages of snap for users are not quite as great. You get the latest and greatest sooner, but snaps are slow to start the first time you run them in a session and thanks to all the duplicate files they take up more space. Also they are sandboxed so they can't access any files unless they are stored in the current users $HOME or on external media mounted in /media/$USER/.hat lea

Holger

The amount of information is phenomenal.  Thank you.  A bit over my head.  Seems with 4GB, Midori might be the best choice except it did not handle the graphics (as shown in the attachment above).

That leads me to consider Ubuntu and FF NON SNAP(?)  Even if it doesn't help, would be worth trying.  Problem is, have no idea how to get it.  I know just enough to mostly not know how to do such things.  I thought the ONLY FF available for Raspberry UBUNTU was this SNAP version I have.  I assume an apt of some sort.  When I did an apt upgrade, it did not indicate anything for FF of any flavor.

I found this:

[https://vitux.com/4-ways-to-install-mozilla-firefox-in-ubuntu/](https://vitux.com/4-ways-to-install-mozilla-firefox-in-ubuntu/)      but I can't tell which method will install FF NON-SNAP .... being its 'Raspi-ized" Ubuntu on the machine.  Guess I am trying to say being a Pi400, the repository may only offer FF SNAP.  Hope I am making sense.

[COLOR=#000000]MAFoElffen, thank YOU for your great information.  Tucking it in my head for future reference.[/COLOR]

---

### Post by MAFoElffen on 2022-03-09
No. It "IS" in the Apt Repo's for Pi. This is how mine is installed and how it shows on it:
```

mafoelffen@ubuntu:~/git/UbuntuForums/system-info$ apt show -a firefox
Package: firefox
Version: 97.0.2+build1-0ubuntu0.20.04.1
Priority: optional
Section: web
Origin: Ubuntu
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 201 MB
Provides: gnome-www-browser, iceweasel, www-browser
Depends: lsb-release, libasound2 (>= 1.0.16), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.30), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libdbus-1-3 (>= 1.9.14), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.12.6), libfreetype6 (>= 2.10.1), libgcc-s1 (>= 3.3), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.42), libgtk-3-0 (>= 3.14), libharfbuzz0b (>= 0.6.0), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), libstdc++6 (>= 9), libx11-6, libx11-xcb1 (>= 2:1.6.9), libxcb-shm0, libxcb1, libxcomposite1 (>= 1:0.4.5), libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxi6, libxrandr2 (>= 2:1.4.0), libxrender1, libxtst6
Recommends: xul-ext-ubufox, libcanberra0, libdbusmenu-glib4, libdbusmenu-gtk3-4
Suggests: fonts-lyx
Replaces: kubuntu-firefox-installer
Task: ubuntu-desktop-minimal, ubuntu-desktop, kubuntu-desktop, kubuntu-full, xubuntu-desktop, lubuntu-desktop, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-budgie-desktop
Xul-Appid: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
Download-Size: 49.1 MB
APT-Manual-Installed: no
APT-Sources: http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 Packages
Description: Safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.

Package: firefox
Version: 75.0+build3-0ubuntu1
Priority: optional
Section: web
Origin: Ubuntu
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 186 MB
Provides: gnome-www-browser, iceweasel, www-browser
Depends: lsb-release, libatk1.0-0 (>= 1.12.4), libc6 (>= 2.30), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libdbus-1-3 (>= 1.9.14), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.12.6), libfreetype6 (>= 2.10.1), libgcc-s1 (>= 3.3), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.30.0), libgtk-3-0 (>= 3.4), libharfbuzz0b (>= 0.6.0), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), libpangoft2-1.0-0 (>= 1.14.0), libstdc++6 (>= 9), libx11-6, libx11-xcb1 (>= 2:1.6.9), libxcb-shm0, libxcb1, libxcomposite1 (>= 1:0.3-1), libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxi6, libxrender1, libxt6
Recommends: xul-ext-ubufox, libcanberra0, libdbusmenu-glib4, libdbusmenu-gtk3-4
Suggests: fonts-lyx
Replaces: kubuntu-firefox-installer
Task: ubuntu-desktop-minimal, ubuntu-desktop, kubuntu-desktop, kubuntu-full, xubuntu-desktop, lubuntu-desktop, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-budgie-desktop
Xul-Appid: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
Download-Size: 46.1 MB
APT-Sources: http://ports.ubuntu.com/ubuntu-ports focal/main arm64 Packages
Description: Safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.

```
So once you remove the Snap App, then install from the repo:
```

snap disable firefox
snap remove --purge firefox
sudo apt install firefox

```

Look at the attached screenshot... That is with running Xorg-XServer, LightDM, Gnome Sessions, LibVirtD, FireFox with 12 tabs open... and altogether only taking about 1.5 GB memory...

What does it hurt to try it? You are already thinking about trying other browsers, right? Besides the Snap version of FireFox will not allow users to use Gnome Extensions, Like the standard FireFox browser will.

---

### Post by WacoJohn on 2022-03-09
It gets better by the minute.  What I would like to do is run Ubuntu on my Pi400 and I am.  I would like to run the best browser I can find which performs acceptably.  Certainly FF SNAP doesn't.  Willing to try FF nonSNAP and see how it goes.  If no grace, then Midori (except apparently Midori as some kind of graphics problem).  So, I need the idiot's way of getting rid of FF SNAP and trying FF nonSnap.

I asked for comprehensive help ..... and WOW, ... I'm gettin it.  THANK YOU ALL immensely.  Problem is ME.  Most of this is academic and somewhat over my head.  NOT THAT I AM NOT GRATEFUL!

So ... if I can get what it takes to get FF Snap off here and FF nonSNAP on here, that is two giant steps.  A third would be solving the Midori graphics problem.  I'll take what I can get and thank you again.

---

### Post by MAFoElffen on 2022-03-09
I posted that in my last post... I'll go into more detail and explain it...

At the desktop, press the the keys <Cntrl><Alt><T>... A Graphical Terminal Session should pop up...

This command will list all your installed Snap app's
```

snap list

```
Look for 'FireFox', just to ensure that is how it is installed.

This command will stop the Firefox Snap app:
```

snap disable firefox

```
This command will remove the Firfox Snap App 
```

snap remove --purge firefox 

```
This command will install FireFox from the Ubuntu Apt Repositories
```

sudo apt install -y firefox

```
Make sure it finishes the installation without errors, then close the Graphical Terminal Session Window.

Go to Activities > start Typing "FireFox" > Right-Click on the Icon and select "Add To Favaorites" to add it back to the Left Dock... Select Icon to start...

Test and Enjoy...

---

### Post by WacoJohn on 2022-03-09
> **MAFoElffen said:**
> I posted that in my last post... I'll go into more detail and explain it...

YEAH!!! Sorry to trouble you.  I just didn't/couldn't spot it in your previous post.  Undertaking it immediately and will update with what results.  THANK YOU SIR.

EDIT:

Completed your recommendations.  Had to do a restart or FF would not install.   After that, FF has been running GREAT (though it's only been a few minutes).

> This command will remove the Firfox Snap App 
          ```
snap remove --purge firefox 
```

**had to do a restart here.**

> This command will install FireFox from the Ubuntu Apt Repositories
     
     ```
sudo apt install -y firefox 
```
Make sure it finishes the installation without errors, then close the Graphical Terminal Session Window.

Sooo, this problem is SOLVED thanks to all the help.  Ironically, the first reply was right.  It's just at the time I had no idea what he was talking about (snap??)

In any case, thanks to all who have lent their valuable time to me.  I learned more than I can express.

---

### Post by DuckHook on 2022-03-09
I hope I'm not confusing you further, but another option for browser is Epiphany. I've run Midori before and find it a great browser but, like you, I found that it sometimes chokes on certain graphics from certain sites. Epiphany tended to work better for me on those sites. Epiphany might be considered a middleweight. It's more resource heavy than Midori, but definitely less than the bloated, heavyweight, mainline browsers like FF, Chromium or Brave. You may want to give it a try to see if it suits your needs.

FWIW, the days of being able to install the non-SNAP version of FF appear to be numbered. I believe that my development version of Jammy no longer has it in the repos (and Jammy is just a few weeks away). I could be wrong, but I seem to recall that what looks like an apt version of FF is actually a stub that redirects apt to installing the SNAP version of FF. It's a sleight of hand that may confuse new users and really should be come with better warnings.

If you want to avoid SNAPs, the following workarounds exist:

[LIST=1]
[*]Install the ESR version of FF from the Mozilla Team PPA. I don't normally recommend PPAs, but the Mozilla Team is reliable, so security is less of a concern. And Canonical's decision to push SNAPs so hard is also pushing me back to using this riskier alternative. Note though that the ESR version is not the latest and greatest, though it is certaily current enough and, for most people, more than sufficient. It also has the benefit of longer support cycles. To install:```
sudo add-apt-repository ppa:mozillateam/ppa
sudo apt update
sudo apt install firefox-esr
```
[*]The second option is to install the standalone version of FF. This is a self-updating version that, once installed, will check for updates every time you open it and thereafter auto-update on its own. Instructions for installing the standalone version are here: [https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users](https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users)   The initial setup is a bit more involved, but you only have to go through it once and then it's pretty much maintenance free after that.
[/LIST]
Good Luck!

---

### Post by WacoJohn on 2022-03-09
> I hope I'm not confusing you further

Sir, I was born confused.  Your comments/advice are immensely appreciated.  FF ESR I believe is advised in Raspberry Bullseye ... a 32-bit I do believe.  I had no problem with Bullseye and whatever FF it was that was recommended but I prefer a 64-bit environment since, my Pi is 64-bit..  Between all the offers for Pi 400 (I have tried most of them) it's confusing exactly which is which ... 32-bit/64-bit OS, Chromium, FF, FF snap, FF nonsnap, FF ESR, Midori, Epiphany .. etc.  In any case, have plenty to be confused with and I can learn from right here in this thread, thanks to people like you.

So far, can't ask for anything better than this Ubuntu and this FF (nonsnap).  Smooth as an ice cold beer on a TX summer day.

---

### Post by DuckHook on 2022-03-09
> **WacoJohn said:**
> …FF ESR I believe is advised in Raspberry Bullseye ... a 32-bit I do believe.
mmm… no… I don't believe so. I have nuked 32-bit architecture from my system entirely and I have this ESR version installed. While FF may offer both 32-bit and 64-bit in theory, if you use the aforementioned PPA, it will install the 64-bit.
> Between all the offers for Pi 400 (I have tried most of them) it's confusing exactly which is which ... 32-bit/64-bit OS, Chromium, FF, FF snap, FF nonsnap, FF ESR, Midori, Epiphany .. etc.
Perhaps a soothing word of advice then: it's not actually as confusing as you may be anticipating/dreading. Every one of these alternatives, whether SNAPs, from the repos, or from PPAs are 64-bit. The days of Ubuntu mixing 32-bit apps among their 64-bit offerings are almost over. The only 32-bit platforms that come to mind are Steam, WINE and maybe a couple of VMs—and that, only if you specifically so instruct when installing. In fact, the complaint these days is Canonical doing away with 32-bit support altogether. You may be conflating Canonical's philosophy with Raspbian's, but they are opposites. They approach the matter of OSes quite differently. Canonical wants to do away with 32-bit and have stopped supporting it going forward. The RPi guys are still very keen on 32-bit because it isn't as much of a resource hog and this better suits their lean and limited HW. So, if dealing with Ubuntu, you will almost certainly be 64-bit. If installing Raspbian, it's a hodge-podge of 32 & 64 which can admittedly be confusing.
> So far, can't ask for anything better than this Ubuntu and this FF (nonsnap).  Smooth as an ice cold beer on a TX summer day.
Glad you found a combo that works. Keep in mind the possible fly in the ointment that may come with the upgrade to Jammy (which may force you to resort to the aforementioned options), but otherwise, best not to fix what ain't broken.

Continued best of luck and Happy Ubuntu-ing.

---

### Post by WacoJohn on 2022-03-09
> Continued best of luck and Happy Ubuntu-ing.

FWIW .... same problem with Epiphany (now called Web apparently) as with Midori.  Here is the screenshot.

---

