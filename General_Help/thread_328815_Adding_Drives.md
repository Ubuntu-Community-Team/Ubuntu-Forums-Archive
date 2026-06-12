---
title: "Adding Drives"
date: 2006-12-31
forum: General Help
---

### Post by Raptor45 on 2006-12-31
When I installed 64bit edgy it failed to detect my NTFS partitions. I got around this by editing fstab, and although I can now access the drives through /mnt/, Edgy doesn't provide the normal links to them. What I mean is under "Computer" or "Places" or on the Desktop, I don't see the links to the drives that would normally appear automatically. How can I get them back?

Also, for some curious reason I have two floppy drives detected where there should only be one. fstab only has one listed, but in /media/ there is an extra "floppy" shortcut which links to floppy0, the actual drive. Under "Computer" and "Places" both are listed. Whats the best way to fix that? 

Thanks for the help!

---

### Post by skale on 2006-12-31
There's nothing to fix.  There is *supposed* to be a link with the floppy drives, because some apps can use either, and this way the apps that look for /media/floppy will still run.

In fstab, check the options for the drive.  it should have a defaults or auto or something.  Post that one.

---

### Post by Raptor45 on 2006-12-31
OK, I won't worry about the floppy stuff then.

```
/dev/hdd1	/mnt/hdd1/	ntfs 	auto,users,ro,umask=0222,utf8=true 0 0
/dev/hdc3	/mnt/hdc3/	ntfs 	auto,users,ro,umask=0222,utf8=true 0 0
```

Those are the two drives I added. They read fine, Ubuntu just doesn't give them all the links in the right places. Not a real technical problem, but an issue of convenience I'd like fixed.

---

### Post by Rab22 on 2006-12-31
> 
Also, for some curious reason I have two floppy drives detected where there should only be one. fstab only has one listed, but in /media/ there is an extra "floppy" shortcut which links to floppy0, the actual drive. Under "Computer" and "Places" both are listed. Whats the best way to fix that?


The issue with the floppy maybe similar to mine. I had two floppy drives showing up as, "Floppy Drive" and "Floppy 1".

Inside /etc/fstab, you may notice there is a line:
```

/dev/        /media/floppy0  auto    rw,user,noauto  0       0

```

Change that line to read
```

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Try that a see if it resolves your floppy problem. :)

> 
Those are the two drives I added. They read fine, Ubuntu just doesn't give them all the links in the right places. Not a real technical problem, but an issue of convenience I'd like fixed.


I'm not 100% positive, but I believe they must be mounted under /media/ for GNOME to associate icons with them in Computer/Places.

I would try changing your fstab file to give them file references there.

Best of luck with it!

---

### Post by Raptor45 on 2007-01-01
Right you are! It had to be in /media I guess, thank you very much!

---

