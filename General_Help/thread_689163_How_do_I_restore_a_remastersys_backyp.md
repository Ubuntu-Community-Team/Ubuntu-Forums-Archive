---
title: "How do I restore a remastersys backyp?"
date: 2008-02-06
forum: General Help
---

### Post by z0mbi3 on 2008-02-06
As the title says really, I've burnt my backup ISO based on my ubuntu server installation but I can't work out how to install this to the hd.

Can anyone shed some light please?

---

### Post by danwood76 on 2008-02-06
Does remastersys not create a live cd?
Im pretty sure it does, in that case you would just boot from it log in and do a  re installation which will restore your system.

regards,
Danny

---

### Post by Craigus on 2008-02-06
[http://www.remastersys.klikit.org/]("http://www.remastersys.klikit.org/")

---

### Post by z0mbi3 on 2008-02-06
This is what I;m not understanding is how to do the installation bit. Any help would be appreciated.

When I load the live cd I don't get an option for installing, it just wants to load. I guess what I'm basicaly after is how to install from a live disk from the command line.

---

### Post by danwood76 on 2008-02-06
It looks like you have to start ubiquity (the ubuntu installer) you might be able to do alt + F2 then just type ubiquity to start it.

This is where I found it: (same question as yours I think)
[http://loscompanion.com/forums/index.php?topic=2727.0](http://loscompanion.com/forums/index.php?topic=2727.0)

regards,
Danny

---

### Post by z0mbi3 on 2008-02-06
Hmm this isn't much use to me as I don't have X installed.

How can I do it in a command line only enviroment?

---

### Post by danwood76 on 2008-02-06
You have no gui?

Your q would probably be better off asked in the remastersys forums as I doubt many people use that method for backup.
It is possible to just tar your entire system and restore it by doing the opposite, this tends to be easier especially from the command line.

regards,
Danny

---

### Post by BcBuzzard on 2008-03-08
The 'sudo remastersys backup cdfs' command removes the icon for ubiquity from the menus and desktop!

If you do a "sudo apt-get install ubiquity" from a terminal apt will inform you if the ubuntu livecd installer is still on your system and upto date.

To restore a remastersys backup:
load a teminal or press Ctrl + Alt +F1 - F6 (F7 to return to GUI) to get a console.
Login if needed, or type "sudo ubiquity" to load the Live CD Installer.

Ubuntu is the sprit of people working together.

---

