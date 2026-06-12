---
title: "Increased boot time if SD-card inserted"
date: 2013-04-30
forum: General Help
---

### Post by holzi on 2013-04-30
Normally my WeTab needs 30s to boot but if an SD-card is inserted it takes several minutes. Does somebody have an idea how to fix that?

---

### Post by gordintoronto on 2013-04-30
Is this with Ubuntu or MeeGo?

What happens if you insert the SD card after booting?

---

### Post by holzi on 2013-05-01
I have installed Ubuntu 13.04. When I insert the SD-card after booting it works normally.

---

### Post by coldraven on 2013-05-01
I don't know the WeTab but presumably you installed Ubuntu using a card or stick. Is it still set to boot from USB first?
Does it even have a boot order BIOS type of thing?

---

### Post by holzi on 2013-05-01
Hm, I didn't change anything but for some reasons I can't reproduce the problem at the moment. My tablet is booting everytime at fullspeed now no matter if the SD-card is inserted or not. 

But it didn't seem to be an issue with the bios. It was set to boot from the internal SSD. When the problem occured my tablet needed much time between the time after the bios-logo when the screens turns dark lila and the login screen.

---

### Post by JebusWankel on 2013-05-01
Ubuntu runs periodic file system checks every couple (27 last I remember) boots. This might be helpful [https://wiki.ubuntu.com/BootCharting]("https://wiki.ubuntu.com/BootCharting")

---

### Post by Rebelli0us on 2013-05-01
When this happened to me it was a defective card reader. Have you tried a different reader?

---

### Post by holzi on 2013-05-01
Hm while trying to get an external monitor over the hdmi-connector to work I experienced extreme boot time. After deleting all files I created for this purpose (hdmi still didn´t work) the boot time was normal again.

I attached bootcharts from before and after removing my modifications.

Seems like it wasn´t my SD.

---

### Post by holzi on 2013-05-03
Okay, now I get the feeling that Ubuntu is trying to mock me. Yesterday it booted in 30s with SD.Card, today it needed 3 minutes. Then I removed the card and suddenly it only needed 30s again. 
Why has my Ubuntu such an inconsistent booting behavior?

Edit: Now it gets even more confusing. I rebooted with the card and needed 30s again.

Edit2: I think I know now the circumstances of this bug. It allways happens when the tablet was shut down for a longer time (for example the hole night) and an SD-Card is inserted and repeats itself as long as the Card inserted while booting. If I remove it and reboot the bug doesn´t appear even in following reboots.

---

