---
title: "Unistalling grub without windows xp cd"
date: 2007-11-19
forum: General Help
---

### Post by APMT19 on 2007-11-19
Howdo I uninstall grub without the windows cd? is there a program?

---

### Post by taurus on 2007-11-19
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by bodhi.zazen on 2007-11-19
From the Ubuntu Live CD:

	1. Boot live CD, open a terminal.

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

----------

From Knoppix :  sudo install-mbr /dev/hda

----------
See also Windows Boot Disk:
	[http://support.microsoft.com/kb/305595/EN-US/](http://support.microsoft.com/kb/305595/EN-US/)

---

### Post by Cannonball003 on 2008-01-20
> **bodhi.zazen said:**
> From the Ubuntu Live CD:

	1. Boot live CD, open a terminal.

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

----------

From Knoppix :  sudo install-mbr /dev/hda

----------
See also Windows Boot Disk:
	[http://support.microsoft.com/kb/305595/EN-US/](http://support.microsoft.com/kb/305595/EN-US/)

Ok so would I do this before or after I delete the ubuntu partions in windows?
also this works for Windows XP Pro right?

---

### Post by bodhi.zazen on 2008-01-20
> **Cannonball003 said:**
> Ok so would I do this before or after I delete the ubuntu partions in windows?

Does not matter, you can do it all from a live Ubuntu CD.

> also this works for Windows XP Pro right?

Should work just fine. If not post any problems.

---

### Post by Cannonball003 on 2008-01-20
> **bodhi.zazen said:**
> Does not matter, you can do it all from a live Ubuntu CD.



Should work just fine. If not post any problems.

Thanks for the help.

Can anyone confirm the windows xp pro thing because I heard the mbr is different?

---

