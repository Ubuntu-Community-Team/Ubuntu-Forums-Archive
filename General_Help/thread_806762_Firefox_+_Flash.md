---
title: "Firefox + Flash"
date: 2008-05-25
forum: General Help
---

### Post by Nim-X on 2008-05-25
Hi i have to click this in order to play the flash files in Firefox, how  to disable this?

[IMG]http://img167.imageshack.us/img167/421/flashshitmz0.jpg[/IMG]

thanks in advance

---

### Post by Sarah L on 2008-05-25
All flash files should load automatically with a webpage.
What you have posted here looks like something from a video site, such as Youtube or Metacafe. The start button is part of the Flash "applet's" design and has nothing to do with Firefox.

---

### Post by NilsE on 2008-05-25
Like Sarah L said most video sites will provide the start button..  Some don't so try this one and if it starts immediately then your browser is working normal.

[http://www.albinoblacksheep.com/flash/numa](http://www.albinoblacksheep.com/flash/numa)

---

### Post by Nim-X on 2008-05-25
> **NilsE said:**
> Like Sarah L said most video sites will provide the start button..  Some don't so try this one and if it starts immediately then your browser is working normal.

[http://www.albinoblacksheep.com/flash/numa](http://www.albinoblacksheep.com/flash/numa)

lol

nope, it doesn't start automatically, i have to click it

maybe its a plug in but i cant find it in the list of my plug ins

---

### Post by scizzo on 2008-05-25
This sounds like the security plugin from the site of firefox where it asks the user everytime it wants to start a flash application in the browser.

[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

That plugin.

---

### Post by Nim-X on 2008-05-25
i havent installed that or any of them

well, i did but it is deinstalled, so i HAD Flashblock installed, but it is apparently still active

it does not appear in my plugins or add-ons list

i guess it's not deinstalled properly

---

### Post by YETI.ru on 2008-06-11
Hi. I have the same problem and it's not FlashBlock. I never installed flashblock but after reading this thread i did and i had to press two times on each flash file for it to play. It's obviously something that Shockwave Flash plugin does and i want to know if there's a way to configure it.

---

### Post by meshuggahner on 2008-06-11
I had the same problem - happened when trying to fix the sound in flash videos. This what I did:

- Removed any installed flash plug-ins with Synaptic
- Re-installed flash as suggested in another thread:
> **pedro_orange said:**
> Don't bother with that

```
sudo apt-get install ubuntu-restricted-extras
```

Let that do it for you.

That fixed the video loading, but still had problems with sound. I then followed the [How To: The (almost) Perfect Pulse Audio Setup]("http://ubuntuforums.org/showthread.php?t=776739") to fix the sound problem.

Hope this helps.

---

