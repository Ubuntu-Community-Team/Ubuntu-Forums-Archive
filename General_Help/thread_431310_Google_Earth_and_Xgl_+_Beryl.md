---
title: "Google Earth and Xgl + Beryl?"
date: 2007-05-02
forum: General Help
---

### Post by Mr Greencastle on 2007-05-02
Feisty, ATI Radeon Xpress 1100

I've tried downloading and installing Google Earth 4 different ways (.bin from site, apt-get, automatix, and even wine) and it seems to always get stuck at the 'initializing' splash after running it once its installed. I have 3d acceleration enabled and Beryl (with Xgl), works flawlessly.

Google Earth works near perfection in a regular Gnome session, so I wonder if this is an Xgl problem. Any help getting it running under Xgl and Beryl would be greatly appreciated!

Regards,
Mr Green.

---

### Post by kvonb on 2007-05-02
You might find that it's the ATI driver, I had that problem last year when I had an ATI card.

Are you disabling Beryl before running g-earth?  Just right click on the Beryl icon and select "metacity" as your window manager for the g-earth session.

If that doesn't work, you might try another ATI driver, but I need to warn you, that could be the start of many nightmares :S.

Good luck, Kev :)

---

### Post by lbyrd33 on 2007-05-02
I had the same problem and I just gave up.

---

### Post by Mr Greencastle on 2007-05-02
It doesn't seem to help disabling Beryl, and frankly, I'd rather not, as I have a desktop setup that requires it...

I'm also definetly not changing the driver, I had a bad experience with that in Edgy.

Thanks anyway, after all, I guess its just Google Earth, but the simple fact that it doesn't work bothers me :(

---

### Post by kvonb on 2007-05-02
Yes, I wouldn't suggest messing with the drivers, they are a real pain!

A not-so-helpful suggestion is to buy a cheap Nvidia card and switch to that.  I use an old 64meg Nvidia Geforce2/mx400 on my spare system, it runs Beryl perfectly.

You might be able to pick one up really cheap on ebay.

---

### Post by Mr Greencastle on 2007-05-03
It's unfortunate that the only solution is to buy a different brand of video card.
I'm using a laptop with an ATI Radeon Xpress, so buying the Nvidia isn't an option.
My desktop has an Nvidia card, though, and everything works.

I was really hoping someone had found a solution to this.

---

### Post by ianprinz on 2007-05-03
If it's any consolation I can tell you that Google earth should work. The setup on on one of our machine is Ati card + feisty Fawn + Beryl and works with Google Earth flawlessly. There's only one very essential item that we had to get right first and that was the xorg.conf file. After scouring the forums and howtos we found this guide ( [https://help.ubuntu.com/community/RadeonDriver#head-180e7f8934082e4a506ce23130b024b773218317](https://help.ubuntu.com/community/RadeonDriver#head-180e7f8934082e4a506ce23130b024b773218317) ) to setup the ATI card (a radeon 9200) and other settings which I cannot remember right now and Bingo! Beryl worked a charm and all other apllications, including Google Earth work perfectly. As an aside, we did install google earth as a download because all other attempts at installing it did fail.

If it's of any help I could post you our xorg,conf file for reference.

---

### Post by Mr Greencastle on 2007-05-03
After reading that guide, it looks like that it's only for Aiglx,
I'm not quite sure my card (Integrated laptop chip) is compatible with Aiglx 3d
acceleration.

I've tried it before, but the only thing that works for me is Xgl. My chip is an ATI Radeon Xpress 1100.

Has anyone had success with this card?

---

### Post by pocketman on 2008-04-02
The solution found [here]("http://ubuntuforums.org/showthread.php?t=453106") worked for me.

Good Luck!

---

