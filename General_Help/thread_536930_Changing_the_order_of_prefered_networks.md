---
title: "Changing the order of prefered networks"
date: 2007-08-28
forum: General Help
---

### Post by Dylnuge on 2007-08-28
Hello,

A few weeks ago, my internet went out, and I connected to a hotspot near my house. Now, whenever I start the computer, it connects me to that unsecure, poor signal, hotspot. I don't have access to network printers or anything. I searched around, but the only post on this I found was in the development forums.

How do I change the order of automatically logged onto networks in network manager?

Thanks,
Dylan

---

### Post by Dylnuge on 2007-08-30
...Anyone?

---

### Post by Dylnuge on 2007-08-31
Please?

It really sucks that such a feature was implamented, complete with auto connect, and no one knows how to use it. After all, short of asking the hotspot to rename/secure/remove their network, I don't really have an option. Someone programmed this in, could they help?

---

### Post by Dylnuge on 2007-09-04
Look, this is getting to be a joke. I know enough about computers to understand that there is a way that the computer knows to log onto the hotspot because I chose to. The computer does not just remember it-either it is contained in a file or inside a config or log for the applet itself. Either way, I can edit this file and remove the refs to the hotspot. All I need to know is what file it is!

Please help.

---

### Post by dumbmatter on 2007-09-06
i don't think there is a way to give networkmanager an order, unfortunately.  you can make it forget about the other network though.

first stop gconf:
```
gconftool-2 --shutdown
```
then go to ~/.gconf/system/networking/wireless/networks/ and there should be a folder for every network you have connected to.  delete the one that is giving you trouble.

---

### Post by Dylnuge on 2007-09-06
Hmm...

I did that, but it still reconnects to the last one I used (the hotspot) if I am in range. There was no auth or anything, so maybe the files there were not needed?

---

### Post by dumbmatter on 2007-09-06
i don't really know the logic it uses to connect to networks.  it seems like it likes unsecured networks for some reason

 if you delete the network from gconf, it won't auto-connect to it until you manually connect to it.  but after you manually connect, you will have to delete it again or it might decide to start auto-connecting again.

---

