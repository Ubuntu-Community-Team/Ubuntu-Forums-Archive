---
title: "Cant Change Appearance O_o"
date: 2008-04-22
forum: General Help
---

### Post by necronzero on 2008-04-22
This is weird... I have an intel embedded 945G graphics card.
Everything was fine... I installed Wine, emule, and some other programs...
Then I added the extra effects on my desktop and it was working... so i decided to try the emerald themes.

I installed everything (except beryl-manager) (cause i cant >_> if anyone shows me how tnx... (ubuntu 7.10)

I managed to get the theme to work. I reboot my PC for updates n stuff and i didnt have the theme anymore, and whats worse, i cant even change my appearance now, evry time i click the extra effects button it tells me it cant change it.

I didnt care, I installed cedega and installed Guild Wars. to my surprise it said I cant run the game because i have no 3D acceleration.

Can someone show me how to turn on 3D acceleration on this graphics card?
Can someone tell me how to fix the desktop effects thing??? 

THANKS IN ADVANCE

---

### Post by scientist1971 on 2008-04-22
I have the same problem with cedega and 3D acceleration which is a real #%$* as you have to pay for it
if I sort mine out I will post the solution straight away

---

### Post by Ub1476 on 2008-04-23
Turn of Compiz (System>Preferences>Appearance>Visual Effects>None) and try to launch the game..

Beryl/beryl-manager is outdated. It's called Compiz-Fusion now. It's already installed, but to configure it:

```
sudo apt-get install compizconfig-settings-manager
```

It can be launched as Advanced Desktop Effects from Preferences. 

You have to set visual effects to custom for this to work.

If you for some reason has no direct rendering,

```
glxinfo | grep direct #if yes, you have direct rendering
```

post the output of:

```
cat /etc/X11/xorg.conf
```

---

### Post by necronzero on 2008-04-23
after rebooting everything was fine again O_O

---

