---
title: "AMD Driver for laptop with switchable graphics card"
date: 2016-09-16
forum: General Help
---

### Post by sryii on 2016-09-16
I am currently at my wits end trying to figure this out.  All I want to do is be able to use my darn graphics card!

My setup:
HP pavilion dv6
Radeon HD 6730M
Ubuntu 16.04 LTS(fresh install with dual boot to windows 7)

I have looked up multiple guides and attempted to install something to get my graphics card to work.  

BinaryDriverHowTo on the ubuntu documentation page said to install fglrx, get error that says it doesn't exist
Same guide try to install drivers from AMD which gives me a zip file for some reason.  Tried to run the file the installer says I need to install the required pre-requisites for package generation and then directs me to a .log file that doesn't exist.

Tried the switcheroo guide, nothing happens when I try to change things.

Can someone please help me figure out what to do next?

---

### Post by QIII on 2016-09-16
Hello!

What is your CPU/APU?  Is there an integrated graphics controller and the HD 6000 series is the dedicated?  Can you turn off the integrated in your BIOS.

With 16.04, fglrx is no longer available, so the guides you find for installing it will not work -- and may even make a mess.  It's probably time for me to edit the community wiki and direct 16.04 users to appropriate help.

---

### Post by sryii on 2016-09-16
Oh yes sorry! It is an Intel i5 with and Intel integrated graphics (sandy bridge 3000).

Unfortunately I can't switch off the integrated graphics. I am only change it from dynamic to fixed, neither of which means off.

---

### Post by QIII on 2016-09-16
Ah.  So we are in marshy territory here.

With the withdrawal of support for fglrx from AMD regarding the X Server version used in 16.04 (moving to the open source AMDGPU driver and the new and improved open source Radeon driver), switching between the two in a hybrid setup is something for which I have not yet found a solution.  

With 16.04 and your AMD GPU, the Radeon driver would be what you would use -- it would have been installed with Ubuntu had the AMD GPU been the one active at install time.

I'm still hunting for info on this one.

---

### Post by sryii on 2016-09-16
Thank you for the help.  I'm not really committed to 16.04. Would installing an older version of Ubuntu solve the problem?

---

### Post by QIII on 2016-09-16
14.04.3 or earlier should be good.  The version of fglrx works and it includes functionality for switching.

In either 14.04.4 or .5 you will start getting components that will cause trouble.

---

### Post by sryii on 2016-09-16
Okay I will give that a try.  I will update if that works.  Thanks for your help!

---

### Post by sryii on 2016-09-19
Okay quick update.  Well I installed 12.04 LTS and found that the system thought my graphics card was unknown even though I could see with terminal commands.  So I carried on and installed with the initial instructions in BinaryDriverHowto/AMD and that ran into a problem with amdconfig command.  Then I tried the instructions found here:

[https://ubuntuforums.org/showthread.php?t=1930450](https://ubuntuforums.org/showthread.php?t=1930450)

that are actually specifically for older versions of Ubuntu.  It got hung up on 

```
[COLOR=#000000][FONT=&quot]sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise[/FONT][/COLOR]
```

saying that there was no valid html link and it can't be build.  Ok, so I moved back to the BinaryDriverHowto/AMD and did a manual install of 13.4 for switchable graphics cards.  But after all that I tried launching steam and it said OpenGL was not able to be used to launch the app, which I can only guess means that the drivers didn't find my card or installed something that didn't work properly.  Any other options or ideas?  Thanks again for all the help!

---

