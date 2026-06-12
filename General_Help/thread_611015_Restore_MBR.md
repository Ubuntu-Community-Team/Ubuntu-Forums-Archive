---
title: "Restore MBR"
date: 2007-11-12
forum: General Help
---

### Post by PurposeOfReason on 2007-11-12
So I have an old Vaio that I need to see that had Ubuntu and XP on it. For obvious reasons, I need to remove Ubuntu and GRUB. That was easy enough but when I boot a XP CD for recovery mode, it asks for a andministrator password. I never set one so I tried to leave it blank. At the moment I can't boot into anything. Is there a way to restore the mbr with a live cd?

Or if there is a way to just install GRUB, I guess that would work too.

---

### Post by ddrichardson on 2007-11-13
Not to restore the Windows MBR without a backup copy from Linux there isn't. Only from the recovery console in Windows - for which you need an Administrator password. There are however live cd available to break administrator passwords - which I wont go into on a public forum, google will point you right though.

---

### Post by taurus on 2007-11-13
Try [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

---

### Post by PurposeOfReason on 2007-11-13
I guess I did it the hard way. I reinstalled linux and GRUB. Booted into windows and changed the password and then deleted linux and fixed the mbr.

---

### Post by rbmorse on 2007-11-14
That's actually the easy way.  There are *other* ways to do it, but they are harder and take almost as long.

---

### Post by bodhi.zazen on 2007-11-14
LOL

the "easy way" is to book a knoppix CD

Open a terminal, enter : ```
 sudo install-mbr /dev/hda
```

You can do it from the Ubuntu live CD:

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

---

