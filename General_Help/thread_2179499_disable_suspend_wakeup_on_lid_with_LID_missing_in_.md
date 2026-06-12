---
title: "disable suspend wakeup on lid with LID missing in /proc/acpi/wakeup"
date: 2013-10-08
forum: General Help
---

### Post by mindpulse on 2013-10-08
Hello! So, I'm running Ubuntu 12.04 LTS on an old (~8 years) Toshiba Satellite P100 (just installed yesterday). When closed, the lid can get jiggled around a little bit, and the locking mechanism for it can easily be slid open - hence, if I put the computer in suspend and place it into a backpack, it often wakes right back up.

I had a look with the command "cat /proc/acpi/wakeup" to see if I could disable the lid as a wakeup entity, but it is not listed.

I then tried adding lid using sudo sh -c "echo " LID" > /proc/acpi/wakeup" , as well as using other names for LID ("LID ", "LID0", etc), but cannot get it to come up on the list. I also tried adding the command to rc.config, but that had no luck either.

Basically, all I want is for my power button to be the only way of bringing the computer out of suspend (and I do want to be able to put it into suspend). Is there any way of doing this given my situation?

Thanks for any help!

---

### Post by varunendra on 2013-10-10
> **mindpulse said:**
> I then tried adding lid using sudo sh -c "echo " LID" **[COLOR="#FF0000"]>[/COLOR]** [COLOR="#FF0000"]/proc/acpi/wakeup[/COLOR]"
I don't know how this is supposed to work, but in the above command, only the "echo" command ran with sudo, the part after ">" as a simple user, so won't be able to write anything in the wakeup file (besides, a single ">" would have overwritten the file if it worked).

You may try-
```
echo "LID" | sudo tee -a /proc/acpi/wakeup
```
..if I understand correctly what you wanted to do with it.

There is an acpi even configuration file "**/etc/acpi/events/lidbtn**" that calls a script "**/etc/acpi/lid.sh**" whenever the lid is opened or closed. You maybe able to modify the configuration file (something with "**action=**") or with the script itself to make it do what you want.

---

### Post by mindpulse on 2013-10-11
Thank you for your help. So, I tried the suggested command but no luck with adding LID to the list. I also tried just having the lid do nothing by removing the call to "/etc/acpi/lid.sh" in "/etc/acpi/events/libtn". 

I then tried manually setting the lid_ac and lid_battery keys using the following command as suggested in: [http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid](http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid)

gconftool-2 -t string /apps/gnome-power-manager/buttons/lid_ac -s "blank"
gconftool-2 -t string /apps/gnome-power-manager/buttons/lid_battery -s "blank"

When that didn't work, I also tried setting IgnoreLid=true in /etc/UPower/UPower.conf

No matter what, if I suspend my computer, close my lid, and then open my lid again, the computer wakes right back up >.<

I read somewhere that apparently there is another handler that catches lid events besides acpi - is there a good way of disabling lid events in that one if it exists?

---

### Post by varunendra on 2013-10-11
> **mindpulse said:**
> So, I tried the suggested command but no luck with adding LID to the list.
As per a post in archlinux forums, it seems the word should be of 4 letters. So instead of "LID", it should be " LID" (a space before "L"), unless your lid switch already has four letters with a number (like "LID0").

Accordingly, please try -
```
echo " LID" | sudo tee /proc/acpi/wakeup
```
..and check if it gets appended to the list.

But I tried some variations here, including above and "LID0", the value doesn't get added to the list at all. There is a similar, but not the same bug report [here]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/250018"), which has been marked as expired now. I think you may file a new bug report as this file is supposed to work as expected.

---

### Post by mindpulse on 2013-10-11
I had actually tried "LID ", " LID", "LID0", and I'm not sure how many other variations, all with no success.

Yeah, I think I'm just going to have to submit that bug report unless I can figure out what else is catching lid events. I checked my bios too, but there's no options for the lid unfortunately.

Thank you nonetheless for the help.

---

