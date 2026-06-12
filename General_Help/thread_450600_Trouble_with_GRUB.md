---
title: "Trouble with GRUB"
date: 2007-05-21
forum: General Help
---

### Post by Axldust on 2007-05-21
I hope you can understand my english (not very good)

Hi, i have a problem and i hope you can help me to solve, 

i have 2 hard drives, 
one HD its ntfs (with 3 partions, one whit windows XP, the other 2 for any kind of file)
the other HD its with ubuntu 6.10 (where i am now)

i installed ubuntu, and restart... my problem is when GRUB loads to start ubuntu, i press ESC to see list of operatin systems but theres not options to load WINxp, and i want to acces it, and i dont know what to do, so i really ask you for help, and thanks since now.

Excuse me if i dont write very well.:(

---

### Post by spin2cool on 2007-05-21
1) backup your menu.lst file
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

2) add a line something like this to the list:

```
title   Windows XP
root    (hd0,0)
makeactive
chainloader     +1
```

Change the details appropriately.  For example, many dells come with a diagnostic partition as the first one, so instead you'd use:
```
title   Windows XP
root    (hd0,1)
makeactive
chainloader     +1
```

Or you might have it on another harddrive:
```
title   Windows XP
root    (hd1,0)
makeactive
chainloader     +1
```

---

