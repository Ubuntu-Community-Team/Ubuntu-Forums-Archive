---
title: "I don't want hard drives to appear as logos on desktop"
date: 2007-02-16
forum: General Help
---

### Post by mattgaunt on 2007-02-16
Hey everyone

I have a hard drive with 2 partitions for windows xp and windows vista, and a second hard drive which is for data

I've mounted the data harddrive and it works all ok, but it has an icon that appears on the desktop, i only want the logo to be under my computer, and i dont want the windows hard drive partitions to be seen anywhere in linux.

So . . 
1.)How do i make it so the logo for the 'data' hard drive only appears in my computer?
1a.)(Extra lil bit if possible)Is it possible to change my home folder to be on the 'data' hard drive?

2.)How do i make all logo for windows partitions go away? (Jus delete them from fstab)??

Thanks in advance for any help

Matt

---

### Post by meng on 2007-02-16
alt-f2, gconf
go to apps > nautilus > desktop and uncheck "volumes_visible"

---

### Post by meng on 2007-02-16
1a. Make the mountpoint for your data drive /home, or /home/username, but make sure you back up your existing /home data first, in fact you can move it all to the data drive.
Look here: [www.psychocats.net/ubuntu/separatehome](www.psychocats.net/ubuntu/separatehome)

2. Depends on whether you just want the logos to disappear (see my previous answer) or whether you don't want the partitions mounted automatically at startup. If the latter, then you can delete the lines from fstab (or just comment them out by placing # at the start of the line, then you can change your mind at a later date).

---

### Post by bg1256 on 2007-02-16
If you don't want to change your set up and simply don't want to see your icons, then:

alt+f2, then gconf editor, and follow the steps two posts above this one.  That's the easiest way, and it won't change anything.  It will just remove the icons.

---

