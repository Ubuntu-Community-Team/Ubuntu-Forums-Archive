---
title: "Opinions Please"
date: 2007-01-22
forum: General Help
---

### Post by tacm on 2007-01-22
This is a generalized question.  I am brand new to Ubuntu and Linux,  It has been a lot of work leaving windows.  I must unlearn and relearn EVERYTHING. I have gotten some great help here and for that Thanx to each and every one who has helped me.  It seems every time I want to do something with my machine I need this plug in or that modification to make it work.  My question is this.  Is it possible to get Ubuntu configured properly to do everything my windows OS did?  examples mp3, DVD playback, Flash, Java  I'm running an AMD64 AND I have the POS 4318 wireless card (That thanx to the forum I just got working after a week)  As much as I dis like Microsoft, I am wondering will I ever be able to get this machine to do all it could before I got rid of windows?

---

### Post by kingmonkey on 2007-01-22
yes, try automatix

---

### Post by Hossie on 2007-01-22
> **tacm said:**
> I must unlearn [...] EVERYTHING.

Yeah, forget everything you have learnt in the evil world. :)

---

### Post by ardchoille42 on 2007-01-22
> **tacm said:**
> This is a generalized question.  I am brand new to Ubuntu and Linux,  It has been a lot of work leaving windows.  I must unlearn and relearn EVERYTHING. I have gotten some great help here and for that Thanx to each and every one who has helped me.  It seems every time I want to do something with my machine I need this plug in or that modification to make it work.  My question is this.  Is it possible to get Ubuntu configured properly to do everything my windows OS did?  examples mp3, DVD playback, Flash, Java  I'm running an AMD64 AND I have the POS 4318 wireless card (That thanx to the forum I just got working after a week)  As much as I dis like Microsoft, I am wondering will I ever be able to get this machine to do all it could before I got rid of windows?

One of the reasons Windows is so bloated is that it installs tons of junk you may never use. Linux keeps things lean so that it doesn't take up tons of space (LiveCD anyone?).. but this requires the user to install things later.

