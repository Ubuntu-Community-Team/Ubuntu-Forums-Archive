---
title: "Miro: Depends libxine1 (&lt;1.1.8) but 1.1.10-1~gutsy1 is to be installed"
date: 2008-02-26
forum: General Help
---

### Post by Buffalo Soldier on 2008-02-26
I'm using Ubuntu 7.10 (386 version) and trying to install miro (1.1.2-0pcf2) but experiencing a dependency problem.

> miro: Depends: libxine1 (<1.1.8) but 1.1.10-1~gutsy1 is to be installed

I'm using the repo stated at the [official miro site]("http://www.getmiro.com/download/ubuntu.php"). Here's my source.list:
```
deb http://tw.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://tw.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://tw.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://tw.archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy partner

deb http://ppa.launchpad.net/dell-team/ubuntu gutsy main

deb http://packages.medibuntu.org/ gutsy free non-free
deb http://www.virtualbox.org/debian gutsy non-free
**deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu gutsy/**
```

Any ideas?

---

### Post by kiloxxx on 2008-02-26
Hi, exactly the same problem here, but no suggestions...
I've tried to downgrade libxine1, but it creates problems with other multimedia players.

---

### Post by ben2talk on 2008-02-26
I met this problem too. Initially through a problem with Avant Window Navigator, when I click an application on there, it misses the correct desktop - so if I have Firefox on screen 2, and I click it from Screen 1, then I shoot over to screen 3....

Uninstalling AWN and reinstalling proved a problem, with broken packages and a conflict with Miro. I think uninstalled Miro, and can't get it back because of the libzine1 library. I assume it was updated recently and broke my AWN and Miro - anyway to take libzine1 back and check to ensure this was the only problem?

---

### Post by bechir on 2008-02-26
Hi all,

You have to disable the "backports" repository in your /etc/apt/sources.list.
libxine1 1.1.10 is provided by this repository.

So, comment all the lines containing gutsy-backports in /etc/apt/sources.list

After that:

```

$> sudo apt-get update

$> sudo apt-get remove libxine1 
# Note the huge amount of package that will be deleted because they depend on libxine1

$> sudo apt-get install libxine1

# And finally:

$> sudo apt-get install <all the packages deleted during the suppression on libxine1 1.1.10> 
# Some of them may be not found because they were provided by the bacports"
# repository but this is the price to pay to have Miro woring again

```

Hope this helps :-)

-- 
Bechir

---

### Post by kiloxxx on 2008-02-27
In my case Miro - version 1.1.2 r6358 - doesn't stop to work, only it is impossible to upgrade it without downgrading libxine1. For people who can't use Miro, I think is better - and easier - to downgrade Miro and to comment out its repository.

---

### Post by bigbooger on 2008-02-29
> **bechir said:**
> Hi all,

You have to disable the "backports" repository in your /etc/apt/sources.list.
libxine1 1.1.10 is provided by this repository.

So, comment all the lines containing gutsy-backports in /etc/apt/sources.list

After that:

```

$> sudo apt-get update

$> sudo apt-get remove libxine1 
# Note the huge amount of package that will be deleted because they depend on libxine1

$> sudo apt-get install libxine1

# And finally:

$> sudo apt-get install <all the packages deleted during the suppression on libxine1 1.1.10> 
# Some of them may be not found because they were provided by the bacports"
# repository but this is the price to pay to have Miro woring again

```

Hope this helps :-)

-- 
Bechir

This really straightened up my issues with Miro. Muchas Gracias!

---

### Post by go_beep_yourself on 2008-03-03
There's no reason to disable backports. Miro is so stupid that it can't figure out that 1.10-1 is (greater than) < 1.1.8, so do this instead.

```
wget http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu/gutsy/miro_1.1.2-0pcf2_i386.deb
wget http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu/gutsy/miro-data_1.1.2-0pcf1_all.deb
sudo dpkg --force-depends -i miro_1.1.2-0pcf2_i386.deb miro-data_1.1.2-0pcf1_all.deb 
sudo apt-get -f install
```

My experience using Linux and 64 bit software for the last few years has helped me figure this one out. If those links are outdated, then go to the repository and manually download the latest from there. Miro is running fine here on this 32 bit machine that I am fixing up for my girlfriend.

---

### Post by bechir on 2008-03-03
> **go_beep_yourself said:**
> There's no reason to disable backports. Miro is so stupid that it can't figure out that 1.10-1 is (greater than) < 1.1.8, so do this instead.

