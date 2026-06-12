---
title: "flatpak uninstall --unused and flatpak update uninstalls and reinstalls the same soft"
date: 2020-01-18
forum: General Help
---

### Post by ardouronerous on 2020-01-18
_**flatpak uninstall --unused and flatpak update uninstalls and reinstalls the same software**_

I'm running Lubuntu 18.04.

```
~$ flatpak uninstall --unused
Uninstalling from system:
org.freedesktop.Platform.GL.default/x86_64/19.08
Is this ok [y/n]: y
Uninstalling: org.freedesktop.Platform.GL.default/x86_64/19.08
~$ flatpak update
Looking for updates...
Installing in system:
org.freedesktop.Platform.GL.default/x86_64/19.08 flathub 8383da7a813b
Is this ok [y/n]: y
Installing: org.freedesktop.Platform.GL.default/x86_64/19.08 from flathub
[####################] 24 metadata, 55 content objects fetched; 88754 KiB transf
Now at 8383da7a813b.
```

As you can see, _[FONT=courier new]flatpak uninstall --unused[/FONT]_ uninstalls _[FONT=courier new]org.freedesktop.Platform.GL.default/x86_64/19.08[/FONT]_, but when I do _[FONT=courier new]flatpak update[/FONT]_, it reinstalls _[FONT=courier new]org.freedesktop.Platform.GL.default/x86_64/19.08[/FONT]_.

Why is this happening?

---

