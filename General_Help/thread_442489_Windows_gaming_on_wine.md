---
title: "Windows gaming on wine?"
date: 2007-05-13
forum: General Help
---

### Post by HPCE_Larry on 2007-05-13
Will I be able to run windows games with wine? I checked the wine FAQ and it wasn't mentioned.

If so, do I simply install it like I would in windows or is there something special I have to do? Pardon my ignorance here, I'm rather new at this.

---

### Post by aldenhg on 2007-05-13
Yes and no. You should check [http://appdb.winehq.org/](http://appdb.winehq.org/) for the games that you want to use. If you can't get them to work you can always try out Cedega, which is a commercial fork of Wine that is specially meant for gaming. My results with it have been mixed, especially with DirectX 9 games (HL2, CS:S, FarCry, etc.). They run, but not very well and you're not going to get the same level of graphical effects that you would in Windows. I personally reccomend that you play whatever games you can natively in Linux (Wolfenstien: Enemy Territory, UT2K4, Doom3, World of Padman - I like FPS, if you can't tell) and then reboot into Windows for anything that isn't native. If you want a decent list of Native linux games, check out [http://www.tuxgames.com/](http://www.tuxgames.com/).

---

### Post by orb9220 on 2007-05-13
If you are into gaming Then you will need a dual boot setup. I have a 8gb partition that I use for gaming in xp.

I don't know but there seems to be quite an unsatfactory group that end up installing xp after ubuntu then they have to restore grub to have a dual-boot anyway for gaming. Plus it makes for a nice backup OS to get to these forums if you end up borking your ubuntu.

---

### Post by strabes on 2007-05-13
orb: That's about how I view my XP install. It's a backup. Once I grow out of gaming (when I finally finish college in 2 years) I'll replace that other OS with another linux distro.

HPCE: I 100% recommend you dual boot if you're into gaming. This page might help you: [http://ubuntuforums.org/showthread.php?t=358183](http://ubuntuforums.org/showthread.php?t=358183)

---

### Post by HPCE_Larry on 2007-05-13
I'm trying to use Ubuntu until I can afford to get windows. I just built a awsome PC and really want to use it, but not having windows for gaming sorta sucks. I'll check out those websites, thanks.

---

### Post by aldenhg on 2007-05-14
Well, I have to commend you for not just pirating Windows. Microsoft may be the devil, but we do live in a society of laws. Good job!
Just so you know your options, if you have a valid install disk for a previous version of Windows, and XP upgrade disc can be had for $99 nowadays - OEM versions might be out on the interwebs for even less.

---

### Post by HPCE_Larry on 2007-05-15
ok i installed a game using wine but now I can't find out where it installed it. How do I make it run?

---

### Post by DoktorSeven on 2007-05-15
Wine creates a "fake" C drive in your home directory under .wine/drive_c

So if you installed something in Program Files\Programname, it would be in 

**~/.wine/drive_c/Program\ Files/Programname/**

You can run it by opening a terminal, typing **cd ~/.wine/drive_c/Program\ Files/*name-of-program*** and running with **wine *programname.exe***.

---

