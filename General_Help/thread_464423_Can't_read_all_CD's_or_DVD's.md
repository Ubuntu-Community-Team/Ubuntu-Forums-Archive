---
title: "Can't read all CD's or DVD's"
date: 2007-06-04
forum: General Help
---

### Post by bob-linux-user on 2007-06-04
Greetings to all.

I have a weird problem. Have just cleanly reinstalled Feisty and added some applications via Synaptic etc. I now find that my DVD drive will only read some CD/DVD but not all.

When I find that a disc has not been mounted, I go to Places-Computer.
I see two icons
CD-ROM 1
and
CD-RW/DVD+/-RW Drive
(this is odd in itself as I only have one drive)

When I click on cd rom 1 I get:
Unable to mount the selected volume.
mount: special device /dev/scd0 does not exist

When I click on the other icon I get
Unable to mount media.
There is probably no media in the drive

It is not a fault with the drive or the discs as they work ok when I boot the PC into Windows.

Some discs will load OK but I have not spotted a pattern of failure.

Can anyone help please ? My faith in Ubuntu has been shaken and I want to see the light again !

Bob

---

### Post by zvacet on 2007-06-04
**system>settings>removable drives&media>storage>chek all boxes**

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by fdrake on 2007-06-04
sometimes i find a similar problem when i burn data on windows. it says that the device cannot be mounted on ubuntu.

---

### Post by rml1732 on 2007-06-04
I have exactly the same problem as bob-linux-user and I followed zvacet's suggestion to no avail. I was able to read cds and dvds prior to the most recent kernel upgrade, but I am a n00b and that may have no bearing on the problem whatsoever.

---

### Post by bob-linux-user on 2007-06-05
Thanks for your postings

I have tried zvacet's suggestion as well. It did not work. I don't think it is a question of restricted formats or codecs. Surely Nautilus should mount and let me explore files even if other programs are not installed. The DVD it would not see is a DVD from Linux Format Magazine-not an encrypted DVD. The DVD works fine in the same computer when booted in Windows.

?

Regards

Bob

---

### Post by zvacet on 2007-06-05
Right click to panel>add to panel<scroll down>system&hardware>mount disc(or something similar because I don´t use english version).Maybe that will help.

---

### Post by bob-linux-user on 2007-06-05
Thanks Zvacet. I tried it and it did not work. Sorry.

?

Regards

Bob

---

### Post by quasi_71 on 2007-06-07
Same problem here.  I have a Dell GX150 running Ubuntu Feisty.  I removed the cd-rom drive and replaced it with a dvd reader/cd writer combo drive.  I can read CDs but for some reason can't write and am completely unable to see any files on dvd media.  The drive works fine in other operating systems.  I tested it just now with Geexbox and it played a dvd movie flawlessly.  I also have 2 drive icons.......   help !

---

### Post by Ahunt on 2007-06-08
Since the most recent updates I have had a similar problem. I have two CD drives (one DVD, one CD-ROM) and suddenly since the update I can't write data to CDs - just get the same errors reported here. Also Totem does not read DVDs put in the DVD drive, although I can pull them up on gxine.

This looks like another "system-breaking" update where something that was working is wiped out by an update, similar to the digital camera problem reported at [http://ubuntuforums.org/showthread.php?p=2685665](http://ubuntuforums.org/showthread.php?p=2685665)

What happened - are there any solutions that work?

Adam

---

### Post by quasi_71 on 2007-06-08
Got it fixed... not sure which of the following things actually did the trick though......
1- Installed Automatix
2- Installed DVD codecs (AUD-DVD) ?
3- Allowed an automatic update to install (mentioned something about HAL)
4- Rebooted

---

### Post by Ahunt on 2007-06-08
Hey that is great that you found a fix. 

Can you provide more info on "Automatix" and "DVD codecs (AUD-DVD)". I couldn't find them in the repositories through Add/Remove. What are they and how do we install them - remember we are beginners here!!

Thanks for any help you can provide.

Adam

---

### Post by quasi_71 on 2007-06-09
I'm a complete Linux newbie too mate..... been using Ubuntu for maybe 2 weeks now.  Automatix is another software installer thingie - get it here: [http://www.getautomatix.com/](http://www.getautomatix.com/) - just chose installation, then Ubuntu, then your version and open the link (Ubuntu seens to know what to do with it) and you're off.  Once that's done, fire it up and choose the DVD codecs from it's list.  Easy enuf.

---

### Post by rml1732 on 2007-06-19
Bob-linux-user, I found the following list of codecs and installed them. Problem solved.

You should be able to just copy and paste this into terminal.

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui libcurl3-gnutls liboggflac3

Hope it works for you.

---

### Post by bob-linux-user on 2007-06-30
Thanks RML1732 and others. I can't repeat the initial problem at the moment but as soon as I do, I will try your solution.

Regards

Bob

---

### Post by bigjack on 2007-07-20
I also have this problem with 7.04 Ubuntu on an IBM Thinkpad T40.  CDs and DVDs that I could read several weeks ago no longer get loaded.  They just make a clicking sound for awhile.  Some CDs and DVDs load OK.  I've been through all the help sites for codecs, CD/DVD playing, ripping etc, but nothing has helped.   All the CDs work on another computer and CD/DVD player.  I did not have this problem until after an update several weeks (a little over a month?) ago.  I've tried all the suggestions, including Zvacet's, and the Automatix etc. solution, but nothing has solved the problem.

Any more suggestions?

---

### Post by quasi_71 on 2007-07-23
Bigjack - your problem sounds more hardware related to me.  Try booting the Ubuntu Live CD and see if you can read discs.  Or try another Linux Live CD like Puppy Linux, DSL, or even WinPE/BartPE/ERD Commander if you want to test it in a Windoze environment.

---

### Post by dthiery on 2007-08-15
I guess I'll chime in too.  I'm having the same problem with DVD's on my system.  If I put in a CD or data DVD (not a movie) it automounts fine, but if I try to put in a movie DVD the drive spins for a while and never mounts.  I know for a fact that this did work before (can't say how long before) and can't think of any software I've added to my system that would change this.

Dave

---

### Post by piege on 2007-10-30
I have the same problem... 

I can assure you that the dvdpayer is working ( I can boot the livecd ).

I tried everything in this post ... 

I beleive this problem is more than just hardware trouble ...

---

