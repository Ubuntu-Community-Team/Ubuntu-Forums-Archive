---
title: "Record of booting messages."
date: 2007-07-13
forum: General Help
---

### Post by OldAlgis on 2007-07-13
During booting of ubuntu 7.04 (with gnome desktop) there is at least one warning message, which flashes on the screen, but disappears so quickly that I have not been able to read it.

I expect it is recorded in the logs, somewhere in the /var/log area, but where?  Any direction would be greatly appreciated.

---

### Post by vanadium on 2007-07-13
The command "dmesg" prints the bootup messages. You can output the results to a file

 dmesg > boot.messages

or page though them this way:

 dmesg | less

---

### Post by OldAlgis on 2007-07-13
> The command "dmesg" prints the bootup messages.

Thank you, vanadium.  I had the impression that dmesg gives a lot of booting information, but not all the messages and warnings that appear during the booting process.

Thanks for replying!

---