That said, you can find a lot of information [here]("https://help.ubuntu.com/community/RestrictedFormats"), [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/common-tasks-chap.html"), and [here]("https://help.ubuntu.com/community/FreeFormats").

---

### Post by Hossie on 2007-01-22
> **ardchoille42 said:**
> One of the reasons Windows is so bloated is that it installs tons of junk you may never use. Linux keeps things lean so that it doesn't take up tons of space (LiveCD anyone?).. but this requires the user to install things later.

That said, you can find a lot of information [here]("https://help.ubuntu.com/community/RestrictedFormats"), [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/common-tasks-chap.html"), and [here]("https://help.ubuntu.com/community/FreeFormats").

I think a fresh windows installation is naked, and a fresh Ubuntu Installation has tons of programs you never use. :rolleyes:

---

### Post by david_2001 on 2007-01-22
> **tacm said:**
> ...Is it possible to get Ubuntu configured properly to do everything my windows OS did?  examples mp3, DVD playback, Flash, Java

Those four are an absolute doddle to set-up nowadays, though maybe you want to consider using ogg rather than mp3 :wink:.  As I'm sitting here I'm able to do all that plus rip CDs to ogg format to play on my aging Xclef HD-800 JukeBox; watch and record digital tv, fix (with ProjectX, a Java application) and edit the recordings (frame accurate too), and burn them to DVD; use my Microsoft MCE remote control to change channels etc.; scan with an Epson Perfection 3170 (not Linux friendly); plus all the boring stuff like browsing (including YouTube with no problem at all), reading emails, writing letters...

---

### Post by tacm on 2007-01-22
> **david_2001 said:**
> Those four are an absolute doddle to set-up nowadays, though maybe you want to consider using ogg rather than mp3 :wink:.  As I'm sitting here I'm able to do all that plus rip CDs to ogg format to play on my aging Xclef HD-800 JukeBox; watch and record digital tv, fix (with ProjectX, a Java application) and edit the recordings (frame accurate too), and burn them to DVD; use my Microsoft MCE remote control to change channels etc.; scan with an Epson Perfection 3170 (not Linux friendly); plus all the boring stuff like browsing (including YouTube with no problem at all), reading emails, writing letters...
Youtube is a problem.....I guess ill have to keep working on it

---

### Post by david_2001 on 2007-01-22
> **tacm said:**
> Youtube is a problem.....I guess ill have to keep working on it

I guess that you mean a Flash Player problem.  If it helps, I used the flashplugin-nonfree package available from Seveas' Repository ([http://seveas.imbrandon.com/)](http://seveas.imbrandon.com/)) (uninstall any previous attempts first).  For edgy you need to add the following to your /etc/apt/sources.list:
```
deb http://seveas.imbrandon.com edgy-seveas all

```
and set the authentication gpg key with:```

wget http://seveas.imbrandon.com/1135D466.gpg -O- | sudo apt-key add -
```
Substitute dapper for edgy if you're using 6.06.

---

### Post by gh0st on 2007-01-22
I reckon you can do pretty much anything you can do on a Windows machine with a Linux machine nowadays. It was a lot of hassle a few years ago but with Ubuntu and Automatix it's a breeze now.

The first thing I do with a new Ubuntu install is run Automatix to get all my media players, codecs, Java and Flash setup. It's so easy, I love it. Have a look at [www.getautomatix.com](www.getautomatix.com) it really helped me out when I was new to Ubuntu.

The only area I would say Linux suffers slightly in comparison to Windows is with gaming. You can get a lot of Windows games to work now with Wine and Cedega, it's getting better but it's not quite there yet. This doesn't bother me cos I use consoles for gaming and with the new generation of consoles emerging now a Linux PC and a good console is all I need to keep me happy.

I'll admit there was a time when I flitted between Windows and Linux but since finding Ubuntu I'm perfectly happy. These days a dual-boot machine to me means a machine that runs Ubuntu and Fedora :D

---

### Post by tacm on 2007-01-22
> **gh0st said:**
>  These days a dual-boot machine to me means a machine that runs Ubuntu and Fedora :D
:D :D :D :D  I hope I can get to that place

---

### Post by Daveski on 2007-01-22
> **tacm said:**
> My question is this.  Is it possible to get Ubuntu configured properly to do everything my windows OS did?  examples mp3, DVD playback, Flash, Java  I'm running an AMD64 AND I have the POS 4318 wireless card (That thanx to the forum I just got working after a week)  As much as I dis like Microsoft, I am wondering will I ever be able to get this machine to do all it could before I got rid of windows?

Ubuntu only supplies fully free (as in speech) components, so anything which requires proprietory or non-open formats will need to be added. Ubuntu is free so you are within your rights to distribute it as you please.

MP3 is subject to patents, as is DVD decoding/decrypting, and of course so are many of those other audio and video codecs you might be familiar with. Many of these can be added to ubuntu - even completely free of charge (free as in beer).

---

### Post by allwin on 2007-01-22
> **tacm said:**
> This is a generalized question.  I am brand new to Ubuntu and Linux,  It has been a lot of work leaving windows.  I must unlearn and relearn EVERYTHING. I have gotten some great help here and for that Thanx to each and every one who has helped me.  It seems every time I want to do something with my machine I need this plug in or that modification to make it work.  My question is this.  Is it possible to get Ubuntu configured properly to do everything my windows OS did?  examples mp3, DVD playback, Flash, Java  I'm running an AMD64 AND I have the POS 4318 wireless card (That thanx to the forum I just got working after a week)  As much as I dis like Microsoft, I am wondering will I ever be able to get this machine to do all it could before I got rid of windows?

Yeah, I'm an old Windoze user myself, and I have to say that I was able to satisfactorily get everything on your list working.  Quite a bit of fooling around, I must admit.  The chief things I'm still looking for is a way to use my web cam (a cheapy newer one not yet supported) to create YouTube videos (haven't found an editor like Movie Maker yet, still searching); play MIDI using the synth on my sound card instead of the CPU being pegged; wireless (including roaming around and detecting other than my own home router); play a regular purchased music CD with out it stopping between buffers(!).

And though getting upgrades is automatic, they tend to frequently wipe out a lot of the customizations I might have made before the update (chiefly nVidia drivers getting smashed) leading to those wonderful WTF moments I remember from early Windoze.  Fact is, the unplanned and unscheduled release of so many updates every day is burdensome and doesn't lead to the stability I'd hoped for.  Every reboot since I installed UBUNTU is a crap shoot, it seems.

I'm getting more enamored with UBUNTU as I use it but I'm not ready to make the big leap yet, with prolly the same reservations you have.  Even if I got it all to work, I'm not sure the user experience is there.  While I'm getting to memorize terminal commands and the locations of things inside /etc/ to modify them, to me there's nothing like an environment where you never have to type out a whole file name (case sensitive yet) to get something done.  I can't even remember the last time under Windows that I needed to get to the command line because the UI didn't offer a way to click on something.

Ten years ago I messed with Yggdrasil linux, and back then X couldn't set itself up for the right screen rez, and neither does it today in 2007.  In UBUNTU, my disks came up with no 32 bit mode, just like Windows 3.1 used to do.  I had to spend time tuning both.  I see no virtue in such acts.  But it's getting there, if only they'd listen to us:biggrin: 

And that's my opinion, you asked for it.

---

### Post by tacm on 2007-01-22
> **allwin said:**
> 
I'm getting more enamored with UBUNTU as I use it but I'm not ready to make the big leap yet, with prolly the same reservations you have. 

And that's my opinion, you asked for it.
Well..... After virus apon virus apon spyware apon adware problems....not to mention my personel opinions of microsoft....I dumped it all together....Its just going to take me a long time to get up to speed with linux.  :D but ill keep a positive attitude :confused:  or at least try

---

### Post by allwin on 2007-01-22
> **tacm said:**
> Well..... After virus apon virus apon spyware apon adware problems....not to mention my personel opinions of microsoft....I dumped it all together....Its just going to take me a long time to get up to speed with linux.  :D but ill keep a positive attitude :confused:  or at least try

I've used Norton and Mcafee, and Black Ice Defender as a firewall.  Been lucky, I guess.  Nowadays Mcafee and Windows Defender.  Managed to keep spyware and viruses at bay just fine.

The one thing that worries me about Linux is...you can only get so much "system" from the official repositories.  The rest you have to cobble together from third parties, plus going out all over Google for hints and tips.  Even this forum.

Won't be long before some clown posts a bad SUDO command on his blog to cure some ill, or recommends a bad download, which tons of people gladly cut and paste and install without authentication.  That'll be just as bad as spyware and viruses, maybe worse.  All that in the name of getting your desktop to fly in space or something like that!

Once again, my opinion only, as I have crashed my box using some commands I have found here and there...then realized, hey, some guy tells me to SUDO this command and that command (wink wink) and I go ahead and do it.  That's even worse than some web page dropping an Activex on me, sigh.

Ought to be a better way...I'm just saying...

---

### Post by gh0st on 2007-01-23
> **tacm said:**
> :D :D :D :D  I hope I can get to that place

I might have to make that Dual-Boot joke my signature ;) 

Don't get me wrong I'm not one of these people who just wants to bash Windows and will find any excuse (they make it so easy though :D). I grew up using Windows and controversially for a Linux convert I don't hate Bill Gates. I just hate Steve Balmer and the way Microsoft conduct their business :D 

I used to have a good job as a .NET developer and in a lot of ways I only had that job because of Microsoft. I didn't hate them when they paid my bills.

Anyway, I'm getting off-topic here sorry. Basically I just wanted to say, don't feel guilty about using Windows sometimes, some people seem to see it as a cardinal sin, just remember you always have a choice and try to help all the people who don't even know they have a choice to realize it :D

There is lots of stuff to learn in the Linux world, it takes time but give it a chance and keep an open mind. You'll get comfortable in no time.

---

