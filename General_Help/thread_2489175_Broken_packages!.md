---
title: "Broken packages!"
date: 2023-07-20
forum: General Help
---

### Post by John Jason Jordan on 2023-07-20
Broken packages!

I have tried every repair that I have read about, and nothing has worked. I started with Synaptic package manager, which offers to fix broken packages, and then it says it has successfully repaired them, but it lies. You then try to install something and it says 'you have held broken packages.'

sudo apt --fix-broken install  <executes without error and with no output, but does nothing
sudo dpkg --configure -a <ditto the above>
sudo apt install -f <ditto the above>
sudo apt update <does its thing, but accomplishes nothing>

I am trying to install nemo, the file manager for Cinnamon. I have it installed on the computer I am writing this on, and it installed without problems, although it did install a ton of Cinnamon stuff. Now I'm trying to install it on my desktop, but I can't because of the broken packages. I've spent two hours trying to fix the problem, and I need help. Here's my latest effort:

sudo apt install nemo
    The following packages have unmet dependencies: nemo: Depends libgail-3-0 but it is not going to be installed. Unable to correct problems; you have held broken packages.

I've run into broken packages before, but they were always easy to fix. I need help with this one.

---

### Post by MAFoElffen on 2023-07-20
There are two more choices...
```

sudo apt full-upgrade 

```
will install new packages to try to satisfy dependency problems
```

sudo apt dist-upgrade

```
Is a more agressive approach and will both remove packages and install new packages to satisfy a dependency problem.

How did you try to install nemo? What command did you use? This was a dry-run on mine:
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo apt install -s nemo
[sudo] password for mafoelffen: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libann0 libcdt5 libcgraph6 libgts-0.7-5 libgts-bin libgvc6 libgvpr2 liblab-gamut1 libpathplan4
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  catdoc cinnamon-desktop-data cinnamon-l10n dvisvgm exif fonts-lato fonts-lmodern gist hwdata id3 libcinnamon-desktop4 libgail-3-0 libnemo-extension1 libptexenc1 libruby3.0 libteckit0 libtexlua53
  libtexluajit2 libxapp1 libzzip-0-13 lmodern nemo-data nemo-fileroller odt2txt python3-xlrd rake ruby ruby-json ruby-net-telnet ruby-rubygems ruby-webrick ruby-xmlrpc ruby3.0 rubygems-integration t1utils
  tex-common texlive-base texlive-binaries xapp xapps-common
Suggested packages:
  tk | wish ri ruby-dev bundler perl-tk xzdec
The following NEW packages will be installed:
  catdoc cinnamon-desktop-data cinnamon-l10n dvisvgm exif fonts-lato fonts-lmodern gist hwdata id3 libcinnamon-desktop4 libgail-3-0 libnemo-extension1 libptexenc1 libruby3.0 libteckit0 libtexlua53
  libtexluajit2 libxapp1 libzzip-0-13 lmodern nemo nemo-data nemo-fileroller odt2txt python3-xlrd rake ruby ruby-json ruby-net-telnet ruby-rubygems ruby-webrick ruby-xmlrpc ruby3.0 rubygems-integration t1utils
  tex-common texlive-base texlive-binaries xapp xapps-common
