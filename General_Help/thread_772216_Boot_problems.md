---
title: "Boot problems"
date: 2008-04-28
forum: General Help
---

### Post by rustyknife on 2008-04-28
I finally managed to install Ubuntu through the use of the Alternate CD and it only booted correctly once :(

After installing I went to boot using the first option, which gives me a loading bar that moves across the screen and after a few seconds becomes distorted and spreads across the screen. After a few more seconds the screen then goes black and the computer restarts. 

I then tried using the recovery option which loaded up Ubuntu just fine. Ubuntu downloaded the graphics drivers and then I restarted as it asked me to. After I decided to boot Windows as I had some things to do, but later when I attempted to boot Ubuntu again none of the options work. I still get the loading bar error and if I delete the quiet splash line it says "fsck died with exit status 8" and below that it says something about an automatic root filesystem check which does nothing. Although working before the recovery option does not work anymore and gives me a segmentation fault.

What could possibly be wrong?

---

### Post by upthelum on 2008-04-28
If no-one suggests otherwise i would try a re-install with a different cd.

---

### Post by santaslittlehelper on 2008-04-28
If you do reinstall then try to add "noapic" to the line where you removed "splash".
If that works you can add it to your menu.lst.
Once you get some vga drivers install you should be fine though.

---

### Post by rustyknife on 2008-05-01
I found that adding noapic nolapic and apci=off to the recovery mod e boot options allows me to reach the login screen. However, when I enter my password and press enter it grey's over the boxes and just sits there. If I press ctrl-alt-f1 and try and login I can't enter any text into the password bit(I have tried entering my password and pressing enter anyway but it just asks me for my username again). I hope there's some simple solution to this because the login screen is the farthest I can get and nothing else is working at all.

---

### Post by rustyknife on 2008-05-02
Bump?

---

### Post by santaslittlehelper on 2008-05-02
Are you sure you are using the right password? It is case sentative.

You can try to set a new one.
Boot in to recovery mode (by pressing Ecs at boot) then choose recovery mode.

Then type;
```
passwd *username*
```
Where *username* is your account name.

Then;
```
shutdown -r now
```
to reboot.

See if it works.

> **rustyknife said:**
> I can't enter any text into the password bit

Don't worry about that, your not suppose to see anything.

---

### Post by rustyknife on 2008-05-05
With a lucky reinstall (After the 20th time) it is now working normally. :)

Thankyou to those tried to help.

---

