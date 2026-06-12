---
title: "[SOLVED] Brightness Settings"
date: 2008-05-14
forum: General Help
---

### Post by JustinAlf on 2008-05-14
How do I adjust the settings for my laptop brightness!?  It's fine when it's on AC power, but on battery i can barley see it.  Is there a settings file that I can edit?  There seems like there has to be, becuase it changes when unplugged.  Any help is appreciated.

---

### Post by pointone on 2008-05-14
System > Preferences > Power Management

---

### Post by JustinAlf on 2008-05-14
I thank you for the reply, but isn't that for Gnome?

---

### Post by badfish591 on 2008-05-14
from the command line you can adjust screen brightness with 
```
su -s [enter]
yourpassword [enter]
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness [enter]
```

this will set your screen to maximum brightness, you can play around with it after that by entering different numbers in place of the 100

---

### Post by JustinAlf on 2008-05-15
Upgraded to 8.10 and the function keys for brightnes now work.  Everything is fine now.  But thanks for the replies

---