0 upgraded, 41 newly installed, 0 to remove and 3 not upgraded.
Inst fonts-lato (2.0-2.1 Ubuntu:22.04/jammy [all])
Inst tex-common (6.17 Ubuntu:22.04/jammy [all])
Inst catdoc (1:0.95-5 Ubuntu:22.04/jammy [amd64])
Inst cinnamon-desktop-data (5.2.1-1 Ubuntu:22.04/jammy [all])
Inst cinnamon-l10n (5.2.2-1 Ubuntu:22.04/jammy [all])
Inst dvisvgm (2.13.1-1 Ubuntu:22.04/jammy [amd64])
Inst exif (0.6.22-2 Ubuntu:22.04/jammy [amd64])
Inst fonts-lmodern (2.004.5-6.1 Ubuntu:22.04/jammy [all])
Inst rubygems-integration (1.18 Ubuntu:22.04/jammy [all])
Inst rake (13.0.6-2 Ubuntu:22.04/jammy [all]) []
Inst ruby-net-telnet (0.1.1-2 Ubuntu:22.04/jammy [all]) []
Inst ruby-webrick (1.7.0-3 Ubuntu:22.04/jammy, Ubuntu:22.04/jammy-updates [all]) []
Inst ruby-xmlrpc (0.3.2-1ubuntu0.1 Ubuntu:22.04/jammy-updates [all]) []
Inst libruby3.0 (3.0.2-7ubuntu2.4 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64]) []
Inst ruby3.0 (3.0.2-7ubuntu2.4 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64]) []
Inst ruby-rubygems (3.3.5-2 Ubuntu:22.04/jammy [all]) []
Inst ruby (1:3.0~exp1 Ubuntu:22.04/jammy [amd64])
Inst ruby-json (2.5.1+dfsg-2build1 Ubuntu:22.04/jammy [amd64])
Inst gist (6.0.0-2 Ubuntu:22.04/jammy [all])
Inst hwdata (0.357-1 Ubuntu:22.04/jammy [all])
Inst id3 (1.1.2-3 Ubuntu:22.04/jammy [amd64])
Inst libcinnamon-desktop4 (5.2.1-1 Ubuntu:22.04/jammy [amd64])
Inst libgail-3-0 (3.24.33-1ubuntu2 Ubuntu:22.04/jammy-updates [amd64])
Inst libnemo-extension1 (5.2.4-1 Ubuntu:22.04/jammy [amd64])
Inst libptexenc1 (2021.20210626.59705-1ubuntu0.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst libteckit0 (2.5.11+ds1-1 Ubuntu:22.04/jammy [amd64])
Inst libtexlua53 (2021.20210626.59705-1ubuntu0.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst libtexluajit2 (2021.20210626.59705-1ubuntu0.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst xapps-common (2.2.8-1 Ubuntu:22.04/jammy [all])
Inst libxapp1 (2.2.8-1 Ubuntu:22.04/jammy [amd64])
Inst libzzip-0-13 (0.13.72+dfsg.1-1.1 Ubuntu:22.04/jammy [amd64])
Inst lmodern (2.004.5-6.1 Ubuntu:22.04/jammy [all])
Inst nemo-data (5.2.4-1 Ubuntu:22.04/jammy [all])
Inst xapp (2.2.8-1 Ubuntu:22.04/jammy [amd64])
Inst nemo (5.2.4-1 Ubuntu:22.04/jammy [amd64])
Inst nemo-fileroller (5.2.0-2 Ubuntu:22.04/jammy [amd64])
Inst odt2txt (0.5-7 Ubuntu:22.04/jammy [amd64])
Inst python3-xlrd (1.2.0-2 Ubuntu:22.04/jammy [all])
Inst t1utils (1.41-4build2 Ubuntu:22.04/jammy [amd64])
Inst texlive-binaries (2021.20210626.59705-1ubuntu0.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst texlive-base (2021.20220204-1 Ubuntu:22.04/jammy [all])
Conf fonts-lato (2.0-2.1 Ubuntu:22.04/jammy [all])
Conf tex-common (6.17 Ubuntu:22.04/jammy [all])
Conf catdoc (1:0.95-5 Ubuntu:22.04/jammy [amd64])
Conf cinnamon-desktop-data (5.2.1-1 Ubuntu:22.04/jammy [all])
Conf cinnamon-l10n (5.2.2-1 Ubuntu:22.04/jammy [all])
Conf dvisvgm (2.13.1-1 Ubuntu:22.04/jammy [amd64])
Conf exif (0.6.22-2 Ubuntu:22.04/jammy [amd64])
Conf fonts-lmodern (2.004.5-6.1 Ubuntu:22.04/jammy [all])
Conf rubygems-integration (1.18 Ubuntu:22.04/jammy [all])
Conf rake (13.0.6-2 Ubuntu:22.04/jammy [all])
Conf ruby-net-telnet (0.1.1-2 Ubuntu:22.04/jammy [all])
Conf ruby-webrick (1.7.0-3 Ubuntu:22.04/jammy, Ubuntu:22.04/jammy-updates [all])
Conf ruby-xmlrpc (0.3.2-1ubuntu0.1 Ubuntu:22.04/jammy-updates [all])
Conf libruby3.0 (3.0.2-7ubuntu2.4 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf ruby3.0 (3.0.2-7ubuntu2.4 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf ruby-rubygems (3.3.5-2 Ubuntu:22.04/jammy [all])
Conf ruby (1:3.0~exp1 Ubuntu:22.04/jammy [amd64])
Conf ruby-json (2.5.1+dfsg-2build1 Ubuntu:22.04/jammy [amd64])
Conf gist (6.0.0-2 Ubuntu:22.04/jammy [all])
Conf hwdata (0.357-1 Ubuntu:22.04/jammy [all])
Conf id3 (1.1.2-3 Ubuntu:22.04/jammy [amd64])
Conf libcinnamon-desktop4 (5.2.1-1 Ubuntu:22.04/jammy [amd64])
Conf libgail-3-0 (3.24.33-1ubuntu2 Ubuntu:22.04/jammy-updates [amd64])
Conf libnemo-extension1 (5.2.4-1 Ubuntu:22.04/jammy [amd64])
Conf libptexenc1 (2021.20210626.59705-1ubuntu0.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf libteckit0 (2.5.11+ds1-1 Ubuntu:22.04/jammy [amd64])
Conf libtexlua53 (2021.20210626.59705-1ubuntu0.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf libtexluajit2 (2021.20210626.59705-1ubuntu0.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf xapps-common (2.2.8-1 Ubuntu:22.04/jammy [all])
Conf libxapp1 (2.2.8-1 Ubuntu:22.04/jammy [amd64])
Conf libzzip-0-13 (0.13.72+dfsg.1-1.1 Ubuntu:22.04/jammy [amd64])
Conf lmodern (2.004.5-6.1 Ubuntu:22.04/jammy [all])
Conf nemo-data (5.2.4-1 Ubuntu:22.04/jammy [all])
Conf xapp (2.2.8-1 Ubuntu:22.04/jammy [amd64])
Conf nemo (5.2.4-1 Ubuntu:22.04/jammy [amd64])
Conf nemo-fileroller (5.2.0-2 Ubuntu:22.04/jammy [amd64])
Conf odt2txt (0.5-7 Ubuntu:22.04/jammy [amd64])
Conf python3-xlrd (1.2.0-2 Ubuntu:22.04/jammy [all])
Conf t1utils (1.41-4build2 Ubuntu:22.04/jammy [amd64])
Conf texlive-binaries (2021.20210626.59705-1ubuntu0.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf texlive-base (2021.20220204-1 Ubuntu:22.04/jammy [all])

```

---

### Post by Bashing-om on 2023-07-20
John Jason Jordan; Well ...

In Addition to MAFoElffen's advise
What release are you on ?
Show us:
```

lsb_release -a
sudo apt full-upgrade

```

as that package is available in jammy >
> 
sysop@x2204mini:~$ apt list libgail-3-0
Listing... Done
libgail-3-0/jammy-updates 3.24.33-1ubuntu2 amd64


[INDENT]which way did he go George
[/INDENT]

---

### Post by John Jason Jordan on 2023-07-21
[QUOTE=MAFoElffen;14151629]There are two more choices...

```
sudo apt full-upgrade 
```
will install new packages to try to satisfy dependency problems

That got me '... calculating upgrade ... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

```

sudo apt dist-upgrade

```
Is a more agressive approach and will both remove packages and install new packages to satisfy a dependency problem.

That got me exactly the same as above.

How did you try to install nemo? What command did you use? 

It was a month or two ago on a different computer, but also Xubuntu 22.04. And it installed without a problem, and it has been running fine ever since. The only thing I could mention is that installed a lot of Cinnamon, but my desktop is still Xfce4. The problem computer is a desktop that sits next to the one where it installed without a problem. And I should have mentioned this at the beginning, but I did a dist-upgrade on the desktop before I tried to install nemo on it.

---

### Post by John Jason Jordan on 2023-07-21
> **Bashing-om said:**
> John Jason Jordan; Well ...

In Addition to MAFoElffen's advise
What release are you on ?
Show us:
```

lsb_release -a
sudo apt full-upgrade

```

as that package is available in jammy >

OMG, the problem computer is on 20.04. I thought it was on 22.04. Waitaminnit!

OK, I did the dist-upgrade and the desktop (the problem computer) is now 22.04. That's the good news. The bad news is that 'sudo apt install nemo' now produces quite a list of unmet dependencies:

cinnamon-desktop-data
libcinnamon-desktop4
libnemo-extension1
nemo-data
xapp
libexempi8
libgail-3-0 <previously this is the only one I had>
libgsf-1-114
libxapp1

Plus a long list of 'recommends.' It also suggests 'apt --fix-broken install.' Even though I had tried that command before I did it again, and this time it did the same as last time, i.e., nothing. I'm dist-upgraded, but nemo is further from view than before. Oh, and Firefox bit the big one during the upgrade, although that has nothing to do with nemo. I can probably fix Firefox.

---

### Post by Bashing-om on 2023-07-21
John Jason Jordan --- Well well well 

> 
I did the dist-upgrade and the desktop (the problem computer) is now 22.04.

Well, a "dist-upgrade" is not a release upgrade to next version -- that operation is a do-release.

So, what release does the kernel think is installed?
```

cat /etc/issue
cat /etc/*-release

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]something real fishy is going on here [/INDENT]

---

### Post by John Jason Jordan on 2023-07-21
Well, I gave up trying to fix the broken packages. I tried about half a dozen commands tht everyone said would work, but they either did nothing at all or they aborted with the announcement 'cannot continue due to broken packages.' Not very helpful. Even upgrading from 20.04 to 22.04 only increased the problems, and didn't fix any broken packages. After the upgrade even Firefox won't work, and won't reinstall because of broken packages.

I decided to wipe it out and reinstall from scratch, but that turned out to be just as big a problem. I have a vision impairment that makes it difficult to focus up close. And on my 4K screen the font used in the install procedures is impossible for me to read. Yes, you can zoom the screen, but only after the installation is complete, *not on the installation screens*. I recall that when I installed 20.04 I had a friend help me, but right now I'm kind of stuck. 

I'm surprised that Ubuntu doesn't have anything for vision impairments. Maybe I can find a different distro that will make it easier.

---

### Post by ian-weisser on 2023-07-22
Rather than search for a different distro, why not help make the world's most popular Linux distro more accessible?

Developers have historically been very responsive to accessibility bugs that are reported.

The reason you are having accessibility problems in Ubuntu is that too few community members are looking for and reporting those accessibility bugs. You have the power to change that.

Community members interested in accessibility are welcome to revive the dormant Ubuntu Accessibility Team:  [https://wiki.ubuntu.com/Accessibility/Team](https://wiki.ubuntu.com/Accessibility/Team)

---

### Post by tea for one on 2023-07-22
> **John Jason Jordan said:**
> I'm surprised that Ubuntu doesn't have anything for vision impairments. Maybe I can find a different distro that will make it easier.
Settings > Accessibility > Always Show Accessibility Menu
More info [https://help.ubuntu.com/stable/ubuntu-help/a11y.html.en](https://help.ubuntu.com/stable/ubuntu-help/a11y.html.en)

---

### Post by John Jason Jordan on 2023-07-23
> **tea for one said:**
> Settings > Accessibility > Always Show Accessibility Menu
More info [https://help.ubuntu.com/stable/ubuntu-help/a11y.html.en](https://help.ubuntu.com/stable/ubuntu-help/a11y.html.en)

Sorry, that's a fail. What you refer to is a standard screen on an *installed* Ubuntu. The accessibility options do not exist on the screen for the 'try Ubuntu' or the later 'install now.'

Just to be sure I rebooted the ISO on a flash drive. The top bar is two millimeters high, and any text in it is even skinnier. Even for a person with no visual problems it is utterly unreadable. Mind you, the install ISO assumes a VGA screen, or maybe 2K max. My screen is 4K, but te install ISO offers no way to change the resolution so you can read the instructions.

---

### Post by tea for one on 2023-07-23
Not strictly "a fail".
As you have discovered, it probably depends on your display/monitor.

You can use Accessibility settings in a "Try Ubuntu" session via Show Applications > Settings > Accessibility
The icon also appears in the top bar.
My default screen resolution is 1920 x 1080

You can also change the resolution in a live session via Show Applications > Settings > Display

Tested using Ubuntu 22.04 live

---

