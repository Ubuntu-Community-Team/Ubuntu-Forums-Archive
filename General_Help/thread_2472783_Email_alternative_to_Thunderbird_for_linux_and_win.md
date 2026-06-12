---
title: "Email alternative to Thunderbird for linux and windows"
date: 2022-03-12
forum: General Help
---

### Post by makem2 on 2022-03-12
I have used thunderbird in both systems for many years by having one data file accessible in both systems. Lately I have been getting errors like, "You are using and old version  and need to make a new profile". I had the same error in Firefox. I have tried in both programs to use the one data file but cannot get it to work.

I would like to try an alternative to Thunderbird. I am using Windows 10 and xubuntu 21.10 xfce desktop.

Can anyone suggest an alternative usable from one data file across the two operating systems?

---

### Post by DuckHook on 2022-03-12
A toughy.

I know of no alternative, but then, I wasn't aware that T-bird had the versatility in the first place to do what you've just described (I don't use Windows). That's actually kinda cool.

Perhaps there's a way to salvage T-bird rather than go to something else.

Please post the version of T-bird you are using in both Windows and Ubuntu. Also, post your version of Ubuntu.

What I'm thinking/considering is to go to the latest T-bird instead of the one bundled in Ubuntu. Your problem may be that, for stability reasons, the Ubuntu devs rarely upgrade TB after the distro is finalized. Unlike Firefox, TB is frozen in place once a distro leaves beta. There was one upgrade a few weeks ago, but this was to patch a must-fix security hole and was the exception, not the rule.

I suspect your problem arises because MS, being a proprietary ecosystem, leaves it to the app to keep itself updated. This means that TB on Windows is the latest whereas TB on Ubuntu is frozen at an earlier version. The resulting desync creates an incompatibility when the underlying database file is silently modified by the newer app in order to support some new feature (I wish they wouldn't do that without warning and an option to leave the database alone, but that's "progress" for you).

However, by adding the PPA from the Mozilla Team, you can keep TB at the latest and most current release. *Caution* Doing so will henceforth automatically drag your data files along and keep them at the latest version. This means that you might get breakage the opposite way, where your Windows version is not keeping up with your Ubuntu one. You need to appreciate that your whole setup is brittle and fragile—mixing and matching between two different OSes, file structures, etc. You've been lucky so far to get away with it, but TB was never designed to work that way, and any other mail client is unlikely to either.

Before using the following instructions, post those versions for us to review. There's no point risking your email database for the sake of some fancy extra-design functionality without doing your checks and due diligence first. Even then, back up your whole e-mail database before monkeying around with it.

Instructions:

[LIST=1]
[*]First, add the Mozilla Team PPA:```
sudo add-apt-repository ppa:mozillateam/ppa
```
[*]Then:```
sudo apt update
```
[*]Then:```
sudo apt upgrade
```
[*]Unlikely to be needed, but if this doesn't give you the latest release, then```
sudo apt purge --autoremove thunderbird
sudo apt install thunderbird
```
[/LIST]
This should get you up to the latest release, or at least, as current as the Mozilla team keeps their PPA. They are usually pretty good about it, mainly because Mozilla has the resources to assign actual maintainers to their PPA.

A further word of caution: I see by your join date that you are an old hand at Ubuntu, but for any lurkers out there—adding PPAs willy nilly is not good security practice. You are entirely at the mercy of the PPA author and even if they mean well, they may not maintain the PPA with sufficient patches to close security holes. This is a special case and uses a PPA that is trustworthy (more or less), but the same cannot be said of other PPAs.

---

### Post by rsteinmetz70112 on 2022-03-14
I would suggest checking to see if you have the same version of Thunderbird on both machines.

---

### Post by ajgreeny on 2022-03-14
The T'Bird version on my Xubuntu-22.04 systems is 91.7.0 and they all work well, but on my 20.04 it is still 91.5 though I do not share the profile between them because I am aware that doing so can cause exactly the problem you seem to be asking about.

As an example, if I used the profile from my 91.7.0 version but open a T'Bird version below that such as the 78.14 that was updated around Jan 21 this year to 91.5 using this profile, an error will show saying it needs to create a new profile.
I am not sure if this can be overridden as I have never needed to, but others may know how. Nor am I sure if this is the case with just a point move, ie, from 91.5 to 91.7.

I have no idea what version Windows uses nor how application upgrades are dealt with in Windows.  Do all applications have to be upgraded by their own system unlike the repository system for Ubuntu which upgrades everything at once.

---

### Post by mastablasta on 2022-03-15
> **ajgreeny said:**
> 
I have no idea what version Windows uses nor how application upgrades are dealt with in Windows. 

updates are done in application. in case of TB, you choose the install type and then it is upgraded. so if you have stable branch on windows and in ubuntu go with PPA that uses latest stable you should have same version in both. on windows it is also not necessarily automatically updated, though this can be enabled in application.

as an alternative to that you could disable updates on windows version, but this could potentially create a security hole.


another option is to use web based email. it can be accessed from any OS and device.

---

### Post by ajgreeny on 2022-03-15
Thanks  mastablasta.  It's such a long time since I used and managed a Windows box (it was XP back in 2005) and have just about forgotten everything I knew then.

Windows is a mystery to me now in the same way that new Linux users sometimes say that Linux is a mystery to them!

---

### Post by dragonfly41 on 2022-03-15
Although I have Windows and Ubuntu in dual boot mode I stick with Ubuntu Thunderbird.
But considering your requirement my first thought was to have two Thunderbird sessions .. Windows and Ubuntu .. and then sync both sessions. Not a single shared file.

[https://superuser.com/questions/935122/merge-synchronize-two-thunderbird-installations](https://superuser.com/questions/935122/merge-synchronize-two-thunderbird-installations)

---

### Post by mastablasta on 2022-03-16
> **mastablasta said:**
> 
another option is to use web based email. it can be accessed from any OS and device.


additionally IMAP access to web based mail (e.g. to google) can be done from any version of TB or any other email client (e.g. outlook...). in case of IMAP your files are (by default) left on server. POP will download them localy. you can use imap and move files you need to local drive.

---