```
wget http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu/gutsy/miro_1.1.2-0pcf2_i386.deb
wget http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu/gutsy/miro-data_1.1.2-0pcf1_all.deb
sudo dpkg --force-depends -i miro_1.1.2-0pcf2_i386.deb miro-data_1.1.2-0pcf1_all.deb 
sudo apt-get -f install
```



The actual problem is that Miro does not work well with libxine1 ">= 1.1.8". For this reason, the Miro developers added the dependency "< 1.1.8" to the package.

So, if you do as you said, this will indeed install Miro, but you may experience several problems when playing videos (sporadic segfaults...).

---

### Post by go_beep_yourself on 2008-03-03
No segfaults yet, but you can download the libxine package it is looking for, extract the lib, and run it Miro like this

```
LD_PRELOAD=/path/to/libnname.lib miro
```

Compiling is also possible! I'm experimenting with the debian control file right now.

---

### Post by firefeather on 2008-03-04
When I then run ```
sudo apt-get -f install
``` then Miro is simply removed.

> **go_beep_yourself said:**
> There's no reason to disable backports. Miro is so stupid that it can't figure out that 1.10-1 is (greater than) < 1.1.8, so do this instead.

```
wget http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu/gutsy/miro_1.1.2-0pcf2_i386.deb
wget http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu/gutsy/miro-data_1.1.2-0pcf1_all.deb
sudo dpkg --force-depends -i miro_1.1.2-0pcf2_i386.deb miro-data_1.1.2-0pcf1_all.deb 
sudo apt-get -f install
```

My experience using Linux and 64 bit software for the last few years has helped me figure this one out. If those links are outdated, then go to the repository and manually download the latest from there. Miro is running fine here on this 32 bit machine that I am fixing up for my girlfriend.

---

### Post by ben2talk on 2008-03-05
I find the same problem. After installation, Miro 1.1.2 works (apparently) quite well, but then there is a broken package! Is there no way to simply modify the system so that Miro will use the new lib?

---

### Post by dubski on 2008-03-08
Thanks heaps for this.  Worked for me.
;-)

---

### Post by kmak on 2008-03-10
[SIZE="3"]Updated:[/SIZE]

Turns out libxine has seen significant improvements in security and functionality since 1.1.7 and apt spews annoying messages about broken packages every time I try to update.

I went back to the newer libxine (I had noticed some video playback was worse under 1.1.7) and installed the previous version of miro and miro-data and will just have to risk Miro crashing until they decide to play nice with libxine.

Btw, did this affect Hardy users? The beta comes out in two days and I'm thinking about going for it.

[SIZE="3"]Original post:[/SIZE]

Apparently bugs in the gutsy-backports repository version of libxine( 1.1.10 ) caused Miro to crash. Miro dependencies for libxine were changed to libxine( < 1.1.8 ) to work around these issues.

I did the following to downgrade libxine to version 1.1.7 without having to completely disable 'gutsy-backports' repository:

```
sudo aptitude install miro
```

This prompts a Miro reinstall which causes apt to complain that things are broken and offer me a solution:

```
The following packages are BROKEN:
  miro 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2072kB of archives. After unpacking 8192B will be used.
The following packages have unmet dependencies:
  miro: Depends: libxine1 (< 1.1.8) but 1.1.10-1~gutsy1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libxine1-bin
libxine1-misc-plugins
libxine1-x

Install the following packages:
libxine1-doc [1.1.10-1~gutsy1 (gutsy-backports)]
libxine1-gnome [1.1.7-1ubuntu1 (gutsy)]

Downgrade the following packages:
libxine1 [1.1.10-1~gutsy1 (gutsy-backports, now) -> 1.1.7-1ubuntu1 (gutsy)]
libxine1-console [1.1.10-1~gutsy1 (gutsy-backports, now) -> 1.1.7-1ubuntu1 (gutsy)]
libxine1-ffmpeg [1.1.10-1~gutsy1 (gutsy-backports, now) -> 1.1.7-1ubuntu1 (gutsy)]
libxine1-plugins [1.1.10-1~gutsy1 (gutsy-backports, now) -> 1.1.7-1ubuntu1 (gutsy)]

Score is -981

Accept this solution? [Y/n/q/?] **y**
```

Yes, I accept. This basically says it will remove the backported libxine and install the official version from the 'gutsy' repo, which is what I want, despite the negative score. I have no idea why apt installed the documentation for version 1.1.10, but if that makes apt happy, then so be it!

**Note:** I always use aptitude and have no idea if apt-get will do the same. Probably will. YMMV

I'll have to wait and see if this affects other aspects of my system.

---

### Post by go_beep_yourself on 2008-03-18
What's the score mean with aptitude? I stopped using aptitude since it broke my computer twice and the new apt-get version that does auto-remove.

