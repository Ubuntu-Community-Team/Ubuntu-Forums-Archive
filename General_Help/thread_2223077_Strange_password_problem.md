---
title: "Strange password problem"
date: 2014-05-09
forum: General Help
---

### Post by timswait on 2014-05-09
A few years ago I set up a Mythbuntu system for my parents (big mistake - I'm now on an indefinite technical support contract!!). It was set up on 10.04, but recently it's just generally not been working properly and became very unstable. I've been trying to talk them through how to upgrade, planning to upgrade to 12.04 and then to 14.04. They have upgraded to 12.04 but have now hit a big problem. They can't open update manager. Synaptic comes up with the following message when they run it:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
```

They have tried running the command in terminal and the following happens:
```
rosebank@rosebank-living-room:~$sudo dpkg --configure -a
Sorry, try again
Sorry, try again
Sorry try again
sudo: 3 incorrect password attempts
rosebank@rosebank-living-room:~$
```
The thing is *they're not even getting a chance to enter a password!*. They type the command, press enter, and it immediately says the password has been entered incorrectly 3 times without giving them a chance to enter it. I don't understand what's going on. This happens every time they enter a sudo command. So without being able to do sudo anything they don't have much chance to sort it out.

---

### Post by grahammechanical on 2014-05-09
Are they holding down the Enter key causing it to record multiple presses? These kind of questions have to be asked. What "Press Enter" means to us might mean something else to someone else.

Regards.

---

### Post by timswait on 2014-05-10
It was also my thoughts that they were doing something strange like holding down the Enter key, but I have been through it very carefully with them step by step and it really does seem that the problem is as described, the computer is acting as though something has been typed when it's not. I also thought it might be something up with the wireless keyboard they use, but I got them to try a wired keyboard from another computer on it and exactly the same thing happens. There don't appear to be any spurious key presses being recorded in any other situation, so I think it is genuinely happening as described above.
They actually got part way through updating from 12.04 to 14.04, but it crashed and had to be restarted. It was still in the fetching stage that this happened so I didn't think any changes had been applied, but apparently the computer does display 14.04 in the splash screen when it boots up, so I think it's in some kind of half-updated state. But without being able to use any sudo commands there's not much I can recommend them to do :(

---

### Post by bapoumba on 2014-05-10
[http://ubuntuforums.org/showthread.php?t=1401055&page=4](http://ubuntuforums.org/showthread.php?t=1401055&page=4)
Maybe something like this ?
Disk full + unfinished upgrades.

Anything in /var/log/auth.log related to sudo:session errors ?

If their disk is not full, the best would be to boot in recovery mode and finish up the upgrade.

Edit : here is what I have in /etc/pam.d/sudo
```
#%PAM-1.0

auth       required   pam_env.so readenv=1 user_readenv=0
auth       required   pam_env.so readenv=1 envfile=/etc/default/locale user_readenv=0
@include common-auth
@include common-account
@include common-session-noninteractive
```

---

### Post by timswait on 2014-05-28
I think it is related to the unfinished upgrade, I don't think the disk was full, I think it was them that interupted the upgrade and that's messed it up. They have run the "Fix broken packages" option in recovery mode. Apparently, a lot scrolled up on the screen, so it seems to have done something, but the sudo command is still not working. I therefore told them to go into recovery mode and select the "Drop to root shell prompt" option and try to upgrade from there, however typing "apt-get update" returns ```
apt-get:undefined symbol: _ZN11CommandLine10GetCommandEPKNS_8DispatchEjPKPKc
``` What does this mean?

---

### Post by steeldriver on 2014-05-28
Unbelievably there's a single google hit on that error string --> [http://irclogs.ubuntu.com/2014/04/23/#ubuntu-de.txt](http://irclogs.ubuntu.com/2014/04/23/#ubuntu-de.txt)

Based on the google-translated text it sounds like it was fixed by

```

dpkg -configure -a

```

From man dpkg
```

       --configure package...|-a|--pending
              Configure a package which has been unpacked but not yet  config&#8208;
              ured.   [B]If  -a  or  --pending  is  given instead of package, all
              unpacked but unconfigured packages are configured.[/B]

              To reconfigure a package which has already been configured,  try
              the dpkg-reconfigure(8) command instead.

              Configuring consists of the following steps:

              1.  Unpack  the  conffiles, and at the same time back up the old
              conffiles, so that they can be restored if something goes wrong.

              2. Run postinst script, if provided by the package.

```

which jives with your diagnosis that it was an interrupted upgrade that caused the issue. Good luck and let us know how it goes.

---

### Post by bapoumba on 2014-05-28
lol steeldriver, I was on the same page :)
Please have them run the command steeldriver gave you from recovery mode (in case sudo is still not working).

---

### Post by timswait on 2014-05-28
Thank you! Actually I had seen that Google hit and hadn't been able to work out what it was about, seemed to be mainly people chatting about BMWs and Mercedes! I remember a few years ago there was a competition to make a name for a phrase that came back with one and only one result. Googlewhackbit was the winner I think. Such phrases must be very rare nowdays. I guess this particular string will now start returning two results as soon as Google gets round to indexing this thread, so there's now one fewer Googlewhackbit in the world!
"dpkg -configure -a" was a command they had been trying to run through sudo in terminal (but with sudo not working then it was unsuccesful), I hadn't thought of telling them to run it recovery mode. I'll tell them to try that and let you know how they get on.

---

### Post by timswait on 2014-06-06
I've come home to visit my parents for the wekend so I'll try and fix it while I'm here. I can confirm it's as they reported, the sudo command doesn't work, it just immediately flashes up that an incorrect password has been entered 3 times when it's not. Booting into recovery mode I can type "dpkg --configure -a" and a list of packages scrolls off the top of the screen, at the end of which it quits saying "There are too many errors". Running the "Repair broken packages" command in the recovery console does the same thing (I wonder if it's actually running the same command).
This doesn't sound good to me! I'm tempted to scrub it and do a complete re-install, but does anyone have any better ideas for how to fix it?

---

### Post by bapoumba on 2014-06-07
One way to do it would be :
1- check the sources.list sources and third party repositories :
```
cat -n /etc/apt/sources.list
ls /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
``` (thanks to Bashing-om for the last one :))
Sources should all be for 12.04 (no mixing with 10.04) and third party repos/ppa disabled. Do not proceed until you are sure all sources are clean.

2- run from recovery mode [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) :
```
apt-get update
apt-get dist-upgrade
```
(no sudo from recovery mode, this is a root shell).
It may need several cycles, run the commands one after another in that order until there is not error, hopefully.

Best of luck :)

---

### Post by timswait on 2014-06-08
I had given up on recovering the system, so created a live disk to do a fresh install with. However when I booted to this and clicked the install option it detected that I already had Ubuntu installed and gave me the option to re-install this keeping all documents and settings. I chose this and it worked! However since then I've been running into terrible difficulties with the satellite tuner card, I think firmware connected. The upshot of that was that I've ended up wiping and fresh installing anyway as I think there may be some settings left from the old system that were interferring and I just wanted to start from a blank slate to battle the firmware on.
Still if it helps anyone else then one option to recover an un-recoverable system (for example on that's been broken by interupting an upgrade) is to create a live disk (with another computer), boot to that, select the "Install" option and then see if it detects your existing set up and gives the option of re-installing it.

---

### Post by bapoumba on 2014-06-08
Hey, that is one way of doing it, glad you found a way. Hope you'll have a smooth sailing once the firmware issues are solved if not already :)

---

