---
title: "Kazam audio quit after Nvidia card installed &amp; removed"
date: 2015-02-28
forum: General Help
---

### Post by michael-piziak on 2015-02-28
Ubuntu 12.04 LTS

I installed & removed an Nvidia video card.

Before it was installed, Kazam Screencaster worked great.  After Nvidia was installed & after it was removed, both times Kazam will not now record the audio portion of the Screencasts.

The only things I did was 1) I enabled the integrated audio (speaker) in the bios in the Device Options Submenu.  and 2) allowed "Additional Drivers" to install the Nvidia x Server Settings.

I returned the Bios back to factory settings after removing the card.  Perhaps something still installed from Nvidia is stopping Kazam from working now - ?

Also, I deleted Kazam's preferences in the .config folder in an effort to reset it - no luck.

Any ideas how I can get my Kazam Screencaster audio working again ?  Perhaps if I could purge the system of all the Nvidia programs/drivers on it now ?

Update:  I removed & purged Nvidia with help of this webpage, but still no audio in Kazam:  [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

---

### Post by michael-piziak on 2015-03-01
Bump

---

### Post by michael-piziak on 2015-03-01
Solved problem with a program called PulseAudio Volume Control in the Ubuntu Software Center.

Source of solution:  [https://www.youtube.com/watch?v=jeATRDE7LzI](https://www.youtube.com/watch?v=jeATRDE7LzI)

---

