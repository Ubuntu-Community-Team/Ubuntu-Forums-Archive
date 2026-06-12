---
title: "Ubuntu 6.10 + Beryl problems"
date: 2007-04-04
forum: General Help
---

### Post by charish2k1 on 2007-04-04
This isn't actually for me but this is for my roommate.... he tried to get Beryl working on his Ubuntu. The installation was successful but after he had restarted and tried booting into Ubuntu again (choosing the latest and regular kernel, no recovery mode), it has him in a CLI shell instead of the usual GUI KDE interface. I've looked around on the forums and haven't found anything remotely close. Probably wasn't looking properly, but nonetheless, I haven't found anything. Can anyone help with this?

---

### Post by martinw89 on 2007-04-04
Does X crash at the start?  If so, can you tell us the error message?  If X didn't crash try "sudo /etc/init.d/gdm start" from the terminal it puts him in.

---

### Post by charish2k1 on 2007-04-04
That's the thing though... no error message or anything comes up. It just goes straight into the shell and prompts for a login for your user account on Ubuntu.

---

### Post by Shmifty on 2007-04-04
That means X either crashed or didn't start, a problem with your settings or your graphics card. Please post more information about the system.

---

