---
title: "Why does Linux have so many issues with 3rd party progs?"
date: 2007-02-11
forum: General Help
---

### Post by boostedtsi on 2007-02-11
I swear, I went to it again to use it for two purposes only.
linuxcnc, and boinc.

I have no idea how it will do linuxcnc but it refuses to run boinc. Even though it is a linux distro of it.

Maybe it is just me, but if a program is advertised to work under a certain envrioment, maybe just maybe it should do it...

I eventually just shut the box down cause I was just getting too pissed at it.
If you all have any ideas I am all ears.
The issue is it will not connect to localhost.

Yes I do know how to run boinc, I do have over 87K in credits. But then again those other machines are running MS OS and they do as advertised.

I gave Ubuntu a try a few months back was totally unimpressed (although it has improved since my last try at linux) it still is not where it needs to be for a user even with more than a few years experience with computers.

---

### Post by meng on 2007-02-11
How did you install boinc? Did you read this from the BOINC download page?
"Note: BOINC may be available as a package for for your particular Linux distribution (Gentoo, Fedora, Debian, Ubuntu); check this first before downloading from this page."

which ought to have led you to search the package lists, and

sudo apt-get install boinc-client

and/or

sudo apt-get install boinc-app-seti

depending on what you were hoping to do with boinc, I suppose.

And as to the whining/bitching part of your thread :) there is some truth to what you say BUT the situation is more like English and Mandarin Chinese, you know "I've got years of experience in English but when I try and understand Chinese, it just makes no sense whatsoever ... Chinese is just not where it needs to be." What you don't appreciate is that Windows experience counts for nought when it comes to running Linux, in fact it can even be a handicap because no Windows user thinks about installing software from a CENTRAL REPOSITORY, that's an alien concept.

---

### Post by Maestro23 on 2007-02-11
Boinc is available in the repositories.

---

### Post by aysiu on 2007-02-11
Take it one step at a time here.

First, try to understand how programs are installed:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

And before you can *apt-get* install BOINC, you need extra repositories enabled:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

If you prefer to do everything the point-and-click way, this link may serve you better:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

