---
title: "Something is horribly wrong"
date: 2006-11-13
forum: General Help
---

### Post by FuturePilot on 2006-11-13
Today I noticed that something has gone horribly wrong with Dapper. Everytime I try to run something in Wine it crashes then logs me out. The same thing happens if I try to open the screen saver options. I get logged out. And the same thing happens when the screen saver tries to come on. It just logs out on me. What is going on?  *Scared*:icon_frown:

---

### Post by earobinson on 2006-11-13
do you get any error messages?

---

### Post by FuturePilot on 2006-11-13
No, nothing. Though sometimes some text flashes on the screen when it goes blank, but it's so fast I can't even read a word of it.

---

### Post by taurus on 2006-11-13
Do you run it from a terminal?

---

### Post by FuturePilot on 2006-11-13
I tried running winecfg from the terminal but the same thing happens. I've been trying to open the screen saver options from the System>Preferences menu and I can see the window open but then the screen goes blank and I'm back at the login screen.

---

### Post by taurus on 2006-11-13
Do you remember what you updated last?  Did you have anything special running like beryl or things like that?

---

### Post by FuturePilot on 2006-11-13
The only other thing I had running was Firefox. I did install some updates earlier. I can't remember exactly what they were. But I think there was one for Wine and there was one that kept getting held back. It was libgl1-mesa-dri

---

### Post by FuturePilot on 2006-11-13
Anyone have any ideas? This is very disturbing.....:???:

---

### Post by musicinmybrain on 2006-11-13
Sounds like it could be a 3D acceleration problem. A few questions that might help narrow it down.

Are the wine applications games?

Does the crash happen when you press Alt+F2 and run "glxgears"?

Are you using a proprietary video driver downloaded from the ATI or Nvidia site?

---

### Post by zgornel on 2006-11-13
Try deleting ~/.wine

---

### Post by FuturePilot on 2006-11-13
> **musicinmybrain said:**
> Sounds like it could be a 3D acceleration problem. A few questions that might help narrow it down.

Are the wine applications games?

Does the crash happen when you press Alt+F2 and run "glxgears"?

Are you using a proprietary video driver downloaded from the ATI or Nvidia site?
The Wine applications aren't games. The only thing I really had under Wine was the Windows version of Firefox. 
Yes the crash happens when I press Alt+F2 and run glxgears.
I have a GeForce 6600 and the driver is the default one that comes with Ubuntu. I'm thinking you're right about it being a 3D acceleration problem. It only seems to do this with things that use 3D acceleration.

---

### Post by musicinmybrain on 2006-11-14
> **zgornel said:**
> Try deleting ~/.wine

I suspect that might not fix it since the problem occurs with glxgears and other non-wine applications. Also, doing that will delete any Windows programs that have been installed into wine's drive_c directory tree.

---

### Post by musicinmybrain on 2006-11-14
> **FuturePilot said:**
> I'm thinking you're right about it being a 3D acceleration problem. It only seems to do this with things that use 3D acceleration.

That's what it seems like to me, though Firefox in wine is an odd exception. No idea what could be causing it, though. Anyone?

Edit: [Here's a launchpad bug]("https://launchpad.net/distros/ubuntu/+source/xorg/+bug/44939") that appears to cover this problem. Don't see a solution there, though.

---

### Post by FuturePilot on 2006-11-14
> **musicinmybrain said:**
> That's what it seems like to me, though Firefox in wine is an odd exception. No idea what could be causing it, though. Anyone?

Edit: [Here's a launchpad bug]("https://launchpad.net/distros/ubuntu/+source/xorg/+bug/44939") that appears to cover this problem. Don't see a solution there, though.

That's interesting. Same graphics card: Nvidia GeForce 6600. Hmmmmm. Thanks for that info. At least I'm not the only one with this problem.:p Anyone else have any ideas?

---