---

### Post by kmak on 2008-03-19
Yeah, I'm also baffled by the whole apt scoring thing. I use aptitude mostly out of habit -- I don't guess it really matters anymore, huh? I've never found an authoritative answer about this, but I suppose it's pretty OT for this thread.

---

### Post by Tanker Bob on 2008-03-20
Thanks kmak for posting this solution. It worked for me, with a bit more explanation. I regret that I didn't think to save the recovery session, though.

When I first installed Miro with aptitude, it offered to uninstall Kubuntu desktop, Dolphin, Amarok, as well as the libxine files. I didn't want to lose all that, so I typed 'n'. To my surprise, aptitude offered me a different solution. After five or six times answering 'n' and getting succeedingly different solutions and scores, aptitude finally offered just to uninstall Amarok and some libxine files while downgrading other libxine files. I agreed to that approach and everything worked fine after assuring aptitude several times that I wanted to downgrade some files.

aptitude appears to have some significant smarts, and to our benefit.

---

### Post by deodatus on 2008-03-22
This worked for me as well. (aptitude)

---

### Post by theToolman on 2008-04-16
Kudos for this; tried to manually adjust in synaptic but it didn't like what i was trying; aptitude came up with the right solution :)

All media players stil work for me and i have the backports still there for anything else i want.  Not sure about the performance differences mentioned with 1.1.7 vs 1.1.10+ but miro is cool, so i have to put up with 1.1.7.

---

### Post by abhiroopb on 2008-05-21
Got a solution from aptitude but it involved in the removal of amarok and installation of libgpod2. I recently managed to get libgpod3 installed and working with amarok for my iPod, so the aptitude's solution is not working (it gives more than one but they all involve very similar things!).

---

### Post by abhiroopb on 2008-05-21
EASY SOLUTION:

go to getdeb.net and download FIRST the miro-data package and the the miro package and double click on them to install: [http://www.getdeb.net/app/Miro](http://www.getdeb.net/app/Miro)

BUT, when I open the player (v 1.2) it opens for a bit and crashes:

from the terminal:
```


abhiroop@Vanimo:~$ miro
INFO     Starting up Miro
INFO     Version:    1.2
INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.2/tv/resources - 6612
INFO     Builder:    build@build
INFO     Build Time: 1206533156.18
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/abhiroop/.miro/sqlitedb
INFO     Spawning global feed dtv:manualFeed
INFO     Spawning global feed dtv:singleFeed
INFO     Spawning global feed dtv:search
INFO     *** Launching Downloader Daemon ****
INFO     Spawning global feed dtv:searchDownloads
INFO     wbg: setting autodownload stuff initially to new
INFO     Spawning global feed dtv:directoryfeed
INFO     wbg: setting autodownload stuff initially to new
INFO     Creating channel tab order
INFO     Creating playlist tab order
INFO     Spawning Miro Guide...
INFO     Spawning auto downloader...
TIMING   Icon clear: 0.001
INFO     Starting movie data updates
INFO     Adding default feeds
INFO     Displaying main frame...
INFO     Creating video display...
INFO     Finished startup sequence
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
INFO     loaded renderer 'xinerenderer'

** (miro.real:18996): WARNING **: Invalid borders specified for theme pixmap:
        /home/abhiroop/.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Range/null.png,
borders don't fit within the image

** (miro.real:18996): WARNING **: Invalid borders specified for theme pixmap:
        /home/abhiroop/.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Frame-Gap/frame1.png,
borders don't fit within the image
INFO     got file:///tmp/tmpBjMCkQ.html
INFO     First URL is https://www.miroguide.com/firsttime
TIMING   idle (select initial tab) too slow (0.527 secs)
INFO     *** Daemon ready ***
INFO     got file:///tmp/tmpGD4nve.html
INFO     First URL is https://www.miroguide.com/
INFO     got file:///usr/share/miro/resources/html/guide-navigation.html
INFO     First URL is https://www.miroguide.com/
INFO     got about:blank
INFO     First URL is https://www.miroguide.com/
INFO     got https://www.miroguide.com/firsttime
INFO     First URL is https://www.miroguide.com/
/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
abhiroop@Vanimo:~$ 

```
HELP!!!

---

### Post by vamsibethapudy on 2008-06-12
I think the problem is solved. i have upgraded & the upgradation removed miro for some reason.
I just went to the miro site & copied the ftp link given in another forum & reloaded. i used add or remove programs & miro is installed.
:guitar::lolflag:
 you can mark this thread as solved

---

