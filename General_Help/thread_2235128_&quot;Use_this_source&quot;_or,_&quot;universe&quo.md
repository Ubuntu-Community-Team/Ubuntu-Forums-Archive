---
title: "&quot;Use this source&quot; or, &quot;universe&quot;"
date: 2014-07-19
forum: General Help
---

### Post by salmichaels on 2014-07-19
I was trying to install chromium b/c firefox was on the blink, when something weird happened. Software Center told me that something was needed that it couldn't get, I don't remember what, and can't make that happen again. Because now when I try to install it through software center it doesn't have the install button, it just says "Use this source". In fact, that's what everything in software center says. The install button is completely gone. I've tried a few things suggested on the web, nothing has worked. I've seen people reporting almost the exact same problem, and the posted fixes worked for them, but not for me.

UPDATE: I was desparately trying to fix the problem and tried removing the software center for reinstall, but when I tried to get it back it won't reinstall. There's no application candidate, neither is there with synaptic. My machine's a mess!

---

### Post by ajgreeny on 2014-07-19
Open a terminal and run commands ```
sudo apt-get update
sudo apt-get upgrade
``` and report back here with the output or any error messages you get.
(in code tags please, highlight the text in the reply box and click on the # in toolbar above)

---

### Post by buzzingrobot on 2014-07-19
The name of the package is "software-center". Synaptic should install it.

---

### Post by salmichaels on 2014-07-21
I can't get synaptic, no candidate. 

apt-get update: 

 ```
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring Release.gpgIgn [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates Release.gpg                         
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports Release.gpg                       
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security Release.gpg                        
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring Release                                     
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates Release                             
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports Release
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release    
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US    
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring/main i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring/restricted i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring/universe i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring/multiverse i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring/main Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring/main Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring/multiverse Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring/multiverse Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring/restricted Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring/restricted Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring/universe Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring/universe Translation-en
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates/main i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates/restricted i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates/universe i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates/multiverse i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates/main Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates/main Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates/multiverse Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates/multiverse Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates/restricted Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates/restricted Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates/universe Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-updates/universe Translation-en
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports/main i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports/restricted i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports/universe i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports/multiverse i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports/main Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports/main Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports/multiverse Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports/multiverse Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports/restricted Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports/restricted Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports/universe Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-backports/universe Translation-en
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security/main i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security/restricted i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security/universe i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security/multiverse i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security/main Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security/main Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security/multiverse Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security/multiverse Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security/restricted Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security/restricted Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security/universe Translation-en_US
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) raring-security/universe Translation-en
W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring/main/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring/restricted/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring/restricted/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring/universe/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring/universe/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring/multiverse/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring/multiverse/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring-updates/main/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring-updates/universe/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring-updates/universe/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring-backports/main/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring-backports/main/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring-backports/restricted/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring-backports/universe/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring-backports/universe/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring-security/main/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring-security/main/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring-security/restricted/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring-security/restricted/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring-security/universe/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring-security/universe/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/raring-security/multiverse/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/raring-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://ppa.launchpad.net/chris-lea/munin-plugins/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/chris-lea/munin-plugins/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by salmichaels on 2014-07-21
Of apt-get upgrade: 

>  Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by deadflowr on 2014-07-21
Raring is EOL.
You won't be getting anything useful with it, as the repos are gone.

Best avenue is to upgrade, (or downgrade to 12.04) to a supported release.

edit: Adding this for you reading pleasure:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by salmichaels on 2014-07-21
There must be some better suggestion out there. If nothing else, I'd like to know what happened.

---

### Post by coldcritter64 on 2014-07-21
> **salmichaels said:**
> There must be some better suggestion out there. If nothing else, **I'd like to know what happened.**

> **deadflowr said:**
> **Raring is EOL.**
You won't be getting anything useful with it, as **the repos are gone.**

Best avenue is to upgrade, (or downgrade to 12.04) to a supported release.

edit: Adding this for you reading pleasure:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

EOL means "End Of Life". That is, it is no longer supported hence the repositories have been removed. I **can't** even **find** the repos for Raring on [noparse]http://old-releases.ubuntu.com/releases/[/noparse]as was the case for older releases up to 11.10.

Sorry to say, but it looks like you will need to upgrade to 14.04 or downgrade to 12.04 as has been mentioned. edit: or one of the current intermediate releases, however a long term support (LTS) release like 12.04 or 14.04 is a better option if you don't like reinstalling/upgrading.

---

### Post by deadflowr on 2014-07-21
I think raring, in particular, is in flux.
For the record, it when out of support in January.

Perhaps it all has to do with 12.04.5 point release coming in a few weeks.
That point release, which has seen a few snags already, will be upgrading versions of 12.04 that were installed from either 12.04.2, .3, .or .4 point release iso's.
Each one of those was based and the hardware stack of standard releases, such as quantal, raring and saucy.
For whatever that may mean for the lost repos.

All that said, we won't be supporting anyone trying to fix issues with any of those which have hit EOL.

We will, however, help anyone in such a state with the help needed to upgrade.
Be it best option (install or upgrade), or which back method to use.

---

### Post by salmichaels on 2014-07-21
i've never done an upgrade before. I just don't wanna start from scratch. It took me a whole weekend to get this thing going to where it was. 

And all this time telling all my broke mac using friends and frustrated windows using friends that I had the better thing. . . One day, it pretty much stops functioning.

---

### Post by mc4man on 2014-07-21
Before this thread is closed.
Just add the old-release repo for raring. 
Many examples of how here (though note none are specific to raring

I think the  last answer by Stuart Cook is the best/easiest, just tried here on an old raring install, worked fine
[http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release)

eg. - add [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) as a mirror, then switch to that mirror in Software Sources & update your sources, ect.

---

### Post by salmichaels on 2014-07-22
I am still not sure what I should do to solve this problem.

---

### Post by salmichaels on 2014-07-22
I tried to update, but this is the response that I get: 

"Failed to download repository information"

"Check your internet connection"

---

### Post by deadflowr on 2014-07-22
> **salmichaels said:**
> I am still not sure what I should do to solve this problem.

> **salmichaels said:**
> I tried to update, but this is the response that I get: 

"Failed to download repository information"

"Check your internet connection"

Unfortunately, neither of these two posts help us to understand what you have tried to do.
Did you try changing to the old release repos as suggested by mc4man?
Or were you doing something else, entirely?

Off-topic, but thinking about it, did raring go end of life before the fix for the heartbleed openssl bug?
Just a thought.

---

### Post by salmichaels on 2014-07-24
I tried that but when I went to source.list it was completely blank. I tried rebuilding it but I messed something up, I don't know what, and it works no better. I think this might have been the issue in the first place? I know this is my fault for not updating regularly, but good lord, what a punishment for not upgrading! 

Is this a fixable problem or am I looking at the labor of a wipe and reinstall?

---

### Post by buzzingrobot on 2014-07-24
> **salmichaels said:**
> I tried that but when I went to source.list it was completely blank. I tried rebuilding it but I messed something up, I don't know what, and it works no better. I think this might have been the issue in the first place? I know this is my fault for not updating regularly, but good lord, what a punishment for not upgrading! 

Is this a fixable problem or am I looking at the labor of a wipe and reinstall?

is there no file at /etc/apt/sources.list or does it exist but is empty?  The sources.list file contains the URL's of the servers from which new software is downloaded and installed.  This applies both to any piece of software you install and for updates. When the Update Manager, etc., display the sources in use, they read them from sources.list.

One of the images posted earlier in the thread indicates sources.list was intact at that time. A routine update, or anything else in the normal course of operations, will not delete sources.list.

How did you try "rebuilding it"?  

13.04 Raring is no longer supported.  No updates are available. The servers that an intact sources.list would contain no longer exist. That means that even if you restore a correct 13.04 sources.list, you will not be able to update.

At this point, my own recommendation would be to install the current 14.04 Long-Term-Support, which has 5 years of support.

---

### Post by salmichaels on 2014-07-31
What a nightmare. I tried to burn a DVD of 14.whatever and Brasero can't seem to do without an issue. I can't get a different burner b/c software center is gone, and I can't get synaptic. Never have expensive Mac or shoddy Windows ever left me in a pickle like this before. When Linux works, it works great. When it fails, it fails hard. It is clearly no good for the non-expert.

---

### Post by coffeecat on 2014-07-31
I am sorry you are having problems, but you need to focus on how to get out of this situation without the grumbling. Optimism and a positive attitude is needed! Which hopefully, I can offer.

A few questions:

1 - Do you have access to another computer with a DVD burner? It doesn't matter which operating system. If you have, details please, including details of the operating system.

2 - Does the machine on which you currently have a broken 13.04 system support booting from USB? And, if so, do you have a spare USB flash drive of at least 1GB capacity?

If the answer to 1 is no and the answer to both questions in 2 is yes, then there is a way to prepare a bootable flash drive from the ISO with a simple terminal command. However, this terminal command is potentially very destructive if you make a typo in it, and if I give it to you, you need to double-check everything before running it. If you wish to try this, we need the following information:

1 - the full filename of the 14.04 ISO. I can probably work this out, but I need to know whether you have the 32 or 64 bit version and whether the 14.04 or 14.04.1 point release.

2 - Plug the flash drive in, ignore any windows that pop up, and run this command:

```
sudo fdisk -l
```

Post the output. You can highlight the output with your mouse and then right-click -> copy to paste it into your post.

---

