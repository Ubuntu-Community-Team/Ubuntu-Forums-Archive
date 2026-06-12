---
title: "where do i put X -query?"
date: 2005-05-14
forum: General Help
---

### Post by Kamping_Kaiser on 2005-05-14
I wasnt sure if this was a "desktop" thread or an "other" thread, so i went for "other"...

I want to set up an Ubuntu box as a thin client, and i know the command to get a remote x sesion is **X -query servername**, but where do i put it? I couldent find anyware in the config files that looked like where I was shown. All i know is its in an X config file. can anyone help with this?

---

### Post by Kamping_Kaiser on 2005-05-18
I found out were on the IRC channel incase someone wants to know:

/etc/X11/gdm/gdm.conf

its down in the [XDCMP] section iirc. There is some examples in the file (its a big file)

---

