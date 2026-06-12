---
title: "Has anyone else switched back to Feisty?"
date: 2007-11-06
forum: General Help
---

### Post by dwasifar on 2007-11-06
I moved to Gutsy on my laptop, my desktop, and a machine I'm building for someone.  I'm still using it on the laptop, for the time being, but on my main desktop I've gone back to Feisty.  From my experience, Gutsy seems not quite ready for prime time.  Here's why.

The first Gutsy install was on the machine under construction.  When that install was completed, desktop effects, which had formerly worked under Feisty, left the windows without frames.  A search of the forums turned up all sorts of different suggested fixes, none of which worked.  Eventually I figured out that I needed to install xserver-xgl.  Why didn't that get installed, if it was going to need it?  Who knows.

The second install was an update to my laptop, which actually is the best of the bunch, though I notice it boots a whole lot slower now, and is a little slower in general.  This I assume was compiz's fault.

The third Gutsy install was an upgrade to my main desktop.  I cloned the hard drive beforehand and let update-manager do the upgrade.  What I wound up with was a desktop that gave me desktop window effects but wouldn't use any themes.  I also had a small collection of other application weirdnesses, which I won't go into except to say that they were apparently related to a previous installation of kubuntu-desktop.  So I decided to do a fresh install.  This went smoothly (well, except for barfing on the lowvoice.nl repo, which all the installations did), and I was able to use themes, but I immediately noticed that the machine became slower-booting, slower-operating, and generally a little quirkier than it had been. Apps, especially Firefox, would gray out and freeze for a while, apparently randomly.  MP3 lame encoding in Grip was far slower.  Web access seemed slower.  I got a lot of unexplained disk activity, which I'm thinking was for indexing, but it interfered with tasks like streaming video.  Automatix barfed on a missing c library.  My Thunderbird mail files were mysteriously corrupted after a day or so (though Thunderbird did fix them, more or less, after a restart).  Finally yesterday I was getting a lot of random slowdowns, opened up System Monitor, and discovered that something, I know not what, was eating CPU, even though it wasn't showing in the task list.  It was also generating a lot of disk activity.  Without knowing what task to kill, I decided to just reboot.  About 30 seconds after the Gnome desktop started, it locked.  Applications already open kept running, and the mouse would move the pointer, but clicks and keystrokes had no effect.  Another reboot gave me the same results.

At that point I said screw it.  I'm sure all these things have solutions, but none of it falls into the "just works" category.  I powered down, swapped the SATA cables between the main HD and the clone, and booted back into Feisty, where I will stay for a while.

I've been using Ubuntu as my main desktop since Hoary, and this is the first release that has made me abandon it and revert to the previous.  Feisty was pretty stable for me the whole time, even while taking obvious abuse like installing kubuntu-desktop, then switching back to Gnome and still running a handful of KDE apps.  And I had almost forgotten what it was like to be pushed into rebooting, Windows-style, to recover from some runaway mystery process or unknown instability.  A friend's system, updated from Feisty around the same time, is similarly slower and not as stable as when it was running Feisty.

I appreciate that a lot of hard work probably went into Gutsy, and I know that including compiz by default is ambitious, but I can't shake the impression that this release was rushed out to meet a deadline.  It's far from stable.  It feels like a beta.  It's actually making me consider switching to OpenSUSE or PCLinuxOS; I'm not ready to really DO that just yet, but it's crossing my mind a lot more frequently.

---

### Post by stoodleysnow on 2007-11-06
Gutsy and happy.:)

---

### Post by spamgoat on 2007-11-06
Although I believe this thread is somewhat useless, i'm still using it to make a shameless plug to my other thread [here]("http://ubuntuforums.org/showthread.php?t=599978") which is the reason i'm likely switching back to Feisty.

The only reason I still haven't is because the things Gutsy does improve upon (the new features that do work) are great, and I just know they'll be gnawing at me.

But the bug explained in my other thread is just driving me to the brink of sanity, so i've little choice. :(

---

### Post by whistlerspa on 2007-11-06
Agree a little with the comments - Feisty did have a 'more stable' feel about it and my system does launch the desktop a little slower and multimedia codecs took a while to sort. But overall it still feels like progress. 

Also agree that once a year for a new version might be better.

---

### Post by glotz on 2007-11-06
The next release will be a LTS. It's good the Ubuntu folks are pushing the envelope with gutsy. Hardy will hopefully be as rock solid as dapper (the current LTS).

