---
title: "High CPU usage playing video content, Thinkpad X201"
date: 2015-06-17
forum: General Help
---

### Post by merlin8 on 2015-06-17
Dear all,

Just a general observation: when playing video content (e.g. YouTube) with Ubuntu 14.04 LTS on a Thinkpad X201 the CPU usage is typically well over 50% - causing the machine to become very warm and noisy.  In Windows 7 on the same hardware for the same video the CPU usage is typically much less than 10%.  I assume this is a hardware acceleration issue, but I have installed the Intel HD graphics driver for Ubuntu and it seems to have no effect/improvement.   So why is Ubuntu so much less efficient than Windows?  I note that this presumably has implications for battery life as well.  The tests were conducted playing HTML 5 content in Google Chrome.

Thanks

---

### Post by tgalati4 on 2015-06-18
Some hardware acceleration features for Chrome were turned off because they would cause graphics lockups.  

Open a Chrome browser and type in:  chrome://settings

Type in *acceleration* in the Search box.  Make sure "Use hardware acceleration when available" is checked.

Also examine the settings of chrome://gpu (you have to type it in a new browser window).  There's a lot of stuff there and I don't know a fraction of it.

Some suggestions:  [http://ubuntuforums.org/showthread.php?t=2259882](http://ubuntuforums.org/showthread.php?t=2259882)

I'm not sure what graphics chip is in an X201.  Perhaps post the output of:

```
lspci | grep VGA
```

If it works in Windows, then you can generally get the same performance in Linux, but you have to manually configure things because many hardware features are turned off by default because of reliability issues over several platforms.

If you are feeling lucky, you can enable a bunch of experimental flags which will improve graphics performance.  Take careful notes and change one at a time then play a test video.  I believe you need to restart Chrome after each change.  Look at chrome://flags

---

