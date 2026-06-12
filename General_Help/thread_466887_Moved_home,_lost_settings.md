---
title: "Moved /home, lost settings"
date: 2007-06-07
forum: General Help
---

### Post by 50words on 2007-06-07
I just moved my /home directory to a separate partition using this tutorial ([http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)). However, when I restarted, all my settings were gone. I had to re-download my Firefox extensions, re-enter my e-mail account information in Evolution, etc.

I didn't lose any actual data, but I want to make sure that this doesn't happen again if I have to re-install Ubuntu at some point. How can I get those settings back?

---

### Post by EndPerform on 2007-06-07
It sounds like the hidden configuration directories didn't get copied over correctly.  You can check this by typing:

```
ls -a
```

in a terminal from your home directory.  For Firefox, the settings are under /home/username/.mozilla, and I'm not sure where Evolution stores it's configuration info.  If you still have the backup you made from the tutorial you followed, you might want to compare the output of ls -a of the backup vs. your new home directory to see what is missing, if anything.

---

### Post by ajgreeny on 2007-06-07
I'm not sure what the link you showed says about moving /home but if you moved all the folders and files from the original /home folder to the new /home partition using the gui of nautilus, did you make sure you had asll the hidden files and folders showing?  If not all your config info will have been left behind in the old home. If you've still got it you could now move them all as well as your documents which have already been moved.

---

