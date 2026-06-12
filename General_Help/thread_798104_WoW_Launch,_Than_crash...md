---
title: "WoW Launch, Than crash.."
date: 2008-05-17
forum: General Help
---

### Post by 1omgz on 2008-05-17
Ok, im running ubuntu 6.06 and i installed world of warcraft fine, but than i type this in my console :

wine /home/joey/desktop/wow/installer.exe

Than in the installer i click play world of warcraft and the launcher opens, the launcher is completley blank accept for "Play".

So i click play , and it crashes my comp.

i dont no what the problem could be i have been searching for a while and i still cant find out

ubuntu 6.06

Thx for your help  ](*,)

---

### Post by 1omgz on 2008-05-17
anyone?

---

### Post by Tru7h on 2008-05-17
version numbers of wine and wow please
also info on your computer like: proc, video card, etc.

---

### Post by 1omgz on 2008-05-17
Wine 0.9.9

WoW : Up to date

Video card : ATI graphics card (WoW ran fine on windows with it.)

---

### Post by g2g591 on 2008-05-17
well, just offhand, your chances of decent performance arn't very great, ATI doesn't have particulary nice drivers/support for Linux . (Nvidia is good in this regard)

---

### Post by Tru7h on 2008-05-17
Did u do a clean install of wow as in put ur discs in install it and run the hundred or so patches or did u drag and drop it from ur windows install?  The dang thing gets corrupt way to easily.

---

### Post by 1omgz on 2008-05-17
hmmmm so my problem is most likley my gfx card than.





well i have an ati radeon 800x or something like that, it was like $800 and it doesnt fit in my comp, it was actually given to me by my dads friend, i wish that worked.

---

### Post by kcy29581 on 2008-05-17
Well, first of all that is not how you run WoW in Wine (Linux). Looking at your post it's clear you are using the installer (from Blizzard's site most likely?) to try and run WoW.

Assuming everything is installed at their default locations, at a terminal you run:
>  wine /home/<username>/.wine/drive_c/Program Files/World of Warcraft/Wow.exe --opengl

Explaining the command in detail:
wine - running WoW via wine
/home/<username>/.wine/drive_c/Program Files/World of Warcraft/Wow.exe - path to where WoW is installed
--opengl - runs WoW in opengl graphics mode, as the DirectX mode is highly unstable in Wine

I can say that WoW runs absolutely perfect with this in Linux/Wine. If you need any other help, just shout and I'll answer. :) (For example, I use Ventrilo too, and this works perfectly with PulseAudio as well!)

---

### Post by kcy29581 on 2008-05-17
Also, are you using the proprietary AMD drivers, or the standard Xorg ones? Reason I'm asking, I only use NVIDIA cards, and from experience only the proprietary ones work for gaming.

---

### Post by 1omgz on 2008-05-18
ya, im gonna try the 

wine /home/<username>/.wine/drive_c/Program Files/World of Warcraft/Wow.exe --opengl

but i think that wine will get confused cause of spaces

---

### Post by 1omgz on 2008-05-18
ughh it still crashes

---

### Post by 1omgz on 2008-05-18
any 1 ??

---

### Post by Trance56k on 2008-05-18
Try this guide [http://www.wowwiki.com/Linux/Wine]("http://www.wowwiki.com/Linux/Wine") good luck

---

