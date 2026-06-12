---
title: "Unable to install ffmpeg in Bionic, and held packages"
date: 2021-08-29
forum: General Help
---

### Post by goodstuff9 on 2021-08-29
[COLOR=#000000]I used to have ffmpeg installed on my system, but somehow – I don’t know how or when – it got uninstalled. So, I tried installing ffmpeg via Synaptic. But when I mark it for installation, it gets the red exclamation mark indicating a broken package.[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]As I looked into this, I also discovered that in the past few days my system says that I have three packages that are “kept back”, and, although the system says they are ready to be updated, they never do update. The three packages are:[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]libavcodec58[/COLOR]
[COLOR=#000000]libavutil56[/COLOR]
[COLOR=#000000]libswresample3[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]sudo apt list –upgradable gives this result:[/COLOR]
[COLOR=#000000]libavcodec58/bionic 7:4.3-2~18.04.york0 amd64 [upgradable from: 7:4.1.3-0ppa1~18.04][/COLOR]
[COLOR=#000000]libavutil56/bionic 7:4.3-2~18.04.york0 amd64 [upgradable from: 7:4.1.3-0ppa1~18.04][/COLOR]
[COLOR=#000000]libswresample3/bionic 7:4.3-2~18.04.york0 amd64 [upgradable from: 7:4.1.3-0ppa1~18.04][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]sudo apt upgrade gives this result:[/COLOR]
[COLOR=#000000]The following packages have been kept back:[/COLOR]
[COLOR=#000000]libavutil56 libswresample3[/COLOR]
[COLOR=#000000]0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]I had the idea to just uninstall those three packages, and then try reinstalling them, but….. I didn’t do that, uninstalling any one of them via Synaptic gave me a message that a LONG list of packages would also be uninstalled – basically, every multimedia application I have, such as Audacity, VLC, etc.[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]I’ve been reading LOTS of answers to others’ questions on this and other sites, but unfortunately they all leave me even more confused about what is wrong and what to do. So, I turn here for help.

Why am I not able to upgrade these three packages? How do I fix that problem/[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]How do I install ffmpeg from Synaptic without getting a broken package error message?[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Thanks in advance for help.[/COLOR]

---

### Post by &amp;KyT$0P# on 2021-08-30
Please post the output from running this command in Terminal -
```
apt-get -s dist-upgrade
```
(It won't actually change anything, it is just a dry-run/simulation telling you what would happen.)

---

### Post by goodstuff9 on 2021-08-30
```
apt-get -s dist-upgradeNOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libavutil56 libswresample3
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

---

### Post by &amp;KyT$0P# on 2021-08-30
Does [FONT=Courier New]apt-mark showhold[/FONT] output anything?

---

### Post by goodstuff9 on 2021-08-30
> **halogen2 said:**
> Does [FONT=Courier New]apt-mark showhold[/FONT] output anything?

It shows nothing.

---

### Post by &amp;KyT$0P# on 2021-08-30
It appears you have multiple PPAs containing different ffmpeg-related packages that are conflicting with each other.  To see which PPA(s) are blocking installing ffmpeg, please post the output from running these commands in Terminal -
```
apt-cache policy ffmpeg
apt-get -s install ffmpeg
```

The first one should tell you from where ffmpeg is trying to be installed, the second one should show what's blocking it.

---

### Post by goodstuff9 on 2021-08-30
```
apt-cache policy ffmpegffmpeg:
  Installed: (none)
  Candidate: 7:4.3-2~18.04.york0
  Version table:
     7:4.3-2~18.04.york0 500
        500 http://ppa.launchpad.net/ubuntuhandbook1/apps/ubuntu bionic/main amd64 Packages
     7:4.1.3-0ppa1~18.04 500
        500 http://ppa.launchpad.net/cybermax-dexter/sdl2-backport/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
     7:3.4.8-0ubuntu0.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     7:3.4.2-2 500
        500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
```


```
apt-get -s install ffmpegNOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ffmpeg : Depends: libavcodec58 (= 7:4.3-2~18.04.york0)
          Depends: libavdevice58 (= 7:4.3-2~18.04.york0) but it is not going to be installed
          Depends: libavfilter7 (= 7:4.3-2~18.04.york0)
          Depends: libavformat58 (= 7:4.3-2~18.04.york0) but it is not going to be installed
          Depends: libavresample4 (= 7:4.3-2~18.04.york0) but it is not going to be installed
          Depends: libavutil56 (= 7:4.3-2~18.04.york0) but 7:4.1.3-0ppa1~18.04 is to be installed
          Depends: libpostproc55 (= 7:4.3-2~18.04.york0) but it is not going to be installed
          Depends: libswresample3 (= 7:4.3-2~18.04.york0) but 7:4.1.3-0ppa1~18.04 is to be installed
          Depends: libswscale5 (= 7:4.3-2~18.04.york0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by &amp;KyT$0P# on 2021-08-30
Those outputs suggest the 4.1.3-0ppa1~18.04 ffmpeg packages might cause less conflicts than the 4.3-2~18.04.york0 versions.  Can you install ppa-purge and use it to remove the ubuntuhandbook1 PPA?

Refer to [FONT=Courier New]ppa-purge --help[/FONT] for more info before actual use

---

### Post by goodstuff9 on 2021-08-30
Thank you very much for your advice.  

Yes, I will try that.  That might take more time than I have right now, I will try later today.  

I have never used PPA purge before.  My understanding from reading is that if it can downgrade the packages, it will, otherwise it will uninstall the package; and, will give me a chance to review what it plans to do before doing it.  Am I understanding it correctly?

---

### Post by &amp;KyT$0P# on 2021-08-30
> **goodstuff9 said:**
> My understanding from reading is that if it can downgrade the packages, it will, otherwise it will uninstall the package; and, will give me a chance to review what it plans to do before doing it.  Am I understanding it correctly?

By default it will ask your confirmation before any changes to installed packages on your system.  It will however disable the PPA without asking, but (as I understand it) if you decide you don't like the changes to installed packages, you can say no to that and just re-enable the PPA in Software & Updates and you're back to where you were before.

---

### Post by goodstuff9 on 2021-08-30
purging the PPA solved the problem, thank you.

---

