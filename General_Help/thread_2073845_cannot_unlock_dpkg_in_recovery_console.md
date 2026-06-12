---
title: "cannot unlock dpkg in recovery console"
date: 2012-10-20
forum: General Help
---

### Post by supernater on 2012-10-20
I made a mistake installing xserver/video/driver and I need to remove the driver.  I booted into recovery mode and dropped to root shell and when I typed

```
apt-get remove fglrx
```

I get...
```

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened
```

How do I fix this?

---

### Post by dniMretsaM on 2012-10-20
Chances are your disk has been mounted as read-only. On the menu that you get in recovery mode, you need to select the [FONT=Courier New]fsck[/FONT] option. That will get you into read-write mode and you can then continue on your merry way.

---

### Post by Merrattic on 2012-10-20
or you may need to use the "sudo" command in front eve3n though you are root ?

---

### Post by dniMretsaM on 2012-10-20
> **Merrattic said:**
> or you may need to use the "sudo" command in front eve3n though you are root ?

Nah, root can preform administration tasks without [FONT=Courier New]sudo[/FONT].

---

### Post by supernater on 2012-10-20
> **dniMretsaM said:**
> Chances are your disk has been mounted as read-only. On the menu that you get in recovery mode, you need to select the [FONT=Courier New]fsck[/FONT] option. That will get you into read-write mode and you can then continue on your merry way.

I did what you said.  When I selected the fsck option and selected yes, I got a blank screen.  There was no command prompt and I couldn't figure out how to get back to that menu to get a root command prompt without rebooting.

---

### Post by steeldriver on 2012-10-20
from the (read-only) root console, you can just execute the following command

```
mount -o remount,rw /
```

(note that there must be no space between the remount and rw options - just a comma)

---

### Post by raja.genupula on 2012-10-20
do this in terminal to clear that 
```
sudo rm -rf  /var/lib/dpkg/lock
```

---

### Post by Merrattic on 2012-10-22
apparently you don't need to use the "sudo" command ;)

---

