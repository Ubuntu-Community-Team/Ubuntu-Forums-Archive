---
title: "screen brightness, bug in 13.04?"
date: 2013-05-02
forum: General Help
---

### Post by nil55 on 2013-05-02
Did a clean install of ubuntu 13.04 (from 12.10) on my Thinkpad edge s430.
When i push my screenbrightness-down key nothing happens except for the indicator on upper right corner appears and just flashes.
When i push the SB-up key the screen brightness turns to the darkest mode and wont go any brighter.

I've come across a few bugs so far and gladly sends a report to developers but this feels more like something I've done.
I didn't have the problem until now, three days after the installation.

heard of this before? ideas what to try/do?
thanks

---

### Post by Frogs Hair on 2013-05-02
I found some questions about the problem on Ask Ubuntu and one pointed to the forums , but you my want to check Launchpad for bugs.

   [http://ubuntuforums.org/showthread.php?t=2139397&p=12621502&viewfull=1#post12621502](http://ubuntuforums.org/showthread.php?t=2139397&p=12621502&viewfull=1#post12621502)

---

### Post by Toz on 2013-05-02
Yes. As per Frog's Hair's link, try the **acpi_osi='!Windows 2012'** kernel boot parameter. /etc/default/grub should look like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```
Don't forget to run:
```
sudo update-grub
```
...to commit the change to the boot loader.

---

### Post by nil55 on 2013-05-03
Thank you Frogs hair and Toz, the !Windows 2012, did the trick. Weird how this just happened out of nowhere...
Thank you

---

### Post by Toz on 2013-05-03
Can you please mark this thread Solved so that others can find it easier and benefit from it? To mark this thread solved:
- Click "Edit Post" on your first post in this thread
- Click on the "Go Advanced" button
- Change the Prefix to "[SOLVED]"
- Click on "Save"

---

