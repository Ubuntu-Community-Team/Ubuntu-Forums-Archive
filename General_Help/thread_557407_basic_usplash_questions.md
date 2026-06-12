---
title: "basic usplash questions"
date: 2007-09-22
forum: General Help
---

### Post by rybu on 2007-09-22
Hi, I've been fussing about with usplash, trying to get a reasonably appealing boot-up "look". 

One thing I recently noticed is that usplash only works on my system in 800x600 8-bit mode.  Is this a common issue, that it will work in very few (one!) mode(s)?   I've got an NVIDIA card capable of quite a variety of modes.  It's strange that 800x600x8 is the only thing usplash can handle on my system.  I do not have these problems on my other laptops that have much older ATI cards.

I've been using the "StartUp-Manager" app to configure my boot process.  Setting a background image for grub is very easy.  Setting up one for usplash is a bit pain.  There seems to be no way to determine if a configuration will work without trying it out, rebooting, and seeing if you get anything more than a blank screen.  I've been following the instructions here:

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

It explains how one starts with a .png file, convert it to a .c file using BOGL, which you then compile into a .so file which usplash can (hopefully) use.  

IMO it would make sense to have a utility that could read these .so files, and tell you basic information about them.  In particular, do some basic checks on them to ensure they will work.  

Anyhow, I'll see if I can get a custom 800x600x8 screen working.  If anyone knows why other resolutions aren't working for me, I'd love to know.  Especially if there's a way to use a higher resolution.

Edit: I must be making some kind of mistake during compilation because I recently got the "fingerprint" splash screen to work in 1280x1024x8.

---

### Post by Vadi on 2007-09-25
Well, I tried a usplash-switcher from getdeb.net, but that one gives a seg fault as soon as it starts up.

The only usplash theme I know if the finger print one, still trying to get it working...

---

