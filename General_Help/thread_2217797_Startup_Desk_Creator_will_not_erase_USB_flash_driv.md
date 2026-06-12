---
title: "Startup Desk Creator will not erase USB flash drive"
date: 2014-04-18
forum: General Help
---

### Post by temporos on 2014-04-18
I downloaded the ISO for Lubuntu 14.04, and I'm trying to create a bootable USB flash drive using it. My computer will recognize the flash drive, and when I start Startup Disk Creator, it shows both the ISO file and the flash drive, like it's ready to rock.

Then, I click "erase" to clean off the flash drive first, and it does this.

[ATTACH=CONFIG]252186[/ATTACH]

After closing the error window, the task manager says that the processes *udisks-helper-modify-partition* and *udisks-daemon* are using 100% of the processor capacity, and it won't let me kill them.

The USB flash drive itself is fine. Anyone know what's going on?

Side question, does anyone know where I can get the MD5 hash for this lubuntu release? It's not [here]("https://help.ubuntu.com/community/UbuntuHashes").

---

### Post by temporos on 2014-04-19
Did not find a solution to this, but I did find a workaround.

I needed to reformat the flash drive's partition using Gparted, and then create the bootable disk using Unetbootin. In short, Startup Disk Creator (the one that comes packaged with Lubuntu) is useless.

---

### Post by sammiev on 2014-04-19
Gparted, and Unetbootin works best for me as well. Glad you found a work around.

---

### Post by JLUbunt on 2014-08-29
Glad I read this article. I spent a lot of time trying to use SDC. Thought it was me so bought different brand of usb. With me the options to create the start up disk was permanently greyed out.Will try something else to create one. 
Thanks for posting this.

---

