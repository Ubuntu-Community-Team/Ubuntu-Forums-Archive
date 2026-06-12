---
title: "Possible to use 1 Gutsy to install sw on another?"
date: 2007-10-29
forum: General Help
---

### Post by jay767 on 2007-10-29
Does anyone know if it's possible to use one gutsy install to "harvest" software and install it on another one?

Here's the situation. My brother & I are both using gutsy but he's stuck with dial up (which isn't even working yet thanks to a compiler error with the modem driver) and I got to thinking it would be convenient to be able take packages, .debs or whatever from my install and install them on his. Just wondering if this is even possible.

---

### Post by maybeway36 on 2007-10-29
You could try AptOnCD, but I'm not sure it gets the dependincies for you.

---

### Post by Maestro23 on 2007-10-29
> **jay767 said:**
> Does anyone know if it's possible to use one gutsy install to "harvest" software and install it on another one?

Here's the situation. My brother & I are both using gutsy but he's stuck with dial up (which isn't even working yet thanks to a compiler error with the modem driver) and I got to thinking it would be convenient to be able take packages, .debs or whatever from my install and install them on his. Just wondering if this is even possible.

Check this link: [http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/](http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/)

---

### Post by IanW on 2007-10-29
I recently managed this trick. But it ONLY works if you're updating the same packages.

1: Run Update manager as normal
2: CD to /var/cache/apt/archive
3: Copy all the debs with the most recent timestamp to a thumbdrive
4: Plug thumbdrive into 2nd PC
5: In a terminal window, enter "sudo dpkg -i /route/to/thumbdrive/*.deb"

---

### Post by jay767 on 2007-10-29
Thanks for the tips! I'll try the AptOnCD approach first. Found a .deb for installing it in /var/cache/apt/archives from synaptic that seems to be a newer version the one on the website. Hopefully it has no dependencies...

Hope it works! Thanks again.

---

