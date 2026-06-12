---
title: "Kubuntu Thunderbird date format"
date: 2007-10-29
forum: General Help
---

### Post by be4truth on 2007-10-29
Hello Everybody,
I need some help.
I have 2 Gutsy Kubuntu installations and migrated one Thunderbird box from Windows XP to Kubuntu  and one Thunderbird  from Fedora5 to Kubuntu.
On both machines I can't get the format of the date inside Thunderbird changed. I tried everything in this link without success [http://kb.mozillazine.org/Change_the_Date_Format]("http://kb.mozillazine.org/Change_the_Date_Format")

Any idea how to get the weekdays off before the date of the emails? Any help is appreciated.

---

### Post by firoozyves on 2007-11-06
Try to solve it by using a script. You need to set the LC_TIME environment variable before launching Thunderbird. First find the correct value for LC_TIME by using the following command:

Code:
locale -a

This should display a list from which you can select the correct locale. Remember to use the entire name including the postfix. Second create a script like the following example:

Code:
#!/bin/sh
# Launches Mozilla Thunderbird with European formatted dates.
export LC_TIME=en_GB.utf8
env DISPLAY=:0 thunderbird %u

Change en_GB.utf8 to what ever you prefer. Save the file with [name].sh and make it executable using chmod.

Finally, you need to change the Launcher Properties:
Right click on the Thunderbird icon, select properties; go to the command line; Browse to the directory where you located the above script; select it; close; launch it!

Hope this will work

---

### Post by be4truth on 2007-11-22
I moved both machines to Ubuntu as there were more problem with this kubuntu version. In Ubuntu non of the problems would occur.
Thx for the help.

---

