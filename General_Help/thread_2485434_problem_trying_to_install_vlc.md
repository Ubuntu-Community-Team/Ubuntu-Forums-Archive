---
title: "problem trying to install vlc"
date: 2023-03-29
forum: General Help
---

### Post by jgw on 2023-03-29
Tried synaptic but failed:

The following packages have unmet dependencies:
 libchromaprint1 : Depends: libavcodec59 (>= 7:5.0)
 vlc-plugin-base : Depends: libavcodec58 (>= 7:4.4)
                   Depends: libavformat58 (>= 7:4.4)
 vlc-plugin-video-output : Depends: libavcodec58 (>= 7:4.4)
E: Unable to correct problems, you have held broken packages.

Thoughts?

---

### Post by SeijiSensei on 2023-03-29
Have you run
```
sudo apt update; sudo apt full-upgrade
```
lately?

Try installing vlc from the command line with
```
sudo apt install vlc
```
It might give you suggested options to try.

I'm running 22.04.2 and have no problems updating vlc. Actually I prefer smplayer with mpv as the player engine.

---

### Post by jgw on 2023-03-29
Thank you for the reply!

Here is the update and full-upgrade:
[https://pastebin.ubuntu.com/p/sn3nFqhFHF/](https://pastebin.ubuntu.com/p/sn3nFqhFHF/)

Here is what happened when I tried to install vlc:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libchromaprint1 : Depends: libavcodec59 (>= 7:5.0)
 vlc-plugin-base : Depends: libavcodec58 (>= 7:4.4)
                   Depends: libavformat58 (>= 7:4.4)
 vlc-plugin-video-output : Depends: libavcodec58 (>= 7:4.4)
E: Unable to correct problems, you have held broken packages.

```
Then I tried to install smplayer and got:
```
greg@greg2:~$ sudo apt-get install smplayer smplayer-themes -y
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 smplayer : Depends: mplayer but it is not installable or
                     mplayer-nogui but it is not installable or
                     mpv (>= 0.6.2) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

This is a real mystery and, apparently, impacts a lot of different aps.

---

### Post by Holger_Gehrke on 2023-03-29
You might want to take a look at 'apt policy libchromaprint1'. It could be you've got some PPA or external repository active that offers a version of this that depends on a newer version of libavcodec than the standard repositories have.

Holger

---

### Post by MAFoElffen on 2023-03-30
From your signature, it says you are running 22.04.1...

But this:
> 
libchromaprint1 : Depends: libavcodec59 (>= 7:5.0)

Package libavcodec59 does not show up in the Ubuntu Repo's until 22.10 and 23.04. When i look up the depends for libchromaprint1, for jammy, I see
```

libavcodec58 (>= 7:4.4)
    FFmpeg library with de/encoders for audio/video codecs - runtime files 

libavutil56 (>= 7:4.4)
    FFmpeg library with functions for simplifying programming - runtime files 

libc6 (>= 2.29)
    GNU C Library: Shared libraries 

libgcc-s1 (>= 3.3.1) [not armhf, i386]
    GCC support library 

libgcc-s1 (>= 3.5) [armhf]

libgcc-s1 (>= 4.2) [i386]

libstdc++6 (>= 11)
    GNU Standard C++ Library v3 

```
Which makes me curious in how you tried to install VLC, on what release... I see that Holger saw that. 

Please. Do tell.

EDIT 1:
It is possibly a conflict via ppa:savory1. From his own notes on that PPA:
> 
Note on bugs: If you have third-party PPAs (ie. other than  ppa:savoury1/*) on your system please do NOT report packaging conflicts  or upgrade issues (ie. APT package management wanting to remove packages  due a conflict) as the only setups I can possibly attempt to support  are those that have only my PPAs (ppa:savoury1/*) added. When any  third-party PPAs are added it can exponentially increase potential  issues, due different people doing their packaging in very different  ways that can easily create package conflicts.


---

### Post by ActionParsnip on 2023-03-30
What is the output of
```

apt-cache policy vlc vlc-plugin-base libavcodec58

```

---

### Post by jgw on 2023-03-31
Hope this is ok:

```
greg@greg2:~$ apt-cache policy vlc vlc-plugin-base libavcodec58
vlc:
  Installed: (none)
  Candidate: 3.0.16-1build7
  Version table:
     3.0.16-1build7 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
vlc-plugin-base:
  Installed: (none)
  Candidate: 3.0.16-1build7
  Version table:
     3.0.16-1build7 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
libavcodec58:
  Installed: (none)
  Candidate: 7:4.4.3-0ubuntu1~22.04.sav3
  Version table:
     7:4.4.3-0ubuntu1~22.04.sav3 500
        500 https://ppa.launchpadcontent.net/savoury1/ffmpeg4/ubuntu jammy/main amd64 Packages
     7:4.4.2-0ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages
     7:4.4.1-3ubuntu5 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
greg@greg2:~$ 

```

---

### Post by ActionParsnip on 2023-03-31
Remove the PPA and install VLC without issue

---

### Post by ActionParsnip on 2023-03-31
I also suggest you use ppa-purge to do this so that packages are rolled back.

---

### Post by SeijiSensei on 2023-03-31
```
     7:4.4.3-0ubuntu1~22.04.sav3 500
        500 https://ppa.launchpadcontent.net/savoury1/ffmpeg4/ubuntu jammy/main amd64 Packages

```
I'd disable this source and use the version of ffmpeg shipped with Ubuntu. 

You might be running afoul of [this]("https://launchpad.net/~savoury1"):
> UPDATE (24 Mar 2023): The PPAs at this Launchpad site are now moving to a subscriber only (those who have donated) system. Given how many people and businesses are using these PPAs that I've put thousands of hours of energy into creating, and given the tiny amount of donations from all those many people and businesses, it is now necessary for the sake of my survival to restrict access to the most popular software at these PPAs to supporters.

```

sudo add-apt-repository remove ffmpeg4
sudo apt-get remove --purge ffmpeg4
sudo apt install ffmpeg vlc

```

---

### Post by RobertLos on 2023-04-01
I solved this by first removing the savoury1-ubuntu-ffmpeg* files in /etc/apt/source.list.d, than doing an apt upgrade and reinstall mplayer and vlc

---

### Post by ActionParsnip on 2023-04-02
> **RobertLos said:**
> I solved this by first removing the savoury1-ubuntu-ffmpeg* files in /etc/apt/source.list.d, than doing an apt upgrade and reinstall mplayer and vlc

Why add a PPA when VLC is in the default repositories?

---

### Post by monkeybrain20122 on 2023-04-02
> **ActionParsnip said:**
> Why add a PPA when VLC is in the default repositories?

Because the default version is old?

That being said I strongly recommend against adding ppas by Rob Savoury. These ppas upgrade too many packages unnecessarily, which make them very brittle. Moreover he spreads the dependencies over multiple repos. For examples, to upgrade vlc you have to add the fmpeg4 repo, to upgrade mpv, you have to add the ffmpeg 4 and ffmpeg 6 repo and mpv doesn't need ffmpeg6 to compile or run. This creates a web of dependencies very difficult to unentangle and you can't purge them with ppa-purge (which works vor only single repo as far as I know) Now he suddenly decides to restrict his repos to subscribers only because he wants to make a buck but the way he does it is to leave the old repos on and put additional dependencies in some hidden repos that only paid subscribers can access. When he pushes out an upgrade,if an unsuspecting user who added his free repos before tries to do an routine upgrade with synaptic, it will remove the packages already installed because of unmet dependencies and may remove half of the system (but apt upgrade from terminal would just hold back those packages) I have created a ticket against him. [https://answers.launchpad.net/launchpad/+question/705950](https://answers.launchpad.net/launchpad/+question/705950)
 
I used to use mc4man's excellent ffmpeg and mpv ppa but he has disappeared for a while (hope he is ok), so when I installed 22.04 I added savoury's to give mpv a quick spin. I soon realized it was a bad call, so I disabled them and compiled ffmpeg and mpv myself but I couldn't manually downgrade all the packages.


@OP you can get updated version of vlc from flatpak.It works great.

---

### Post by ActionParsnip on 2023-04-02
If the version in the repositories does what is needed then "old" is irrelevant.
If there are significant issues with the version in the repositories then the package will be updated. Stop blindly chasing version numbers and you'll find IT is easier to use and manage. You're probably trying to fix something that isn't broken

---

### Post by jgw on 2023-04-02
thank you for the reply.  

I tried the suggestion and got:
greg@greg3:~$ sudo add-apt-repository remove ffmpeg4
[sudo] password for greg: 
Unable to handle repository shortcut 'remove ffmpeg4'
greg@greg3:~$ sudo apt-get remove --purge ffmpeg4
W: Not using locking for read only lock file /var/lib/dpkg/lock-frontend
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
greg@greg3:~$ sudo dpkg --configure -
dpkg: error: unable to access the dpkg database directory /var/lib/dpkg: Read-only file system
greg@greg3:~$

---

### Post by monkeybrain20122 on 2023-04-02
To disable the savoury repositories do **one** of the followings:

1) open software&update and uncheck the boxes of the ppas and then click reload

2) delete the ppas' entries in /etc/apt/sources.list.d then update, for example, to disable all the savoury repos

```
sudo rm /etc/apt/sources.list.d/savoury1*


```

then 

```
sudo apt update
```



3) ```
 sudo add-apt-repository remove ppa:savoury1/ffmpeg4
``` 

do the same for the vlc one

Note you have to use the full apt line for the ppa, not just ffmpeg4


then

```
sudo apt update
```


Do either **one** of the above would disable the repos, but it won't remove or downgrade the packages that you have already installed from the ppas. You have to remove them manually with sudo apt remove, as noted removing ffmpeg may break your system (look also at what packages become autoremovable) so you might as well keep it. vlc should be safe to remove. After that you can get the flatpak.

---

### Post by jgw on 2023-04-05
Thank you for the reply and the codes.  VLC is now installed.

---

