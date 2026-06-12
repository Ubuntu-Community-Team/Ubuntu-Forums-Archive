---
title: "Weird Graphics &amp; sound problems with New PC"
date: 2015-11-17
forum: General Help
---

### Post by typos1 on 2015-11-17
I ve just got a Gigabyte Brix A8-5545. I set it up on my 32" 1080p Samsung tv with HDMI. 

It worked fine after installing, although the graphics were pretty bad - the rendering of the desktop was appalling, but the resolution was correct and I got sound. I tried the proprietary AMD driver, but although it appeared to install, whenever I tried to open Catalyst it didnt open and I got a message saying the driver isnt installed. So I went back to the open source driver.

Anyway, I moved it to my 24" 1080p Samsung monitor/tv (still using HDMI) and the resolution was 800x600, with no other option in "displays" and the monitor was not being detected. I checked the drivers and the open source one was not installed, even though I didnt un install it. Plus, the proprietary drivers options were greyed out and so was the open source one, it also said a manually installed driver was being used, even though I didnt install one ! 

So I looked for a way to change the resolution, I went into Xdiagnose and tried one of the workaround options the first one worked - disabling PAT memory solved it - a reboot started in a higher resolution and more resolution options appeared in "displays" - I checked the 1080 one and the picture is great - far better than it was on the 32" Samsung. The monitor was not still detected though, I just got the extra resolution options.

And I still get the greyed out options for installing any graphics drivers, including the open source one. 

You could argue it doesnt matter as the picture is now pretty good, but a did get some dropped frames on a quick youtube test . . . which also resulted in no sound. In "sound" there is nothing in the "play sound through" box (there was something in there on the bigger Samsung screen and the sound did work). Under the input section the built in audio shows up, but not for output. I installed pulseaudio and the HDMI/Display Port section says "unplugged" even though it isnt.

I m stumped, can anyone help ?

Thanks

---

### Post by typos1 on 2015-11-19
More problems - after rebooting again it hung on the Ubuntu screen, I managed to get it to boot by going into recovery. This time it was back at 800x600 res with no other options and the open source drivers were installed (again I did not install them and they werent showing as installed before the reboot). I installed the proprietary drivers again. 

Now it still wont boot and I cant manage to make it boot normally using recovery as I did before, going into root shell prompt I tried to update but got a message about some problem with the Wily source an it stuck at 0%. Updated via terminal on my old pc (15.04) using the same internet connection and it worked ok.

Not sure whats going on can anyone help ?

---

### Post by mastablasta on 2015-11-19
what GPU chip? which drivers are now installed? any strange messages in dmesg? have you tried purging proprietary driver and then do a manual driver install?
more information needed other than listing the events: [URL="http://ubuntuforums.org/showthread.php?t=1422475"]http://ubuntuforums.org/showthread.php?t=1422475
[/URL]Binary drivers AMD how to: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

fglrxinfo says what?

any kind of display needs drivers. they can be opensoruce or fglrx. it coul dbe that something went wrong during fglrx install (e.g. corrupted file on transfer) and then it didn't install well.

---

### Post by typos1 on 2015-11-19
Its an HD 8510 G, cant find anything of help on google.

I know any display needs drivers and I ve tried the open souirce and the flgrx, but I m confused how they seem to install themselves if I just change the display. 

I re-installed the flgrx drivers as they werent greyed out after the second re-boot, but still have the problem and cant boot at all unless I go into recovery. 

But the point is on the smaller display I get these problems with either the open source or flgrx, but not on the larger one, even though the resolutions are the same.

---

### Post by typos1 on 2015-11-22
Solved it all by re-installing 15.10 whilst connected to the 24" Samsung, all went well, including the installation of the AMD/ATI proprietary driver. 

Cant understand why there were those problems when installing whilst connected to the 32" Samsung, but all fine now. 

The no sound through HDMI was tunred out to be volume on monitor set to "0", cant remember turning it down at all, but hey.

---

