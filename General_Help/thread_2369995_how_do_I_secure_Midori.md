---
title: "how do I secure Midori?"
date: 2017-08-29
forum: General Help
---

### Post by ardouronerous on 2017-08-29
I'm playing OpenMW and I tend to surf the web as I play the game, however, using Firefox along with OpenMW really zaps the RAM, so, I looked into and installed Midori and I noticed a big difference in memory usage, so I'm now using Midori with OpenMW.

But how I secure Midori? What addons do you recommend?

Thanks.

---

### Post by LastDino on 2017-08-29
There are number of extensions included by default, may need some enabling them though (if I remember correctly). Like ABP and NoJS. 

Might want to look into in how to build personal filters as well. 
[https://wiki.archlinux.org/index.php/Midori](https://wiki.archlinux.org/index.php/Midori)

I'm not sure if you can use "firejail" with your setup as I don't know what OpenMW is, or how it works. 

That is usually more than enough security most casual user need. If you need more, I believe there is also options for userscrips, but I never tinkered with it to give suggestion on it.

---

### Post by ardouronerous on 2017-08-29
OpenMW ([https://openmw.org/en/](https://openmw.org/en/)) is a video game, it's available in Ubuntu's repos, but the version in the repos is outdated, so I'm using a PPA to keep it updated.

I've tried Adblock Plus and NoJS, they are like uBlock Origin and NoScript in Firefox, but how do I add more lists to ABP in Midori?

In Firefox, other than uBlock Origin and NoScript, I also use Ghostery, HTTPS Everywhere and Privacy Badger, is there any equivalents in Midori?

I also use AppArmor in Firefox, any there a AppArmor profile for Midori?

---

### Post by vasa1 on 2017-08-29
> **ardouronerous said:**
> ..., any there a AppArmor profile for Midori?

If you can't find any you can always make your own profile. There's an apparmor how-to somewhere in the Security subforum.

---

### Post by vasa1 on 2017-08-29
[RM: midori -- RoQA/RoM; FTBFS, unmaintained and unsupportable]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=864951") found via [https://www.qwant.com/?q=apparmor%20midori&t=all](https://www.qwant.com/?q=apparmor%20midori&t=all)

---

### Post by ardouronerous on 2017-08-29
Okay, so Midori isn't safe to use because it's unmaintained? Any other lightweight alternatives available in the Ubuntu repos?

I've tried Dillo, but it doesn't load the sites that I want to go to unfortunately.

---

### Post by vasa1 on 2017-08-29
Qupzilla is now called Falkon. Try the appimage first: [https://ubuntuforums.org/showthread.php?t=2355301&p=13619371#post13619371](https://ubuntuforums.org/showthread.php?t=2355301&p=13619371#post13619371)

---

### Post by ardouronerous on 2017-08-29
I have never installed an Applmage before.

What about the one available in Ubuntu repos? Any problem with it?

---

### Post by vasa1 on 2017-08-29
> **ardouronerous said:**
> I have never installed an Applmage before.

What about the one available in Ubuntu repos? Any problem with it?Did you look at the link I provided?

---

### Post by ardouronerous on 2017-08-29
Yeah, so the QupZilla in the repos is outdated.
What's the difference between installing through AppImage and PPA?

Since I've never installed through AppImage, I'd rather install through PPA.

Is the PPA mentioned in the thread still valid, since it's a PPA from 2011?

---

### Post by vasa1 on 2017-08-29
> **ardouronerous said:**
> ...
Is the PPA mentioned in the thread still valid, since it's a PPA from [SIZE=6]2011[/SIZE]?
You've been here long enough and surely have enough knowledge to know the answer to that from a "security" angle even if installing that ppa is possible!

---

### Post by ardouronerous on 2017-08-29
How about Epiphany? Is that as lightweight as QupZilla?
Is the one available in the repos any good?

---

### Post by vasa1 on 2017-08-30
> **ardouronerous said:**
> How about Epiphany? Is that as lightweight as QupZilla?
Is the one available in the repos any good?

The best answer would be provided by your experience on your system with your usage. I used Epiphany a long time ago. Maybe it's more functional now :)

---

### Post by ardouronerous on 2017-08-30
Okay, I'll be testing Epiphany and OpenMW later, thanks

---

