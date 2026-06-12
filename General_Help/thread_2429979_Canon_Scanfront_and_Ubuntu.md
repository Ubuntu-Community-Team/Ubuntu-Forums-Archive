---
title: "Canon Scanfront and Ubuntu"
date: 2019-10-25
forum: General Help
---

### Post by dhuscha on 2019-10-25
There was an old thread from 2017 about someone trying to factory reset there Canon Scanfront, in our case it was the 400 series. They were not able to get to the grub menu to follow the service guide, I will include a link to original thread below. 

I figured out that if you live boot from a Ubuntu thumb drive you can mount the SD card and change the grub conf in /boot to show the menu (see option below).

[I]hiddenmenu — Prevents the GRUB menu interface from being displayed, loading the default entry when the timeout period expires. The user can see the standard GRUB menu by pressing the [Esc] key. 

[/I]Comment this out and reboot and you should see grub menu, oh and also increase the timeout. 

Original thread
[https://ubuntuforums.org/showthread.php?t=2379814](https://ubuntuforums.org/showthread.php?t=2379814)

---

