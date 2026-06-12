---
title: "Ubuntu 16.04LTS on R3610"
date: 2017-03-05
forum: General Help
---

### Post by digixmax on 2017-03-05
I'd like to try out Ubuntu 16.04LTS on my Acer R3610 but I have not been able to boot into Ubuntu Live on USB -- following selection of the "Default" boot option on the Unetbootin menu the boot started but eventually appears to hang with the screen staying blank.  I tried 2 different USB sticks with same results, and Mint 18.1 booted successfully using the same USB sticks.  It feels like a display related issue (FWIW the R3610 is connected via HDMI to my Onkyo receiver).

Any pointers/suggestions would be appreciated.

TIA.

---

### Post by DuckHook on 2017-03-06
It may be worthwhile booting Mint 18.1 and noting which driver the OS is using. It is likely nVidia's proprietary driver and not Nouveau (the default FOSS driver used by the 'buntus). This will save you a lot of hunting around and trial & error after installation.

To get your LiveUSB working, try the nomodeset boot parameter. Instructions as follows: [https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132) It's an old thread, but the instructions still work. As stated in that thread, you will also need this parameter in your first boot after the system is successfully installed. Your second action after installation (the first would be the whole update/upgrade routine) should be switching to the proper nVidia proprietary driver (the one that you noted Mint is using). Thereafter, nomodeset should be unnecessary.

Available nVidia proprietary drivers are here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

It is possible that your problem is not related to kernel modesetting but is caused by piping your video signal through a receiver. Try connecting the HDMI cable directly to your TV/Monitor to see if this makes a difference.

As a side-note: do you really want to run mainline Ubuntu on that machine? You may find a lighter flavour more responsive. The Xubuntu/Mate/Lubuntu/Budgie flavours are designed to run on such hardware. Of course, if you are happy with the performance, then no need to change, but given your machine specs, I'm surprised you are satisfied with Ubuntu.

---

### Post by gordintoronto on 2017-03-06
Duckhook: +1, +1, +1!

(Nomodeset, direct connection to TV, Mate etc.)

---

