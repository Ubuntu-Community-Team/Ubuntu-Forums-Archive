---
title: "feisty automatix wont install"
date: 2007-04-29
forum: General Help
---

### Post by curtk69 on 2007-04-29
it gives me an error saying i dont have amd64 architceture?
isnt a venice core amd 3000 a 64 bit cpu?

the reason i want the new automatix is to download the 64 bit nvidia drivers since i only have the 386 version now and want a bigger screen resolution than 1024x 768 on my 24 inch screen

will the 64 bit drivers help with this?

---

### Post by taurus on 2007-04-29
You cannot install 64bit app on a 32bit arch.  It's not going to work.  If you need to install nVidia driver for your graphic card, try using envy.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by m.musashi on 2007-04-30
If you are running 32 bit Feisty you don't want (and I doubt it would even work) a 64 bit driver. Your AMD 64 is a 64 bit processor but it is also a 32 bit processor. It basically has both. If you have a 32 OS you need 32 bit apps and drivers. If you have a 64 bit OS you need 64 bit apps and drivers. You can't really mix them (well, okay you can but not well). You should be able to get the highest resolution you graphics card and monitor support using the 32 bit driver. It just might require some tweaking.

As taurus mentions, envy works quite well. I don't have any experience with it in Feisty but it was life saver in Edgy.

You do know that you can install proprietary drivers in Feisty now with just a few clicks. Check under system -> administration -> restricted driver manager

---

### Post by curtk69 on 2007-05-01
musashi, i checked the restricted drivers thing and it says nvida drivers are already enabled.
but i have tried tweaking the resolution with the nvidia software and the highest avaoilable seems to be 1024x768 whixh is kind of a waste on a 24 inche screen

what does envy do that i already havent done or tried??

---

### Post by m.musashi on 2007-05-01
Resolution problems are not my strong point as I've never really had a problem. However, you might need to edit the xorg.conf file to include the resolution(s) you want to use. If you post your /etc/X11/xorg.conf file we can see if that might be the issue.

You can also run
```
sudo dpkg-reconfigure xserver-xorg
```
That will allow you to make changes and select the resolutions you want. Personally, I don't like using it becauase things usually get worse for me. However, if it's not working right then runnig the script might help you to fix it.

I'm not what envy actually does but it has always worked well for me. It is mainly to install the restricted driver but I think it sets things up too. Whether or not it actually detects resolutions I can't say. If there is a feisty version out you could give it a try.

The easiest fix in my opinion is to just edit the xorg.conf file and restart X. If it doesn't work you can undo the changes easily enough. If you run a script it's pretty hard to undo the changes.

I tried to find a good wiki article or something to help but didn't have much luck. You can check this one out though.

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

