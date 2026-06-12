---
title: "Need computer to detect hard-drive automatically and run script"
date: 2013-03-22
forum: General Help
---

### Post by J-E-N-O-V-A on 2013-03-22
i need to run a script every time i plug in my external hard-drive, but i don't want to have to click a file or paste a command into terminal, how can i make sure the script runs as soon as i plug it in?

---

### Post by steeldriver on 2013-03-22
You could write a udev rule (perhaps based on the idVendor and idProduct ATTRS to uniquely identify the device), and give it a RUN action pointing to your script

---

### Post by tgalati4 on 2013-03-22
Some links:

[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)
[http://hackaday.com/2009/09/18/how-to-write-udev-rules/](http://hackaday.com/2009/09/18/how-to-write-udev-rules/)
[http://ubuntuforums.org/showthread.php?t=1290438](http://ubuntuforums.org/showthread.php?t=1290438)

---

### Post by ManamiVixen on 2013-03-22
Try cuttlefish. It does stuff like that!

[http://www.omgubuntu.co.uk/2012/09/automate-ubuntu-with-cuttlefish](http://www.omgubuntu.co.uk/2012/09/automate-ubuntu-with-cuttlefish)

---

