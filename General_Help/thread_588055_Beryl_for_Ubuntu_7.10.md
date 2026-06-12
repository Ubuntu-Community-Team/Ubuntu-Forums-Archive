---
title: "Beryl for Ubuntu 7.10?"
date: 2007-10-23
forum: General Help
---

### Post by .Oxy on 2007-10-23
Okay, so i recently upgraded my Ubuntu machine from 7.04 to 7.10. I had beryl fully working on 7.04, but now I can't seem to find it anywhere on my machine.
Is beryl not compatible with 7.10?
Thanks.
[size=1]Yes, I'm a newbie. =p[/size]

---

### Post by scorp123 on 2007-10-23
Beryl was replaced with Compiz-Fusion. The "Beryl" project has been discontinued and all the developers have re-joined the Compiz project (from which they originally had broken away) as far as I know.

---

### Post by UK-Wobbie on 2007-10-23
> **.Oxy said:**
> Okay, so i recently upgraded my Ubuntu machine from 7.04 to 7.10. I had beryl fully working on 7.04, but now I can't seem to find it anywhere on my machine.
Is beryl not compatible with 7.10?
Thanks.
[size=1]Yes, I'm a newbie. =p[/size]

Beryl do work on 7.10.. But i do not like it any more :lolflag: I use "Advanced Desktop Effects Settings"... All Beryl was doing is not working with TV out cards :(

Go in to your "Synaptic Package Manager" And put this in the search box!
"compizconfig-settings-manage"

Then when it's all done instilling logout and hit "Ctrl-Alt-Delete key" To restart the X sever.. Log back in and your done :)

---

### Post by notwen on 2007-10-23
The Beryl and Compiz projects have merged to make up the Compiz-Fusion project.  Compiz-Fusion is installed by default in Gutsy.  If you're wanting a config window similar to Beryl's follow UK-WObbie's instructions to install Compiz-Fusion's settings manager but, you'll need to press '**ALT+CTRL+BACKSPACE**' to restart your x-server. =]

---

### Post by UK-Wobbie on 2007-10-23
> **UK-Wobbie said:**
> Beryl do work on 7.10.. But i do not like it any more :lolflag: I use "Advanced Desktop Effects Settings"... All Beryl was doing is not working with TV out cards :(

Go in to your "Synaptic Package Manager" And put this in the search box!
"compizconfig-settings-manage"

Then when it's all done instilling logout and hit "Ctrl-Alt-Delete key" To restart the X sever.. Log back in and your done :)

It as more Effects then Beryl. :guitar:

---

### Post by .Oxy on 2007-10-23
> **UK-Wobbie said:**
> Beryl do work on 7.10.. But i do not like it any more :lolflag: I use "Advanced Desktop Effects Settings"... All Beryl was doing is not working with TV out cards :(

Go in to your "Synaptic Package Manager" And put this in the search box!
"compizconfig-settings-manage"

Then when it's all done instilling logout and hit "Ctrl-Alt-Delete key" To restart the X sever.. Log back in and your done :)

I've done all that, and unless i've missed something/being stupid, i still can't see a difference in anything... :S

---

### Post by UK-Wobbie on 2007-10-23
> **.Oxy said:**
> I've done all that, and unless i've missed something/being stupid, i still can't see a difference in anything... :S

Go to "Settings" And then go to "Advanced Desktop Effects Settings"
Click on something! :lolflag:

---

### Post by .Oxy on 2007-10-23
Ahh, i got it now, thanks alot. :)

---

### Post by UK-Wobbie on 2007-10-23
It's ok anytime :mrgreen:

---

### Post by tomeg on 2008-03-08
> **UK-Wobbie said:**
> Beryl do work on 7.10.. But i do not like it any more :lolflag: I use "Advanced Desktop Effects Settings"... All Beryl was doing is not working with TV out cards :(

Go in to your "Synaptic Package Manager" And put this in the search box!
"compizconfig-settings-manage"

Then when it's all done instilling logout and hit "Ctrl-Alt-Delete key" To restart the X sever.. Log back in and your done :)

I just looked at my Synaptic Package Manager and there is no "compizconfig-settings-manage". Any suggestions. I did a standard install.

---

### Post by PurposeOfReason on 2008-03-08
> **tomeg said:**
> I just looked at my Synaptic Package Manager and there is no "compizconfig-settings-manage". Any suggestions. I did a standard install.
What is the output of:

cat /etc/apt/sources.list

---

### Post by itch808 on 2008-03-29
I have the exact same problem, there is no "compiz-config-manage", i typed in what you wrote and got this:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by PurposeOfReason on 2008-03-30
When you installed, you did not have a working connection that Ubuntu found and all of your sources are commented (#) out. Any line that starts with deb or deb-src, remove the # in front of it to make it active. Then run```
sudo apt-get update 
sudo apt-get upgrade
```

To update the list and upgrade. After that you can install.

---

