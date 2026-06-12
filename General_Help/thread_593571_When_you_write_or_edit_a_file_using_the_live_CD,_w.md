---
title: "When you write or edit a file using the live CD, where does it go?"
date: 2007-10-27
forum: General Help
---

### Post by dwasifar on 2007-10-27
Last night I booted the live CD so I could clone my hard disk with dd.  To find out how long it took to do without sitting and watching it, I put the dd command in a script file followed by a command to write a short file to the desktop; the timestamp of the file will tell me when the  dd completed.

But it brings up something I've been wondering about. Obviously this file that my script is writing is not actually getting written to the live CD.  So where is it going?  Does the live CD create a ram disk?  Does it look at the local hard drive and mount the swap partition if it finds one?  Or is it using ram in some other way?

---

### Post by maybeway36 on 2007-10-27
I'm pretty sure it uses a ramdisk.

---

### Post by aysiu on 2007-10-27
I believe the live CD looks at the local hard drive and mounts the swap partition, but any modifications you make (software installation, file creation, etc.) all get stored in RAM and are subsequently erase upon reboot.

When I create things using the live CD, I usually pop a USB key in and copy those files over to make sure I don't lose them.

---

### Post by Ricardo_V on 2007-10-27
At least for my experience with Knoppix, I think every data you write is lost after reboot. So you better use external storage media for saving your data.

---

### Post by larryfroot on 2007-10-27
Knoppix 5.1 is using a new spanky ntfs tool, the name of which escapes me for the moment. If you have an ntfs partition on the HD knoppix will open files from it, edit those files and save nack to hard drive again** BUT** only if you exit knoppix via the menu...that is you do not just press the reset button or switch the machine off before saving and exiting as you would do a distro on your HD. It is only at the exit emulation that the changes you made are saved to the HD. I am uncertain about FAT 32.  Check out [knopper.net]("http://knopper.net/knoppix/knoppix51-en.html") for more information. Perhaps try it on a piddly little file that would not be missed were it to be sucked into the great laundromat of oblivion?

---

### Post by jflaker on 2007-10-27
all settings are temporary in a ramdisk or a temporary file on the hard disk.......no matter what, the Live-CD is designed to allow USE ubuntu but all changes are lost on reboot.

Best bet is to use an external storage device or all your efforts will be lost

---

### Post by dwasifar on 2007-10-29
Thanks for the answers.  I see I was a little imprecise in the question, as most people took the question to mean I was expecting the files to be persistent.  That wasn't my point; I know they are lost when you end the Live CD session.  I just wanted to know where they live for the duration of the Live CD session.

---

