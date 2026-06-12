---
title: "How can I add screen resolutions to xorg.conf?"
date: 2008-04-26
forum: General Help
---

### Post by atomkarinca on 2008-04-26
I tried reconfiguring xserver-xorg but no avail. I tried [this thread]("http://ubuntuforums.org/showthread.php?t=83973") first:

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

Then I installed the nvidia drivers and nvidia settings manager, but there is only 640x480 resolution. Last I tried changing xorg.conf manually but it just crashed.

Does anyone have any other ideas?

---

### Post by sailor2001 on 2008-04-26
> **atomkarinca said:**
> I tried reconfiguring xserver-xorg but no avail. I tried [this thread]("http://ubuntuforums.org/showthread.php?t=83973") first:

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

Then I installed the nvidia drivers and nvidia settings manager, but there is only 640x480 resolution. Last I tried changing xorg.conf manually but it just crashed.

Does anyone have any other ideas?

/usr/share/applications/screen & graffics

---

### Post by atomkarinca on 2008-04-26
> **sailor2001 said:**
> /usr/share/applications/screen & graffics

Thanks mate, that worked like a charm.

---

### Post by colinnwn on 2009-01-04
can anyone elaborate?  I have no screen or graphics folders or files in /usr/share/applications

---

