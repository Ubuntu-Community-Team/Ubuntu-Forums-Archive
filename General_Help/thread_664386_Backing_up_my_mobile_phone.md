---
title: "Backing up my mobile phone"
date: 2008-01-11
forum: General Help
---

### Post by mercmobily on 2008-01-11
Hi,

I bought a fantastic Nokia 6233. I am sooo happy!
I would like to backup my address book, sms messages, calendar and TODO list.

I am going insane... I got Bluetooth to work, and I can "mount" the phone like this:

sudo obexfs -b 00:1B:AF:F8:44:8B -B 10 /mnt/phone

Which is pretty need.

However, I cannot backup the "real" stuff...

Does anybody know what my options are?

Bye!

Merc.

---

### Post by erginemr on 2008-01-11
Hello,

Check out the following thread, and the details of the program "wammu" given there, which I believe, is precisely what you need:

[http://ubuntuforums.org/showthread.php?t=623645](http://ubuntuforums.org/showthread.php?t=623645)

Synaptic also has it in the repositories. The download with all dependencies is quite bulky but Nokia 6233 is listed as supported in their web page, so it is worth a try.

---

### Post by jken146 on 2008-01-11
Wammu or Gammu (I think gammu may be just a GTK frontend for wammu) should be what you need.  I've used gammu myself and it works a treat.

---

### Post by erginemr on 2008-01-11
> **jken146 said:**
> Wammu or Gammu (I think gammu may be just a GTK frontend for wammu) should be what you need.  I've used gammu myself and it works a treat.

Just vice versa: In spite of the preceding G, Gammu is the backend, Wammu is the Gnome front end.

---

### Post by mercmobily on 2008-01-11
Hi,

WOW< wammu is a NICE piece of software... THANK YOU!

Has anybody experienced a problem where not ALL sms messages are retrieved?

I might go and file a bug report...

Bye,

Merc.

---

