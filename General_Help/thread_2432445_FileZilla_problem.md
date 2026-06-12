---
title: "FileZilla problem"
date: 2019-12-02
forum: General Help
---

### Post by satimis on 2019-12-02
Hi all,

FileZilla problem:

Started Filezilla and selected a directory on local client following warning popup;
```

    A local filename could not be decoded.
    Please make sure the LC_CTYPE (or LC_ALL) environment variable is set correctly.
    Unless you fix this problem, files might be missing in the file listings.
    No further warning will be displayed this session.
    [OK]
```

On Terminal ran;
$ LC_CTYPE="en_HK.UTF-8" filezilla
```

    Reading locale option from /home/satimis/.config/filezilla/filezilla.xml
    Gtk-Message: 18:15:48.231: Failed to load module "canberra-gtk-module"
    wxD-Bus: Signal from /org/freedesktop/DBus, member NameAcquired
    wxD-Bus: Reply with serial 2
    wxD-Bus: Reply to RegisterClient, our object path is /org/gnome/SessionManager/Client26
    gio: file:///home/satimis/Downloads/PRIME-X570-P-ASUS-1201.CAP: No application is registered as handling this file 

```

Please help.  Thanks in advance

Regards
satimis

---

