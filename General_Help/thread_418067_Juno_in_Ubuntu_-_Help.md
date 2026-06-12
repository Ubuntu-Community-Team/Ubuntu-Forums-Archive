---
title: "Juno in Ubuntu - Help?"
date: 2007-04-22
forum: General Help
---

### Post by austinwolfclaw on 2007-04-22
I downloaded and installed Juno for Linux....it is a .deb file. Yet, the file in in /root/desktop and i think i have to be root, i thought. So i created the run program as root script. Nothing.  I checked the code, to see if everything was right, and it was...

how can i get this thing (juno) up and running?

~austinwolfclaw)

---

### Post by hikaricore on 2007-04-22
This thread may help:

[http://ubuntuforums.org/showthread.php?t=365295&highlight=Juno](http://ubuntuforums.org/showthread.php?t=365295&highlight=Juno)

It talks about simply copying the .desktop file the Juno package installs on /root/Desktop to your current user account's Desktop folder.

```

sudo cp /root/Desktop/FILENAMEHERE.desktop ~/Desktop

```

Then:

```
sudo chown YOURUSERNAME ~/Desktop/FILENAMEHERE.desktop
```

Replacing the capitalized text with whatever it really is.

Edit: From my understanding you may also need to have java installed for Juno to work, but try this first before jumping into that.  :)

---

