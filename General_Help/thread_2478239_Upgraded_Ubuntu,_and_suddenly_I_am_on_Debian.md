---
title: "Upgraded Ubuntu, and suddenly I am on Debian?"
date: 2022-08-20
forum: General Help
---

### Post by ras00998 on 2022-08-20
Hello all, 

Bit strange this, a few days ago I upgraded my machine running I think Ubunto 20 to Ubuntu 22.04 lts. 
Everything was fine for a few days.
And then today, (while rushing out the door,  I hastily shut down, everything normal I thought. 
Now when I start up I am on Debian!, Never had this experience before, I do not recall choosing anything etc.. 
Is there somehow a way to easily go between Ubuntu and Debian? Something I might have clicked by mistake?

Thanks for any help on this, 
K

(PS, sorry for my ignorance, my knowledge of Linux is very limited, despite having been using it for years)

---

### Post by mikewhatever on 2022-08-20
Nope. Ubuntu has separate repositories, and none of Debian ones are used by default. Check the list of repositories you have at 
```

/etc/apt/sources.list

```

---

### Post by ras00998 on 2022-08-20
Thank you, strange I get - 

bash: /etc/apt/sources.list: Permission denied

---

### Post by #&amp;thj^% on 2022-08-20
What shows with:
```
cat /etc/apt/sources.list
```

---

### Post by ras00998 on 2022-08-20
Thank you, I get the below  (ps, I am in the UK, I bought a Spanish Slimbook a few years ago, hence the .es links) 

$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 16.04.4 LTS _Xenial Xerus_ - Release amd64 (20180228)]/ xenial main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jammy main restricted
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jammy-updates main restricted
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jammy universe
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jammy-updates universe
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jammy multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jammy-updates multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jammy-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse




deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
kepa@kepa-SLIMBOOK:~$

---

### Post by #&amp;thj^% on 2022-08-20
I sure don't see any pure Debian sources, listed there.
I have seen a reference to Debian on some of KVM installs though.
Looks to me your using Ubuntu

---

### Post by ras00998 on 2022-08-20
Appreciate you looking. 
So strange, everything changed in terms of layout after this one shutdown, and desktop background changed to an image with 'Debian' written on it.

---

### Post by grahammechanical on 2022-08-20
The strange thing I see about the repository addresses in your sources.list file is that there are two different addresses. The addresses for the installed software are for jammy (22.04). But the addresses for the source code of the software are for xenial (16.04). All addresses should be for jammy (22.04).

Was this an original install of 16.04 LTS? And have you upgraded to 18.04 LTS and then to 20.04 LTS? Please describe the upgrade method. Doing several online upgrades through several LTS releases can result in a messed up user interface. This is especially true if one of those versions has reached end of life. Which 16.04 has. Did you get Extended Security support for 16.04? There are big differences between the user interface of 16.04 and 22.04. 

What are the clues that cause you to think you are now on Debian?

Regards

---

### Post by mikewhatever on 2022-08-20
So, the upgrade was from 16.04 to 20.04. There aren't any Debian repositories in the soulces.list, but you can aslo check in another place: 
```
grep -ri debian /etc/apt/sources.list.d/*
lsb_release -a

```

---

### Post by ras00998 on 2022-08-20
Thank you, sorry I cannot really express it - I was prompted to upgrade, just once I believe - from 16 to the 20.04 I believe. 
I just assumed Debian because navigation all moved to bottom of screen instead of left hand side - and desktop wallpaper changed to a pattern with Debian written on it (which I have since deleted by replacing  with a black image, all I can comfortably work with), So I cannot check if anything else was written. 

If there are two different addresses like you say, is this a security concern?  That would be my biggest concern at the moment.

EDIT: 
Could the two addresses be related to the Spanish / English thing. There was some issues, when I first got the computer, now resolved. 
And now, when the shutdown caused this current confusion, language changed to Spanish, first thing I did was change to English in settings..

---

### Post by ras00998 on 2022-08-20
Thank you, 
I get this, 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.1 LTS
Release:	22.04
Codename:	jammy

---

### Post by QIII on 2022-08-20
Do you have room mates?  House mates?  Friends with keys?  Someone whom you allowed to use your machine?  Unsecure wifi?

