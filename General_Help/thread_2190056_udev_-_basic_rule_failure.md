---
title: "udev - basic rule failure"
date: 2013-11-25
forum: General Help
---

### Post by pouzzler on 2013-11-25
Hello,
I wish to understand udev, please don't suggest alternative solutions. 
I aim to have an udev rule to automatically mount usb drives when plugged, and backup /home on them at the same time. Since even after browsing about 20 tutorials, nothing works in the slightest, I decided to go for an oversimplified skeleton:

seb@lappy:~$ cat /etc/udev/rules.d/95.usbbackup.rules 
ACTION=="add", SUBSYSTEMS="usb", RUN+="/home/seb/Documents/my_backup.sh"

seb@lappy:~$ cat /home/seb/Documents/my_backup.sh 
#!/bin/bash
touch /home/seb/Documents/toto

seb@lappy:~$ ls -l Documents/ | grep my
-rwxrwxr-x  1 seb  seb       42 nov.  17 21:06 my_backup.sh

The my_backup script, which I own, and is in a folder I own only touches a file, for now.
The udev rule (as far as I understand, since it doesn't work one bit), detects a new peripheral, of the usb persuasion, and runs the backup script.

Nothing happens at all, and toto never gets touched. How can I check if the udev rule has even fired? And what other debugging steps do you suggest?

Thanks a lot,
Seb

---

### Post by varunendra on 2013-11-26
Have you read the ArchWiki [documentation]("https://wiki.archlinux.org/index.php/Udev") for Udev? Perhaps you should pay special attention to the "Udisk" part of the documentation. Also, the basics of "[Writing Udev Rules]("http://www.reactivated.net/writing_udev_rules.html")". 

I believe your custom rule is missing a very important part of the rules syntax - 'What' is the rule for. You have defined neither kernel name of the target device, nor its attribs, at least one of which must be provided (as much as I understand). Since the rule doesn't include the device name or attributes to identify it, the udev daemon doesn't know when and where to apply the rule, hence nothing happens.

I am not a udev rules expert and the above is just my assumption based on some very limited knowledge and some quick reading from the above linked wiki page. You may have to do some experiments. Hope the wiki and the additional links on that page can help you.

Good Luck !

---