---

### Post by Craigus on 2007-11-06
Sticking with Gutsy on my main desktop, although lack of suspend is irritating me greatly. My (older Toshiba) laptops were unbearably slow with Gutsy; went back to Dapper Xubuntu on one, Antix M7 on another (after trying Fluxbuntu 7.10 rc) and Mepis 6.0 on the third.

---

### Post by chaumurky on 2007-11-13
My USBUIRT is currently borked with Gutsy's 2.6.22 kernel so I had to roll that back to Feisty's 2.6.20 along with restricted modules, nvidia etc. Everything else is shweet. :)

---

### Post by LisaM on 2007-11-13
I want to revert!   I'm having loads of issues with my Dell Inspiron 1420N notebook that came along with the upgrade, and things are only getting worse.  Please tell me HOW to revert to Feisty.

Thanks!

---

### Post by chaumurky on 2007-11-14
Generally it's as easy as moving your /home to another partition and reinstalling Feisty from scratch on the system partition. Unless you tweaked anything in /etc or /boot you should be right as rain (if you did, save those config files for reference later on. On reinstall create the same user and point /home to your other partition.

---

### Post by SomeGuyDude on 2007-11-14
> **whistlerspa said:**
> Agree a little with the comments - Feisty did have a 'more stable' feel about it and my system does launch the desktop a little slower and multimedia codecs took a while to sort. But overall it still feels like progress. 

Also agree that once a year for a new version might be better.

I think a good idea might be a once a year full change (6.0 -> 7.0 -> 8.0), but at the 6 month mark we get kind of a "midterm" that patches the current one with a bunch of the things they're going to be adding in the full release. I have to admit that bi-annual full upgrades always leave me with the impression that none of the current editions are solid enough to last more than a few months.

I'm on Gutsy because Feisty recognized jack squat in my hardware, however. I've got plenty-o-reservations, but nothing too major.

---

### Post by tiepolo on 2007-11-14
Many things didn't work after upgrade :

scanner, printer, audio, wi-fi, etc.

i'm back to feisty by  total reinstall and lost confidence in ubuntu - gutsy isn't even a beta release and the features added are of no interest to me.

i'll also leave debian as a second OS to always be able to recover.

Paolo

---

### Post by Dave Otter on 2007-11-14
Switched back to Feisty.kept losing sound  in Gutsy-cannot load Feisty from CD-had to update from Dapper but it works fine.

---

### Post by #Reistlehr- on 2007-11-14
1 laptop i went back to feisty. My server is still on feisty. My desktop went back to feisty, my other two laptops run beautifully after a day of tweaking gutsy. 

geh.

---

