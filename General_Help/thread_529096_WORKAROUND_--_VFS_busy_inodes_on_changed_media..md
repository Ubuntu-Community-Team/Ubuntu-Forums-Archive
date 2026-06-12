---
title: "WORKAROUND -- VFS: busy inodes on changed media."
date: 2007-08-18
forum: General Help
---

### Post by SuperMike on 2007-08-18
Do you have Fiesty and find that, after ejecting a CDROM manually by the button that your /var/log/messages (System Log) starts to flood with the following error?

VFS: busy inodes on changed media.

The workaround appears to be the following two steps, even if you have no CDROM in the drive at this point:

1. Open Terminal
2. sudo eject
3. Let it eject and then push the button on your drive to pull the empty CD tray back in.
4. sudo eject -t
5. exit

By doing this, I found that it stopped flooding the System Log.

---

### Post by apiper on 2007-10-11
I just discovered that this was happening on Dapper. It looks like the problem lies with the Gnome VFS - does anyone know if this has been fixed in the latest Gnome release? I can't find any mention of it in their bugzilla...

---

### Post by nine01a on 2007-10-11
Was happening on Kubuntu 7.10 beta. This worked, though.

I guess I'll just right click eject from my desktop from now on :).

---

### Post by FuturePilot on 2008-02-14
Thank you for this. I just ran into this problem when I couldn't get my laptop's CD drive to open and found my logs being spammed by 20 of these messages every second. Anyways sudo eject worked. :)
From what I've found through searching this usually happens after improperly ejecting a CD (which seems to be what happened in my case after my VM decided to eject my CD](*,)) So I guess just make sure to unmount CDs properly :)

---