While file corruption does occur and that can wreak havoc, something like what you describe is not an iron oxide particle on a disk platter knocked silly by a cosmic ray.

It sounds to me like an image file was saved to the disk, a config file was changed and your Desktop Environment (DE) was changed.

---

### Post by ras00998 on 2022-08-20
Thanks!
Nobody else was involved, only my hand touched the machine. And wifi is secure I believe. 

You suspect foul play?, because I do not think iron oxide particles have ill intentions.

Edit : 
> [COLOR=#000000]"It sounds to me like an image file was saved to the disk, a config file was changed and your Desktop Environment (DE) was changed."[/COLOR][COLOR=#000000]
Sounds intense! - Is this a complicated thing to fix do you know?

Edit a day later : On second thoughts, I realise it is not very clear what needs fixed..  I guess I want things to go back to the way they where.  This is not possible - things change and you accept it. 

[/COLOR]

---

### Post by Impavidus on 2022-08-21
The xenial sources in your sources.list are nothing to worry about. During a release upgrade, disabled repositories aren't upgraded. You have to do that manually before enabling them later, if you ever enable them. Maybe it would be better if it did work automatically. Maybe not.

It could still be accidental file corruption. If your desktop manager cannot read your config files, it falls back to some defaults. With Ubuntu being based on Debian, some of the defaults (normally overridden when the installer creates users with some other default configuration) may still contain Debian branding. And Spanish may still be the system-wide default language, even when your user has been set to English.

Accidental file corruption shouldn't happen. Any chance you switched the computer off before shutdown was complete during your hasty shutdown when you rushed out of the door? Or it could be a bad harddrive.

---

### Post by ras00998 on 2022-08-21
Thanks! Good to know you do not think there is a security concern. 

Pretty sure I shut down properly, So not sure what triggered this. The upgrade was working fine for 2 full days I think, and several shutdowns. 

I am backing up everything, and I guess I can live with the new desktop layout - Just slightly alarming to see everything change like that. 
I do not think I have the skills to try any change multiple things.

---

### Post by guiverc on 2022-08-21
First, be aware Ubuntu products using the *year* format are different to the far more widely used *year.month* systems, and you cannot upgrade a Ubuntu Core 16 system so it turns into a 20.04 system as they are different products. Ubuntu Core 16 will upgrade to 18, then to 20, then to 22 (*these upgrades cause no user-app changes though which differs greatly to the 16.04 -> 18.04 & later type upgrades*). The *year* format systems (16, 18, 20, 22) are *snap* package only and don't use *deb* package applications, only the *year.month* systems use *deb *packages (but can also use *snap* packages too).   You likely meant 16.04 though (where 16 & 16.04 are different systems).

Many Ubuntu packages come from upstream Debian, and include no changes, thus Debian branding, wallpapers etc. remain.  I'll use as example LXDE.  On releases of Lubuntu up to 18.04, LXDE was used thus it was managed by the Lubuntu team (*on behalf of  Ubuntu*) with changes made to fit their usage, however from 18.10 & onwards Lubuntu used only LXQt, thus the LXDE packages that exist now in Ubuntu are from upstream Debian, with no changes by anyone in Ubuntu, and thus any branding  will say Debian.

Debian branding in Ubuntu is to be expected if it's just in Ubuntu repositories because the package which contained it entered Ubuntu from upstream Debian. It's not generally expected when it's a Ubuntu team that manages it, though it still can occur; but it won't be seen by default with it being left in as it's less work keeping the package with fewer changes possible.

There are numerous packages in Ubuntu repositories that still have Debian logos, wallpapers, backgrounds etc; and they are of no consequence.  If I ever see one, I work out where the file is that contains it, so I can work out the package where it came from & look for why it's there that way. I don't understand where you saw it, so can't explore currently.  

 (*it occurred to me I could have a quick look at how many such files exist on my normally used kinetic (Ubuntu development) system, alas I'm currently using bookworm (Debian) I realized so my answer wouldn't be helpful... this Debian box will have fewer Ubuntu references (but they'll be there!) than Ubuntu contains of Debian due to upstream/downstream location... though this Debian system has a far older LXQt than my Ubuntu does.. as the later LXQt being uploaded to sid is the version Ubuntu already has, with Lubuntu/Ubuntu members uploading it to Debian*... *We aren't uploading any Lubuntu wallpapers though; references will just be packaging details*)

---

### Post by ras00998 on 2022-08-21
Thank you for all the information!
I had a computer on Debian some years ago, but switched to Ubuntu when I got a new computer as it came installed already. 

The Debian branding I saw was the desktop background image which replaced my old image when all the changes occurred, just the text 'Debian' and some kind of pattern. 
The first thing I did was save a black jpg as the background, as I hate a cluttered background.. 
I guess I was silly to assume I was on Debian just because the Desktop background suggested so. 

Can I ask, do you think, things are working ok for me now - but I am going to have issues when things start upgrading? When I was on Ubuntu 16.? before the upgrade to 20.04, I was getting suggested upgrades to install every few days..

---

### Post by mikewhatever on 2022-08-21
You don't have to "start upgrading" whatever that means. 20.04 is supported untill 2025, so there is time.
Based on what we've seen so far, there is no reason to assume there going to be "issues",  unless you know something specific that we do not.
It is easy to disable upgrade prompts, just have to remomber to upgrade manually before the release goes EoL.

---

### Post by ras00998 on 2022-08-22
Thank you - 
Sorry my parlance is so off, by 'upgrading' I meant, when I was on 16. there was regular software updates I was prompted to download. 
(like in the image I attach from a web search) 
I have not seen this since changng to 20.04 - Perhaps I have to manually check for software updates now?
[IMG]https://149366088.v2.pressablecdn.com/wp-content/uploads/2013/04/software-updater.jpg[/IMG]

---

### Post by Impavidus on 2022-08-22
Look at your update settings. You can choose when it should check for updates (never, every two weeks, ..., daily) and what to do (install automatically or prompt). Pick the settings you like. It may take a while before any updates are available.

You mentioned an upgrade from 16.04 to 20.04. 16.04 reached end of life over a year ago and offered an upgrade to 18.04, which in turn can be upgraded to 20.04, which can be upgraded to 22.04. Skipping 18.04 isn't possible with the normal upgrade tool. You can force it, but that's likely to result in unpleasant side effects.

---

### Post by ras00998 on 2022-08-22
Thank you. 
I am looking at the update settings - much appreciated. 

I see, interesting to hear about the skipping of 18.04 being a potential issue, the plot thickens. 
So much to consider so far.

---

### Post by TheFu on 2022-08-22
> **ras00998 said:**
>  Just slightly alarming to see everything change like that. 
I do not think I have the skills to try any change multiple things.

If you moved from 16.04 to 20.xx or later, so many things have changed in the default Ubuntu DE.  For example, 16.04 used "Unity." 20.04 and later use "Gnome3".  Progress?  Perhaps, but it is a matter of opinion.  There are lots of different DEs and GUIs available.  Don't feel stuck using Gnome, if it isn't what you want.

No wifi network should ever be considered "secure".  There are always problems being discovered. Some have been around since 2000 - in al wifi networks.  If you want security over wifi, always use a strong IPSec VPN.  Most people will trade convenience for security. They don't think they are a target or at risk. Just depends on your risk acceptance level. I don't live in a city, but I do live in an area with hundreds of other people within a mile or so. For me, the risk of using wifi without a full VPN is too great to be trusted.  If I lived in an apartment or densely populated city, forgetaboutit.  Everything would be wired.

I think if you ask the long-time experts around here, most people would upgrade once from an LTS to the next one, but then do a fresh install on the 3rd LTS.  1 major upgrade from LTS to LTS only.  Sometimes the old files leave cruft behind that leaves the system is odd states.  It isn't just the DE that changed since 16.04.  Lots of things under the covers have changed in that time.

---

### Post by ras00998 on 2022-08-22
Thank you. 
I did expect changes after the move, the thing is the changes happened 2 or 3 days after the move. After a shutdown where I guess something was clicked - 

Thank you for all your thoughts, very insightful, I do need to get on a VPN.. been meaning to for years.. We are pretty rural but would like to do this.. Using Protonmail so might dive into the proton VPN. 

People are so helpful on here!, posted twice now and got bags of help each time. :) 
Thank you everyone,

---

