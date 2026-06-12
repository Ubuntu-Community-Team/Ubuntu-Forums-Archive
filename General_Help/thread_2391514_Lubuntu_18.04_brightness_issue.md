---
title: "Lubuntu 18.04 brightness issue"
date: 2018-05-10
forum: General Help
---

### Post by dabbler12 on 2018-05-10
I'm unable to change the brightness level of my laptop. Following an answer to [this]("https://askubuntu.com/questions/1029283/display-brightness-cannot-be-adjusted-18-04/1031529"), I added video.only_lcd=0[COLOR=#111111][FONT=Ubuntu] to [/FONT][/COLOR]GRUB_CMDLINE_LINUX_DEFAULT. It didn't work.

---

### Post by dabbler12 on 2018-05-11
I was able to solve this by adding "acpi_backlight = vendor" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub

---

