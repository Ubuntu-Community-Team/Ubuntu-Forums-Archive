---
title: "thinking of moving from win 7 to ubuntu..advice needed"
date: 2013-02-21
forum: General Help
---

### Post by lithiumKid1976 on 2013-02-21
Hi
 I’m seriously thinking about making the change from win 7 to Ubuntu 64bit
Currently, I use my machine for gaming, study, website design (basic) , music  and photos.
Before I make the leap, I have a few questions.. &#61514;

**Machine Spec**
Triple core AMD  phenom 2, 68GB SSD, 8GB ram, and GPU (think its ATI )

**Games.**
I use steam for MW3 and TF2 mainly. does Steam work well in Ubuntu? 
Also, the backed-up files games files from my win 7 machine, can they be used., or as it will be running on Ubunutu, would I need to do a new download and install again from scratch.

**Retro Games**
Does Ubuntu support MAME and retro gaming?

**Virtual Machines**
I know virtual box will run on Ubuntu, and I have been using this on windows 7. 
Do you think the virtual disks from windows 7 will open in Ubuntu? (I’m doing MCITP and have a test domain set up and configured, and don’t really want to start from scratch on this.. )

**I-tunes Integration**
I use,(and quite like&#61514;) I-tunes a lot. I have appleTV, which points back to a share on the win 7 box, from here, i can play my music and look at my pictures etc..

But if I went to Ubuntu, would I lose this ability? I.e. i believe  ITunes doesn’t work with Ubuntu?

**Raid**
I have 2 500gb disks, that i want to set to Raid 0. Is this possible under ubuntu.?

That’s it, any advice appreciated.

---

### Post by Habitual on 2013-02-21
> **lithiumKid1976 said:**
> **Virtual Machines**
I know virtual box will run on Ubuntu, and I have been using this on windows 7. 
Do you think the virtual disks from windows 7 will open in Ubuntu?
if you export them (File > "Export Appliance") and re-import into the "new" Virtualbox environment.

wrt: 
iTunes, you will have to use a|the Virtualbox Windows installation. (The appliance you imported)...

---

### Post by Mark Phelps on 2013-02-21
Not a Gamer, so my advice would be to post a thread in the Gaming forum  section naming the specific games you want to run.  With any luck, folks already running those, or having tried to run those and failed, will respond.

In general, Linux is a bad environment for trying to run Windows games -- but, as with anything else, there are exceptions.

---

### Post by CloakandPigeon on 2013-02-21
TF2 is available on Steam linux, but you likely won't be running MW3 on Ubuntu.  

My suggestion would be to dual boot.

---

### Post by lithiumKid1976 on 2013-02-21
hi 
thanks for the replys.

due to the 60GB limit on the ssd, roughly how much space would i need on the disk to dual boot into Ubuntu?
thanks

---

### Post by Linuxratty on 2013-02-21
As to games,yes Steam runs on Ubuntu.

[http://store.steampowered.com/browse/linux/](http://store.steampowered.com/browse/linux/)

Five G should be fine.

[https://help.ubuntu.com/12.04/installation-guide/powerpc/minimum-hardware-reqts.html](https://help.ubuntu.com/12.04/installation-guide/powerpc/minimum-hardware-reqts.html)

---

### Post by Mark Phelps on 2013-02-21
Understand that any Windows games you want to run in Linux will have to be re-installed through Wine (or one of its equivalents); you can't just point Wine to the Game already installed in Windows.

So, the space for those will have to be added to the space for Ubuntu.

---

### Post by CloakandPigeon on 2013-02-21
> **lithiumKid1976 said:**
> hi 
thanks for the replys.

due to the 60GB limit on the ssd, roughly how much space would i need on the disk to dual boot into Ubuntu?
thanks

Ubuntu doesn't take up much space when compared to Windows, I currently run the system on a 32GB ssd and have /home partition on my regular drive.  Has worked out pretty well, and Ubuntu boots lightning quick.

---

### Post by JiuJitsu500 on 2013-02-21
Yeah bro, you're going to want to

A) stick with Windows. Since you game, you cannot beat that platform. Virtualization cannot possibly allocate all resources properly to do it right, unless you have an uber-uber PC, and it's impossible for a translator like WINE or Parallels to do it correctly or fast enough for MW3 or the like (at least for now, though it is catching up).

B) Switch fully to Ubuntu and realize the newer games are simply not going to happen for you. I have a vastly powerful laptop for Skyrim and it can't even play that right so far.

C) Split the SSD and still give up games. Ubuntu doesn't need a lot of space, 8GB for the entire system and a TON of apps, but you can't expect it to be windows or do windows things. It's  more powerful and efficient platform for everything except gaming and brand-spanking-new hardware. The drivers are also behind for the most part (again, new hardware mostly).

D) get a second SSD for Ubuntu. Like a boss.

E) Don't drink and drive. And don't do drugs. Drugs are just bad, mmmkay? :)

---

### Post by fantab on 2013-02-21
**Dual Boot**, is the word for you. 

Games made for Windows play best in Windows only, barring a few exceptions which work via WINE.
So it is better if you keep Windows and also have  Ubuntu installed (have your cake and eat it too :-)). You can use Windows for your games and Ubuntu for everything else... until such time you get fond of games made for Linux.

There is a lot of information on this forum and on WWW on how to dual boot Windows and Ubuntu...

Good Luck..

---

### Post by hawthornso23 on 2013-02-21
Steam works just fine in linux. Recommend switching to metacity before starting steam though to get better performance. If you already have a steam account with steam games for windows then you will be able to play those games in linux so long as there is a linux version.  You'll have to install but won't have to buy the game again.

TF2 is already on linux. There are a bunch of good games already and they are quickly adding more.

---

### Post by csillva on 2013-02-21
> **lithiumKid1976 said:**
> Currently, I use my machine for gaming, study, website design (basic) , music  and photos.

So, you've given lots of good reasons for using Windows, any compelling things making you want to use Ubuntu? Given your familiarity with Virtualbox, I'd suggest installing a Windows addon to create a second virtual desktop [1], then creating a new Ubuntu Virtual Machine and running it in seamless mode on the second virtual desktop. 

[1] [http://www.lockergnome.com/windows/2012/02/28/how-to-create-multiple-virtual-desktops-in-windows-7-for-free/](http://www.lockergnome.com/windows/2012/02/28/how-to-create-multiple-virtual-desktops-in-windows-7-for-free/)

---

### Post by GameX2 on 2013-02-21
> **lithiumKid1976 said:**
> 
**Retro Games**
Does Ubuntu support MAME and retro gaming?

Retro game play really well, I've tested it.  I don't know about MAME, however.

NES : FCEUX (In the repositories);
SNES : SNES9x (Add a PPA);
GameBoy / GBA : VBA-M (Don't even remember how I got it.  Maybe it was a DEB);
Sega MasterSystem / GameGear / Genesis-CD-32x : Kega Fusion;
NullDC 1.0.3 : Use Wine 1.5.15 (PlayOnLinux make the use of different Wine versions easy).  From what I've tested, Shenmue 2 play really well (Pretty much as good as on Windows).
Project64 also work correctly, depending on the software version, and Wine version.  Check the Wine App DB. ;)

---

