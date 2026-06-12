---
title: "Need to run Azureus as root from Kubuntu KMenu"
date: 2007-05-01
forum: General Help
---

### Post by Aikanar on 2007-05-01
Hello,

I am relatively new to Kubuntu, my friend has been using Ubuntu for about and year and finally convinced me to switch. For the most part, I like it better than any other OS or distro I've tried, but I have a persistent problem with Azureus that is ruining my enjoyment of an otherwise excellent user experience.

The problem is two-fold.  Azureus cannot update its files when an update is due from sourceforge because of lack of permissions, and (even more vexingly) neither can it start new torrents on the FAT32 partition without failing, also for lack of permissions.  I have done all the usual fixes I can find to get around this: setting /opt/azureus to root ownership, enabling the FAT32 incremental write option within Azureus, even installing libraries (via Automatix) to write to FAT32 and NTFS partitions, all without sucess.  The only "magic bullet" is to run Azureus as root.

That is easily done from a terminal -- the problem is that I want it to be selectable directly from the KMenu in the graphical environment.  Working in a GUI is both a preference and (in my case) a necessity (I have motor control issues with my fingers and make *many* typos).

I have tried the advice here:

[http://www.askdavetaylor.com/how_can_i_hide_passwords_in_a_shell_script.html](http://www.askdavetaylor.com/how_can_i_hide_passwords_in_a_shell_script.html)

and modified my sudoers file to add my ordinary account name, and I have written a little shell script:

> #!/bin/sh
sudo  /opt/azureus/azureus

in an attempt to do this, but no luck yet.  This script launches, but does not appear to do anything -- it certainly does not launch Azureus, even though I can do so from the terminal with the same command.

Hopefully, someone here will be able to help me out.

---

### Post by gazj on 2007-05-01
I presume you know how to edit you kmenu, alter the entry for Azureus to read

kdesu /path/to/azureus

save changes, hopefully this will work.

kdesu is sudo's graphical equivilent, this is used to launch all the other programs in kubuntu as root.

---

### Post by Aikanar on 2007-05-01
It works perfectly, thank you. :) 

Now, is there any way to assign the Azureus icon to torrent files?  I uninstalled Ktorrent, but its icon is still associated with all *.torrents.

{If you would would prefer I post this as a separate question, that's fine.}

---

### Post by gazj on 2007-05-02
hmm, unfortunately haven't got a kubuntu installation in front of me, using ubuntu at the moment, and can't remember the procedure in kubuntu.  Glad i was of help with your original problem though.

---

### Post by Aikanar on 2007-05-02
Just found it myself:

1) Right-click and choose 'Properties' from the contextual menu.
2) Click on the Wrench and Screwdriver icon (Edit File type) in the dialog that appears.
3) Click on the image of the file icon.
4) Click the radio button "Icon source from other locations" (i.e., not a system icon).
5) Browse to where the icons for Azureus are (in my case /opt/azureus) and select the one for torrent files.

---

