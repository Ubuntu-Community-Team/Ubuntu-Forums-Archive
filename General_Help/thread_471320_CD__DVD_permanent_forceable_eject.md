---
title: "CD / DVD permanent forceable eject"
date: 2007-06-11
forum: General Help
---

### Post by SonicSteve on 2007-06-11
Hi there,
I'm not sure the title quite says it. I want to be able to press the eject button on my DVD drives / CDrom drives and have them eject with a disc mounted in them.
I know there was a file somewhere in the file system that could be edited (not fstab) that would do this. I can't find the thread though.

Does anyone know what I'm talking about?

Edit;
I should add that when you make the change in whatever file it is you always receive the "unsafe device removal" message. So whatever the file and change is it circumvents this feature.

---

### Post by SonicSteve on 2007-06-12
OK so I found a thread that contained this info problem solved

Here it is,
sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'

The secret was in the sysctl.conf file, what's even better is that in dapper adding this line would give you the "unsafe device removal" message. Now in Feisty it doesn't I now have the best of both worlds.

---

