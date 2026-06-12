---
title: "Repository help"
date: 2007-03-17
forum: General Help
---

### Post by Commodore Guff on 2007-03-17
Uh, I've never had any problems with Synaptic before, but now whenever I try to reload the list or try to download anything, I get:
```
http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://ubuntu.beryl-project.org/dists/edgy/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://ubuntu.beryl-project.org/dists/edgy/main/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://giss.tv/~vale/ubuntu32/./Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://giss.tv/~vale/ubuntu32/./en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://mirror.home-dn.net/debian-multimedia/dists/stable/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://mirror.home-dn.net/debian-multimedia/dists/stable/main/i18n/Translation-en_US.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
```

Any help would be appreciated.

---

### Post by bapoumba on 2007-03-17
Hello,
are you behind a proxy ?

---

### Post by Commodore Guff on 2007-03-18
> **bapoumba said:**
> Hello,
are you behind a proxy ?

Nope.

---

### Post by bapoumba on 2007-03-18
Well, obviously there is a proxy declared somewhere, and synaptic trying to connect through it.
Please check > System > Prefs > Network Proxy
Or Setting > Prefs > Network in Synaptic
Or /etc/apt/apt.conf file
Or etc/environment
Did you install a proxy before (like Anon proxy) ?

---

### Post by Commodore Guff on 2007-03-18
> **bapoumba said:**
> Well, obviously there is a proxy declared somewhere, and synaptic trying to connect through it.
Please check > System > Prefs > Network Proxy
Or Setting > Prefs > Network in Synaptic
Or /etc/apt/apt.conf file
Or etc/environment
Did you install a proxy before (like Anon proxy) ?

None of that turned up anything.

Yes, I did have that installed, but I removed it.

---

### Post by Commodore Guff on 2007-03-18
Nevermind, a restart got it working again.

Thank you.

---

