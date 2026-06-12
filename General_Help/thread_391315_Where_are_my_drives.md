---
title: "Where are my drives?"
date: 2007-03-23
forum: General Help
---

### Post by phaedo5 on 2007-03-23
Sometimes when I restart Ubuntu Edgy I only have one drive.  Linux only recognizes the Linux partition.  All my other drives and partitions are no where to be found.  

I don't know what info to put here.  I really don't know where to even begin.  After a couple of restarts or so, the drives reappear.  I don't know what is up.  

Any ideas?

---

### Post by Muzik83 on 2007-03-23
Something like this occasionally happens on my system when the filesystem (JFS) doesn't get uncleanly mounted.

Next time it happens, try going to a command prompt and typing:
sudo mount -a
which means "mount all drives that are supposed to be mounted on boot"

You should either end up with your drives mounted correctly (and if so I have no idea why it didnt do that on boot), or an error message...which would be most helpful in trying to diagnose the problem ;)

-sean

---

### Post by phaedo5 on 2007-03-23
Ok.  That makes sense.  I did that.  And got this.

[I]Failed to mount '/dev/disk/by-uuid/42A86672A866647F': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run 'ntfsfix' on Linux unless you have Vista, then mount NTFS with
   the 'force' option read-write, or with the 'ro' option read-only.[/I]


Is there any danger of running ntfsfix and force mounting?

---

### Post by Muzik83 on 2007-03-23
Sorry, I don't have any NTFS drives, so I cant say for sure what to do.  Perhaps someone else will have some advice :)

-sean

---