There are instructions on [the LinuxCNC website for installing on Ubuntu](http://www.linuxcnc.org/index.php?option=com_content&task=view&id=21&Itemid=4&lang=en): > f you prefer to start with the distributed Ubuntu CD, which the Ubuntu team will ship to you free of charge (for instance if you cannot download the above CD image), you can install EMC2 yourself with these instructions:

    * Step 1: Install Ubuntu 5.10 Breezy Badger or 6.06 Dapper Drake LTS (a very easy to install & use Linux distribution),
    * Step 2: Once you have installed Ubuntu , get the install script from here: [breezy-install](http://www.linuxcnc.org/emc2-install.sh) or [dapper-install](http://www.linuxcnc.org/dapper/emc2-install.sh), choose "Save to Disk" and click OK.
    * Step 3: Now an emc2-install.sh icon will appear on your Desktop. Right-click that icon, select Properties. Go to the Permissions tab and check the box for Owner: Execute. Close the Properties window.
    * Step 4: Now double-click the emc2-install.sh icon, and select "Run in Terminal". A terminal will appear and you will be asked for your password.
    * Step 5: When the installation asks if you are sure you want to install the EMC2 packages, hit Enter to accept. Now just allow the install to finish.
    * Step 6: When it is done, you must reboot (System > Log Out > Restart the Computer) - once you have rebooted you can run EMC2 by selecting it on the Applications > CNC menu.
    * Step 7: If you aren't ready to set up a machine configuration, try the sim-AXIS configuration; it runs a "simulated machine" that requires no attached hardware.

    Now that the initial installation is done, Ubuntu will prompt you when updates of EMC2 or its supporting files are available. When they are, you can update them easily and automatically with the Update Manager. Steps #2-4 can also be done more quickly by pasting these commands in the terminal: ```
wget -c http://www.linuxcnc.org/dapper/emc2-install.sh
chmod +x emc2-install.sh
./emc2-install.sh
```

---

### Post by aysiu on 2007-02-11
> **meng said:**
> H
And as to the whining/bitching part of your thread :) there is some truth to what you say BUT the situation is more like English and Mandarin Chinese, you know "I've got years of experience in English but when I try and understand Chinese, it just makes no sense whatsoever ... Chinese is just not where it needs to be." What you don't appreciate is that Windows experience counts for nought when it comes to running Linux, in fact it can even be a handicap because no Windows user thinks about installing software from a CENTRAL REPOSITORY, that's an alien concept. More details here:
[The Chinese Language is not "Ready for the Desktop."](http://ubuntuforums.org/showthread.php?t=120489&highlight=chinese+ready+desktop)

---

### Post by meng on 2007-02-11
I wasn't claiming an original idea, but even I'm somewhat surprised to have that  cited "in my face" so quickly. :D

---

### Post by nickoli_02 on 2007-02-12
Haha, that's great Aysiu :)

---

### Post by boostedtsi on 2007-02-12
Yes when I went to CPDN I read it's suggestions as to DL'ing it from the add/remove programs list. 

I did exactly that.
It does not work, as it refuses to connect to localhost.

I am no novice when it comes to dealing with computers, but debugging and or figuring out why programs do not work when I have done everything stated, and it gives such a generic error I have issues with.

I will give linux props for being an outstanding server os, and built in server apps. 

But as to be used by an end user it still has quite way to go.

---

### Post by meng on 2007-02-12
Okay, I think you could still be asking for help here, so I tried installing BOINC myself. I went to Add/Remove and installed BOINC. Now this apparently installs BOINC Manager, and its dependencies, but it doesn't install a BOINC client (I guess you could use the manager to connect to a client on another computer ...) So, not knowing this, I tried running BOINC manager and I got the same error message you got - unable to connect to localhost, or more specifically, unable to connect to a BOINC client on the localhost.

So I installed boinc-client:
sudo apt-get install boinc-client
and tried connecting again (didn't even need to restart the BOINC manager). Bingo! Worked immediately.

Now I can't be sure that you are having the same problem, because you didn't provide a detailed account of what you did. But, from your description, it's at least conceivable that you made the same mistake I did, although it would mean that you had completely ignored the advice from my first post, but I guess that happens all the time (members ignoring my advice I mean). Anyway, I hope it may be as simple as that and you can get to BOINCing right away.

---

### Post by Maestro23 on 2007-02-12
> **meng said:**
> Okay, I think you could still be asking for help here, so I tried installing BOINC myself. I went to Add/Remove and installed BOINC. Now this apparently installs BOINC Manager, and its dependencies, but it doesn't install a BOINC client (I guess you could use the manager to connect to a client on another computer ...) So, not knowing this, I tried running BOINC manager and I got the same error message you got - unable to connect to localhost, or more specifically, unable to connect to a BOINC client on the localhost.

So I installed boinc-client:
sudo apt-get install boinc-client
and tried connecting again (didn't even need to restart the BOINC manager). Bingo! Worked immediately.

Now I can't be sure that you are having the same problem, because you didn't provide a detailed account of what you did. But, from your description, it's at least conceivable that you made the same mistake I did, although it would mean that you had completely ignored the advice from my first post, but I guess that happens all the time (members ignoring my advice I mean). Anyway, I hope it may be as simple as that and you can get to BOINCing right away.

Man meng, great minds think alike.:) 

I did the same thing except via synaptic where I could see all the programs associated w/BOINC and get a description of what they did.  Had no probs either.  Just wanted to see if or what the issues were.

---

### Post by meng on 2007-02-12
> **Maestro23 said:**
> Man meng, great minds think alike.:) 
I did the same thing except via synaptic where I could see all the programs associated w/BOINC and get a description of what they did.  Had no probs either.  Just wanted to see if or what the issues were.
Well I was trying to emulate what the OP did to see if I could replicate the problem. I've never been a fan of Add/Remove, although I've heard it's much better these days (looks it too, from my single use).

---

### Post by Talon2 on 2007-02-13
> **Maestro23 said:**
> Boinc is available in the repositories.

Unfortunately the version available in the repositories is an old version (v5.4) which allows little control over cpu useage which can and does lead to heat issues in many machines.

What we need is whoever maintains BOINC in the repositories to package up v5.8 so we can install it.

---

### Post by meng on 2007-02-13
> **Talon2 said:**
> Unfortunately the version available in the repositories is an old version (v5.4) which allows little control over cpu useage which can and does lead to heat issues in many machines. What we need is whoever maintains BOINC in the repositories to package up v5.8 so we can install it.
Good point, however, I'm still interested in addressing the OP's original complaint, which is that the program doesn't work at all, not that it has CPU usage problems.

---

### Post by meng on 2007-02-14
Guess I misjudged, the OP wasn't interested in following up on this.

---

### Post by OrangeCrate on 2007-02-15
> **aysiu said:**
> 
If you prefer to do everything the point-and-click way, this link may serve you better:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)


Aysiu (or anyone else),

I followed the instructions for enabling additional repositories in the above listed tutorial, and received the following errors. Could you translate this for me, as to what I did wrong, and how I might correct it? Or should I ignore it, as it just appears to be a listing of duplicate sources?

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)

Thanks.

---

### Post by meng on 2007-02-15
Yup, looks like you enabled the extra repositories TWICE, hence the duplicate sources message (as you noticed). Post your sources.list here, from terminal:

cat /etc/apt/sources.list

and post the output in this thread.

---

### Post by OrangeCrate on 2007-02-15
^, Output as follows:

cat /etc/apt/sources.list

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

---

### Post by OrangeCrate on 2007-02-15
^^, I've attempted to find a default listing for repositories in Dapper, and their original settings to see where I was prior to making the changes. Do you know if one exists, and where I can find it, to double check the entries, and return them to default?

---

### Post by meng on 2007-02-15
Are you sure that's the whole file? Because I can't see that you have multiverse enabled in those lines, but the error message says there's a duplicate multiverse.

---

### Post by OrangeCrate on 2007-02-15
^, Yes, this is the whole file.

cat /etc/apt/sources.list


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

---

### Post by OrangeCrate on 2007-02-15
> **meng said:**
> Are you sure that's the whole file? Because I can't see that you have multiverse enabled in those lines, but the error message says there's a duplicate multiverse.

Sorry, I just remembered... After posting, I went back into the Synaptic Package Manager, and edited out what I remembered changing from the original tutorial that asiyu posted. (This prompted my post right before your response on trying to reset the defaults.)

---

### Post by OrangeCrate on 2007-02-15
I found a partial list to check defaults, and right from the start, it appears that I have lost the first entry:

"Ubuntu 6.06 (Source)
Officially supported.
Restricted copyright."

My current first entry is:

Ubuntu 6.06 LTS Updates (Binary)

which is #2 on the partial list of defaults I found.

Frankly, I'm simply not sure how I deleted that first item, unless I accidently hit "remove" instead of "edit". Is there a way to add it back manually, or can I just reinstall Synaptic to get back to the defaults?

Edit:

I see now, that I most likely caused the problem of duplicates because I had the "unsupported" and "commercial" repositiories already checked on the add/remove page. If I can reset synaptic to it's defaults, I think I can back myself out of this problem.

I see from a forum search, the following instruction to install (reinstall?) synaptic:

sudo apt-get install synaptic

But, being fairly new to Ubuntu, I am reluctant to go any further until I have advice on what to do next...

---

### Post by OrangeCrate on 2007-02-15
Bump

---

