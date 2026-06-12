---
title: "How to simplify/reset Grub menu?"
date: 2014-04-16
forum: General Help
---

### Post by amanchesterman on 2014-04-16
I'm setting up an old laptop with various Linux distros in order to try them out side-by-side. I have installed Lubuntu, Peppermint and Bodhi in separate partitions: all are working without a hitch and I have no problems using them.
However the Grub menu that appears at startup is a mess. It was fine when I just had Lubuntu and Peppermint, it listed (as I expected) Ubuntu, Peppermint and Memory test. But since installing Bodhi the entries for Lubuntu and Peppermint have been expanded into long strings across the screen. The first one for Lubuntu, for example, begins:
"Ubuntu, with Linux 3/11/0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os 'gnulinux-3.11.0-19-generic-advanced-e6bebbd9-a192- ... etc. etc." (the rest is off the screen). The entries for Peppermint have a similar form although the details are different.

I have tried running *sudo update-grub* but it hasn't made any difference. Is there command which will generate the Grub menu afresh and give me **short** entries for Lubuntu, Peppermint and Bodhi?

---

### Post by su:bhatta on 2014-04-16
a laymans solution:
load Lubuntu, then```
 sudo update-grub
``` & ```
sudo grub-install /dev/sdx
``` , replacing the 'x'.

Then Lubuntu grub will be used and it will reflect a better configuration.

---

### Post by Dennis N on 2014-04-16
Unless you take steps during an installation to do otherwise, the grub from the last OS you install is the one which creates the grub menu you see. When an older version of grub probes for information created by  later versions (which use submenus) during installation, you can get entries like you show in your grub menu.

Solution:

You need Lubuntu to control the boot process. To have that happen, you need to install grub from Lubuntu: use the existing setup to boot into Lubuntu, and then in the terminal run **[FONT=Courier New]sudo grub-install /dev/sda[/FONT]** (assuming your hard disk is designated sda). After that completes, run **[FONT=Courier New]sudo update-grub[/FONT]**.

Reboot and you should get a good grub menu.

---

### Post by amanchesterman on 2014-04-16
Many thanks Dennis N: a clear explanation and an effective solution. I've learned a bit more ... 

Thanks
John

---

### Post by ajgreeny on 2014-04-16
If you want your Lubuntu OS to actually show "Lubuntu 14.04" or something similar to that in the grub menu for the version you have you simply need to edit the /etc/default/grub file as root and change the line 
```
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
```
to read
```
GRUB_DISTRIBUTOR="Lubuntu 14.04"
```Note the required quotation marks.  Now run sudo update-grub again and the menu will now show Lubuntu 14.04, not "Ubuntu etc etc" as it did before for any of the ubuntu family of OSs.

This edit is very useful, and almost essential if you have many different ubuntu family OSs installed on the same system.

---

### Post by amanchesterman on 2014-04-17
Neat, and very useful as you say! Thanks, I have learned even more now. :)

---

