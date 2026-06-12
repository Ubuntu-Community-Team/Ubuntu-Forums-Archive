---
title: "Filezilla closes during connection process (Ubuntu Upgraded to 16.04 from 15.10)"
date: 2016-05-30
forum: General Help
---

### Post by chamira on 2016-05-30
When connecting to a site using the Site Manager, the process begins but the window closes within a few seconds.

I have re-installed the application, and also deleted the .filezilla directory on the home drive, as well as the .config/filezilla/filezilla.xml

When running the application from the terminal I get the following read out:
```
wxD-Bus: Signal from /org/freedesktop/DBus, member NameAcquired
wxD-Bus: Reply with serial 2
wxD-Bus: Reply to RegisterClient, our object path is /org/gnome/SessionManager/Client15
wxD-Bus: CPowerManagementInhibitor: Requesting busy
16:55:27: Debug: Failed to connect to session manager: SESSION_MANAGER environment variable not defined
wxD-Bus: Reply with serial 3
wxD-Bus: Reply: Error: The name org.freedesktop.PowerManagement was not provided by any .service files
wxD-Bus: Falling back to org.gnome.SessionManager
wxD-Bus: CPowerManagementInhibitor: Requesting busy
wxD-Bus: Reply with serial 4
wxD-Bus: CPowerManagementInhibitor: Request successful, cookie is 1412593329
filezilla: relocation error: /usr/lib/x86_64-linux-gnu/libgnutls.so.30: symbol asn1_der_decoding2, version LIBTASN1_0_3 not defined in file libtasn1.so.6 with link time reference
```

---

