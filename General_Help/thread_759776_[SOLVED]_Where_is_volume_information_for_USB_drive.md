---
title: "[SOLVED] Where is volume information for USB drives stored?"
date: 2008-04-19
forum: General Help
---

### Post by glibdud on 2008-04-19
Hey folks. I was dinking around with my iPod and the various tools available to talk to it. I didn't like the fact that that it was mounting to the iPod's volume name, which contained a space, so I right-clicked the device on the desktop, clicked Properties, went to the Volume tab, and expanded the Settings section. For mount point, I typed "/media/ipod".

Well, apparently that was a mistake. Though it doesn't give you any warning, it doesn't actually want the "/media/" part of the path. When I ejected the device, unplugged it, and plugged it back in, I got an error complaining about the slashes.

It seems I won't be able to use the same method to change it back, so does anyone know where that information is stored in the filesystem? It's not in fstab, and I don't really have any clue where else to look.

---

### Post by bingoUV on 2008-04-19
Which tool did you finally use which mounted your iPod to its volume name?

---

### Post by glibdud on 2008-04-19
I didn't have to do anything special to mount it on its volume name... that was the default.

I solved this one on my own. I had a sort of "duh" moment a few minutes after I submitted it. I went around with a "grep -r" on a few directory trees and eventually found it. For the benefit of those who might stumble upon this looking for something similar, it is stored here:

```
~/.gconf/system/storage/volumes/_org_freedesktop_Hal_devices_volume_uuid_XXXX_XXXX/%gconf.xml
```

Where "XXXX_XXXX" is (part of?) the UUID of the device. Inside that file you'll find something like:

```
<?xml version="1.0"?>
<gconf>
        <entry name="mount_point" mtime="1208565765" type="string">
                <stringvalue>/media/ipod</stringvalue>
        </entry>
</gconf>
```

That stringvalue entry is what needs to be modified. I changed the "/media/ipod" to just "ipod" and all is well. It didn't work immediately, but after a reboot it's fine. A logoff/login is probably just as good.

---

### Post by prshah on 2008-04-19
> **glibdud said:**
> 
```
~/.gconf/system/storage/volumes/_org_freedesktop_Hal_devices_volume_uuid_XXXX_XXXX/%gconf.xml

```


Or you can access the same information by using the gconftool program. Just FYI.

---

