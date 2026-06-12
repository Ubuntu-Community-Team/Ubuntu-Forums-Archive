---
title: "No matter what I try I cannot get D6000 driver script to run"
date: 2023-03-01
forum: General Help
---

### Post by theskeptic75 on 2023-03-01
[SIZE=4][FONT=arial][/FONT][SIZE=2]Hi - I'm new to ubuntu forums and also relatively new to linux - hoping someone might have some insight.  I've already googled  this and cannot find anything that seems to work...

I have a Dell XPS 13 7390, and just got hold of a D6000 docking station.  Trying to get my two monitors to talk to my laptop - they are not detected.

After some googling saw that I probably need to the displaylink driver - Ah, I thought, job done.  I promptly downloaded it, and tried to run it - that's when I started making a dent in the wall with my head.

After ensuring the file was executable (right click properties/permissions, also later tried 'sudo chmod +x <filename>), and that I'd installed the dkms framework, double click produces the error
Unknown error code 100
execvp: No such file or directory

'sudo ./<filename>' gave similar error
'[COLOR=#000000]sudo: unable to execute ./<filename>: No such file or directory

So I tried going to root with 'sudo -i' - same error.

Next I checked dependencies (courtesy of another google search) with 'ldd <filename>' - apparently, the file is 'not a dynamic executable'; whatever that means.

Additional info:
I installed 20.04 myself before upgrade
22.04, Kernel 6.0.0
File is [/COLOR][COLOR=#000000]displaylink-driver-5.6.1-59.184.run (which I can provide on request)
[/COLOR]I'm aware that this driver has issues running on 6.0.0, but I did find a work around

Any help at all on this would be very gratefully received - thanks in advance[/SIZE][FONT=arial]
[/FONT][/SIZE]

---

### Post by oldfred on 2023-03-01
Edited *** & font size.

Have you updated UEFI from Dell, not sure if that will also update Dock.
That is now available with Ubuntu.
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
sudo fwupdmgr get-devices
sudo fwupdmgr get-updates
sudo fwupdmgr update
fwupdmgr --version


You may do better with 22.04. Dell is generally good at releasing updates, but they then have to be included in new kernel & then in distributions. Best to use distribution that is newer by a year or so than hardware to avoid most issues.

---

### Post by MAFoElffen on 2023-03-01
You got the official Dell/Ubuntu DisplayLink Drivers from here right? --> [https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu](https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu)

Their installation instructions are here: [https://support.displaylink.com/knowledgebase/articles/684649](https://support.displaylink.com/knowledgebase/articles/684649)

---

### Post by theskeptic75 on 2023-03-02
> **MAFoElffen said:**
> You got the official Dell/Ubuntu DisplayLink Drivers from here right? --> [https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu](https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu)

Their installation instructions are here: [https://support.displaylink.com/knowledgebase/articles/684649](https://support.displaylink.com/knowledgebase/articles/684649)

Yep... that's where I got it from.  Install instructions and release info included in download.

---

### Post by theskeptic75 on 2023-03-02
> **oldfred said:**
> Edited *** & font size.

Have you updated UEFI from Dell, not sure if that will also update Dock.
That is now available with Ubuntu.
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
sudo fwupdmgr get-devices
sudo fwupdmgr get-updates
sudo fwupdmgr update
fwupdmgr --version


You may do better with 22.04. Dell is generally good at releasing updates, but they then have to be included in new kernel & then in distributions. Best to use distribution that is newer by a year or so than hardware to avoid most issues.

Hey ... thanks for your reply - appreciated.  Note I am already on 22.04 kernel 6.0.0 - I wasn't clear in my notes - sorry.

I updated as per your link and command lines above.

Also (to check I wasn't going mad) created and ran 'Hello world' script - no issues.

However, when trying to run the driver script after the recommended updates and restart still getting the same errors and won't run.

Seems clear it's something to do with this particular script and my machine.

---

