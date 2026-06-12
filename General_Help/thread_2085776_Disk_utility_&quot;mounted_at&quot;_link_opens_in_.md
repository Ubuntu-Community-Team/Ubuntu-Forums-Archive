---
title: "Disk utility &quot;mounted at&quot; link opens in Firefox"
date: 2012-11-19
forum: General Help
---

### Post by cbraxton on 2012-11-19
This is in Xubuntu 12.04 - I'm finding when mounting a volume with Disk Utility, when clicking on the "mounted at" link it opens up in Mozilla Firefox instead of the Thunar file manager, which is something of an annoyance. Anyone have a way to fix this? (I have not been able to find anything in the Settings Manager.)

---

### Post by carl4926 on 2012-11-19
I'm not using xubuntu
But try right clicking the mounted link > properties

---

### Post by cbraxton on 2012-11-19
> **carl4926 said:**
> I'm not using xubuntu
But try right clicking the mounted link > properties

Thanks, but in Xubuntu when you right-click on the link all the choices you get are "open link" and "copy link address" - nothing about properties. I'm assuming that somewhere buried in the Xfce configuration there's someplace to set the handler for file links, but I have not been able to find it...

---

### Post by rai4shu2 on 2012-11-19
Disk Utility?

Why the need to manually mount things, for that matter?

---

### Post by LewisTM on 2012-11-19
That's probably because the file:// URI scheme is associated with a web browser instead of a file manager. It should not by default but who knows what happens when you install apps, upgrade, etc.?

Open file ~/.local/share/applications/defaults.list

Add these lines:
> [Default Applications]
x-scheme-handler/file=exo-file-manager.desktop
Logout/login. Hopefully it should work now. You can test it with 
```
exo-open file:///
```
Note: The file ~/.local/share/applications/mimeapps.list might also contain associations that could conflict with your settings. In theory defaults.list overrides mimeapps.list but better keep it clean.

Cheers!

---

### Post by cbraxton on 2012-11-20
Thanks for the ideas. I added the suggested entry to ~/.local/share/applications/defaults.list, and executing "exo-open file:///" does open up Thunar. However, the file link in Disk Utility still opens up in Firefox!

I also checked in ~/.local/share/applications/mimeapps.list, but the only web browser references therein are associated with http and https links:

```

[Default Applications]
application/x-cd-image=vlc.desktop
application/vnd.oasis.opendocument.spreadsheet=libreoffice-calc.desktop
application/x-wine-extension-inf=leafpad.desktop
text/plain=leafpad.desktop
video/x-msvideo=parole.desktop
application/octet-stream=leafpad.desktop

[Added Associations]
application/vnd.oasis.opendocument.spreadsheet=libreoffice-calc.desktop;
application/x-wine-extension-inf=leafpad.desktop;
text/plain=libreoffice-calc.desktop;leafpad.desktop;
application/x-cd-image=vlc.desktop;
video/x-msvideo=parole.desktop;
application/octet-stream=leafpad.desktop;
x-scheme-handler/http=exo-web-browser.desktop
x-scheme-handler/https=exo-web-browser.desktop

```

It's not that big a deal, I don't open up file links in Disk Utility very often but this is one of those little annoyances/glitches that just bugs me. (I believe this started after installing the Opera web browser, after doing that the links started opening up in that. After uninstalling Opera the links started opening up in Firefox.)

---

