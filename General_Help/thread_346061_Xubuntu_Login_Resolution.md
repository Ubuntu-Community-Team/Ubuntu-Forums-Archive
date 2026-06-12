---
title: "Xubuntu Login Resolution"
date: 2007-01-25
forum: General Help
---

### Post by Gorlist on 2007-01-25
Hi, right quick question in regards to the login screen for Xubuntu. Im finding that its running the monitor at a odd resolution/Hz until I login as a user - this is fine accept its causing on screen artifacts from my poor old onboard graphics card - any suggestions?

I have found the following post: [http://www.ubuntuforums.org/showthread.php?t=173562&highlight=login+screen+resoultion](http://www.ubuntuforums.org/showthread.php?t=173562&highlight=login+screen+resoultion)

Though found it generally confusing.... :(  

Regards!

---

### Post by energiya on 2007-01-25
I wanted to do the same thing so I removed the unwanted resolution from /etc/X11/xorg.conf. If you want to try, don't forget to make a backup of xorg.conf, just in case...

---

### Post by Wim Sturkenboom on 2007-01-25
Your configuration file contains a number of subsections similar to the one show below
```
SubSection "Display"
Viewport   0 0
Depth     24
modes     "1280x960" "1024x768"
EndSubSection
```

The x-server will use the first mode before you login. After login it will use the one that you selected somewhere.
I think that removing the first one for the default depth will probably solve your issue. You will not use it as it will give you artifacts.

---

### Post by Gorlist on 2007-01-25
Thank you for the responses - 

**@Wim Sturkenboom** - Ive now removed the super high resolutions depth 24 - working great.   :D

---

### Post by justifiedandancient on 2008-04-14
Well, I can't tell you the answer but I can tell you that it isn't quite this simple. My xorg.conf had no mention of 1600 anywhere yet that was the resolution of the login screen. My conf file was allegedly a failsafe one and only had entries for 16 bit depth. Now when I logged on I managed to get a sensible screen resolution using the XFCE settings manager. I carried on like this for a while and then decided to see if I could make it better so I added the same resolution entries for 24 bit and voilà! the login screen was the correct (for me) 1280x1024 60Hz. However, once logged in the screen was now set to 1280x960 and the 1280x1024 modes that I could select didn't work as they had refresh rates of 43Hz or lower! So, I edited the conf file again and changed the screen resolutions for the 24 bit depth to be @60 in each case and then I got the correct value for the login screen and was able to reset the logged in display by choosing "default". Now, I'm sure the X gurus will complain that I've used a failsafe config to start with but it wasn't until I installed 8.04 beta that I could get any sensible configuration at all for a 64 bit install.

So, just to reiterate, it is entirely possible for your login screen to use a screen resolution that doesn't appear in your config file. Now that I have a working config file I will save it and maybe try the "proper" package configuration.

---

