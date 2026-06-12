---
title: "[SOLVED] Oppenoffice icons not in Menu"
date: 2008-05-04
forum: General Help
---

### Post by BandD on 2008-05-04
I recently did a clean install of Hardy, though I copied my /home from Gusty to an external HDD and then copied all the files onto my new Hardy /home.  

But...the thing is that in Gutsy I removed the ubuntu version of OOo because of a SEVERE memory leak in Impress and installed a newer version directly from OOo.  So the hidden file in my /home for OOo is set up for that version, I suppose.  And I think that those settings are not playing nice with the ubuntu version in Hardy.  

OOo will run from the terminal.  But I can't seem to add launchers in the Applications Menu.  Even when I go to Edit Menus, there is nothing for me to check to include OOo.

Is there an easy fix that some one knows about.  I'm not above just un-installing OOo, deleting the hidden OOo file in my home, and re-installing.  However, there are an awful lot of individual packages to un-install and re-install.  So any help would be greatly appreciated!

---

### Post by ErwinC on 2008-05-04
try: Terminal: whereis openoffice      and look for the bin file.
Make a new starter: command: ooffice -writer  (or -calc) etc

Have you installed  a OOo-style/theme via synaptic?

then you select this style in OOo-menu: extra/option/layout or something like that.

---

### Post by BandD on 2008-05-04
I tried un-installing, deleting /home/openoffice.org2, and re-installing but to no avail.  I also tried the theme, trick...no dice!

I have a feeling there is some other config file is hiding somewhere in /home.  But I'm not really sure what it would be.  

Also, I just tried running ooffice -writer in a terminal and I got an error saying
```
bandd@bandd-laptop:~$ ooffice -writer
javaldx: Could not find a Java Runtime Environment!
```

---

### Post by BandD on 2008-05-05
I checked all the packages, and found some OOo java packages that had been skipped.  So I installed those.  

Then I went digging through /home and found some OOo launchers hiding in /home/.local/applications.  I opened up the Menu Editor and dragged those laungers to the Office section and now everything is hunky-dory.

---