### Post by Sockerdrickan on 2007-11-14
feisty is better than gutsty :(

---

### Post by qamelian on 2007-11-14
> **Tux0r said:**
> feisty is better than gutsty :(
Nope. I would rather change to another distro entirely than go back to Feisty. The last Ubuntu release that worked as well as Gutsy was Breezy. In Dapper, Edgy, and Feisty, things got broken relating to my laptop that now work again. I've installed Gustay on a wide variety of hardware and it has been the most trouble free release in a long time.

---

### Post by bartos on 2007-11-15
I Have been thinking of going back to Feisty also.
Ubuntu Ultimate is my what I install with because it has all the software already loaded with it.
I have noticed in Gutsy that more windows turn grey during operations than with FF.
Also login is super slow 
Am going to try a straight Gutsy install and if same problems show up then maybe revert to FF
Does Feisty still get the same software and security updates as Gutsy? I would like to stay up to date if i do go back.

---

### Post by Druke on 2007-11-15
I'm moving back on my laptop, network manager doesn't like my wifi with or without ndiswrapper, and I had it perfect on gutsy. sad :( gutsy is awesome.

---

### Post by bartos on 2007-11-17
I went back to Feisty.
I don't build a fast machine to be slowed by a OS. I can do that with my old OS (won't honor them by mentioning name)
Login was slow,grey windows all the time.

---

### Post by drawkcab on 2007-11-18
> **tiepolo said:**
> Many things didn't work after upgrade :

scanner, printer, audio, wi-fi, etc.

i'm back to feisty by  total reinstall and lost confidence in ubuntu - gutsy isn't even a beta release and the features added are of no interest to me.

i'll also leave debian as a second OS to always be able to recover.

Paolo

I've lost confidence too.  I've been with X/Ubuntu for two years but Gutsy has ended the romance.

I'm stoked on this gnome remaster of pclinuxos.  Rumor has it that it's going to become an official branch:

[http://www.linuxgator.org/Gnome/gnome_page/gnome.html](http://www.linuxgator.org/Gnome/gnome_page/gnome.html)

If these guys can get broadcom working with their livecd, sans ndiswrapper, I don't see why ubuntu can't get it to work with an install.

---

### Post by Grafster on 2007-11-18
I miss dapper style stability.
Hopefully Hardy will get back to the "it's not sexy but it works" ethos.
(I think working is actually really sexy, but I seem to be in the minority).

---

### Post by drawkcab on 2007-11-18
So I got wireless working in Mint but not in Gutsy.  How does that work?

---

### Post by fjgaude on 2007-11-18
> **LisaM said:**
> I want to revert!   I'm having loads of issues with my Dell Inspiron 1420N notebook that came along with the upgrade, and things are only getting worse.  Please tell me HOW to revert to Feisty.

Thanks!

Could you tell us what the issues are?

I know of no way to "revert" except to reinstall from a LiveCD.

---

### Post by Grafster on 2007-11-23
I have offically moved all the way back to feisty.
Wireless is broken. And it worked before it seems impossible to fix now and I just can't be bothered to waste the time and effort.

(there were other, serious screen problems for a while too, but I can't be sure what part of that was gutsy and what part of that was me just not understanding how to configure xorg properly)

Hopefully Hardy will stop trying to change stuff just to change stuff and start getting back to "it just works" (which, once upon a time, was the ubuntu creed).

---

### Post by ImpressMe on 2007-11-24
> **drawkcab said:**
> So I got wireless working in Mint but not in Gutsy.  How does that work?

Upgrading to Gutsy smashed my wireless. A clean reinstall and it worked.

Perhaps a clean install of Mint is the reason?

---

### Post by DjBones on 2007-11-24
Gutsy crashes on my laptop all the time .. its not a problem because i rarely do mission critical work on it lol, but i never had that problem when it ran Feisty

My other computers all run Debian, absolutely loving it..
If you have a chance, it requires a bit more know-how .. but its much faster and stable

(ubuntu's packages are just refurbished snapshots of the debian/unstable packages anyway lol)

---

> **Grafster said:**
> I miss dapper style stability.
Hopefully Hardy will get back to the "it's not sexy but it works" ethos.
(I think working is actually really sexy, but I seem to be in the minority).
+1 ;)

---

### Post by Afkpuz on 2007-11-24
I did switch back after trying gutsy for a while.  I had lots of programs start locking up on me.  Firefox was a big one.  There were several little things that I can no longer remember, but I know that they all added up to more frustrations than I had in fiesty.  I probably will upgrade to hardy when it comes out though.

---

### Post by zonum on 2007-11-29
I have switched to Feisty as of last night (from Gutsy).  I had taken an image of my Feisty install prior to updating to Gutsy, and had it available so it was just a matter of applying the image to the drive and and rebooting.

In anycase, my reason to reverting back was due to too many grey/gray windows (specially with Firefox, and then "Force Quit"'ing FF, Re-starting the session and then being able to click on the video that had greyed out FF, and have no issues the second time around).  I also had issues with Rhythbox greying out when pressing the Next button when playing mp3's, and Movie Player just stopped playing wma files when it used to play them just fine.

Anyway, I will be doing testing with Feisty although I expect no issues as I didn't have them prior to updating the Feisty installation via Synaptic with Gutsy.  My plan is to verify that Feisty works "perfect" for my system, and then I will update via Synaptic, to Gutsy and do more testing and try to capture when it is that I start seeing the grey windows, issues, etc...

Thanks.

zonum

---

### Post by maljaros on 2007-11-29
I found, after installing Gutsy, that Feisty, Suse and Windows are still all available through GRUB at boot-up so don't understand the question about how to roll-back from Gutsy to Feisty.

---

### Post by Grafster on 2007-12-01
> **maljaros said:**
> I found, after installing Gutsy, that Feisty, Suse and Windows are still all available through GRUB at boot-up so don't understand the question about how to roll-back from Gutsy to Feisty.

You mean after "updating to gutsy through synaptic (or apt-get) that...".
If you've done an install (a clean install) you have nothing to go back to.

---

