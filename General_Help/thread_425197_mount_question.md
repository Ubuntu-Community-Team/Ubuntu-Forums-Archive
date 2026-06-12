---
title: "mount question"
date: 2007-04-27
forum: General Help
---

### Post by andrei048 on 2007-04-27
Hello! I'm an ubuntu newbie and I have a little problem, 
I want to read/write my NTFS partiton, and i want this to be enabled at start up.

# Entry for /dev/sda5 :
UUID=241C70481C701750 /media/sda5 ntfs-3g defaults,locale=en_US.UTF-8 0 1

this is how my fstab looks

the partition is not mounted automatically. And, if i mount it with sudo, I cannont acces is becaut I'm not root.

Also, how can i put this partion on the desktop, as is was?

The partion was originally mounted, but was unmounted and dissapeared from the desktop when i activated read/write on the ntfs 3 g tool.

Thanks for future help.

---

### Post by Pox on 2007-04-27
Try this.

UUID=241C70481C701750 /media/hda5     ntfs-3g    defaults,locale=en_US.UTF-8,nls=utf8,umask=007,gid=46 0       1

That's a modded version of my line, and it's automounted on startup and is accessible by all users. Hope that helps :)

---

### Post by andrei048 on 2007-04-28
I did that, but absolutly no change. If i go to /media/sda5 there is absolutly nothing there. I really want to be able to write to that NTFS partition because it is the largest space on my laptop.

---

### Post by Compyx on 2007-04-28
Try changing the "/media/hda5" in Pox' post to "/media/sda5", that might help. Can't test this myself, haven't used Windows/NTFS for over 5 years now.

---

### Post by andrei048 on 2007-04-29
I found the problem. I also have on my computer Windows XP, and when i don not shutdown windows, but hibernate it, Ubuntu can't mount my NTFS partions.
After I have "cleanly" shot down windows it works fine.
Thank you for the help.

---

