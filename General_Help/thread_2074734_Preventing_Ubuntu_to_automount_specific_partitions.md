---
title: "Preventing Ubuntu to automount specific partitions"
date: 2012-10-22
forum: General Help
---

### Post by _asc_ on 2012-10-22
Hello,

I have a dualboot configuration with Windows 7 and Ubuntu 12.10. The Windows 7 partition is automatically mounted and shown in the Launcher and in Nautilus. Since I do not need to access the Windows partition from Ubuntu, I want to prevent it from being mounted. I looked at /etc/fstab, but there is no entry for the Windows partition. 

How can I prevent partitons from being automounted?

---

### Post by kc1di on 2012-10-22
Not sure but this thread may be of help

[http://askubuntu.com/questions/165702/how-can-i-prevent-ubuntu-from-mounting-particular-partitions-deivices]("http://askubuntu.com/questions/165702/how-can-i-prevent-ubuntu-from-mounting-particular-partitions-deivices")

---

### Post by grahammechanical on 2012-10-22
Open the Dash and type Disks. Use that utility. Be careful. The dash ( **-** ) icon will delete any partition selected.

Select the partition and click the icon of 2 cogs meshed together and select Edit Mount Options. There you will find a slider called Automatic Mount Options. Move it to the Off position.

See if that solves it.

Regards.

---

### Post by Cheesemill on 2012-10-22
I don't think it is being automounted.

Available devices are shown in Nautilus and the Dash but they are only actually mounted when you click on their icon.

Do you just want to hide the unmounted device in Nautilus and the Dash instead?

---

### Post by _asc_ on 2012-10-22
Hello again,

I tried it with the Disks utility, like grahammechanical suggested. In addition to switching "Automatic Mount Options" to off, I had to uncheck the options "Mount at startup" and "Show in user interface" and that did the trick.

Thank's a lot for all your answers!

---

