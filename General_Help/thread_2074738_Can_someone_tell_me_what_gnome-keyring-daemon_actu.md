---
title: "Can someone tell me what gnome-keyring-daemon actually does?"
date: 2012-10-22
forum: General Help
---

### Post by SteveDeFacto on 2012-10-22
I changed the permissions so it can't execute and I've had no noticeable changes occur. I can type in my password to unlock things the same as usual. I don't understand what it is actually for?

---

### Post by Paqman on 2012-10-22
You might find a problem if you tried to do stuff like connect to a wifi network. Your keyring holds the passwords for stuff like wifi and encryption. You could keep it disabled if you like, but by definition it's a trusted core component of your OS so should normally be running.

---

### Post by 2F4U on 2012-10-22
Read this as a starting point:

[http://en.wikipedia.org/wiki/GNOME_Keyring](http://en.wikipedia.org/wiki/GNOME_Keyring)

---

### Post by SteveDeFacto on 2012-10-22
> **2F4U said:**
> Read this as a starting point:

[http://en.wikipedia.org/wiki/GNOME_Keyring](http://en.wikipedia.org/wiki/GNOME_Keyring)

Yeah, I've read that but applications don't appear to be storing passwords in it. It does not appear to have any use as far as I can tell but I guess what Paqman said is probably the main use for it.

---

### Post by Paqman on 2012-10-22
> **SteveDeFacto said:**
> applications don't appear to be storing passwords in it.

Gnome apps will, others won't.

---

