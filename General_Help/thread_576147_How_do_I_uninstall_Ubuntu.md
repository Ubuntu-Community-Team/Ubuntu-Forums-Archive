---
title: "How do I uninstall Ubuntu?"
date: 2007-10-14
forum: General Help
---

### Post by Heous on 2007-10-14
This may draw some flak from die-hard Ubuntu users, but I want to uninstall it.  I'm a PC gamer, so Ubuntu will never be able to replace Windows as my primary OS, and I installed it on an extra hard drive I had lying around to see how it worked.  I haven't used it in a long time and I want to uninstall it and use it to store more Windows applications.  My current configuration is a dual-boot system on a Dell Dimension 8400.  It isn't a partitioned hard drive, it's two hard drives each devoted to one operating system.  I want to wipe clean the hard drive that has Ubuntu on it and then format it as a secondary drive in Windows XP.  If anybody can help me do this or direct me to the proper instructions I would gladly appreciate it.

Edit:  I forgot to mention that I don't have the original Windows boot disc or a floppy drive on my computer.

---

### Post by Atzu on 2007-10-14
hmm maybe using the live CD gnome partition editor to delete ubuntu partition ?

---

### Post by fdrake on 2007-10-14
sudo apt-get remove ubuntu.

just kidding . Just boot with the live cd and delete all the partitions with GParted and then boot with the windows installation. you know you can dual boot keeping both your os?

---

### Post by strabes on 2007-10-14
> **fdrake said:**
> sudo apt-get remove ubuntu.

just kidding . Just boot with the live cd and delete all the partitions with GParted and then boot with the windows installation. you know you can dual boot keeping both your os?

You don't need the windows CD for this. Just make it a fat32 partition with the ubuntu cd or the Gparted CD.

---

### Post by bodhi.zazen on 2007-10-15
You may need to restore the MBR ...

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

EDIT: Oh, i see you do not have a windows disk , LOL

You can restore the MBR from linux, you can use the Ubuntu live CD or Knoppix :

Ubuntu : 1. Boot live CD, open a terminal.

	2. Enable The Universe repositories (System->Administation->Software Sources : tic "Community maintained Open Source software (universe)"

	3. Install  ms-sys
		```
sudo apt-get update && sudo apt-get install ms-sys
```

	4. Restore MBR
		```
ms-sys -w /dev/<drive>
```
		<drive> = your windows hard drive (/dev/hda)

	* you might need to ms-sys -p or ms-sys -w /dev/<partition>

	How to : [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)
	man page : [http://linux.die.net/man/1/ms-sys](http://linux.die.net/man/1/ms-sys)

Knoppix :

Open a terminal and type ```
sudo install-mbr /dev/hda
```

You may need sudo install-mbr /dev/sda depending on your hard drive ....


HTH

---

