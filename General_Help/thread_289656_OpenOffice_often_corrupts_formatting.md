---
title: "OpenOffice often corrupts formatting"
date: 2006-10-31
forum: General Help
---

### Post by silentb on 2006-10-31
I have installed Edgy with OpenOffice 2.0.4-0ubuntu2.

Unfortunately OpenOffice often won't keep the formatting when saving a document as *.odt. Opening the *.odt as *.zip and looking inside styles.xml shows that just the style names are saved, not the information they contain.

I have searched in Ubuntu's and OpenOffice's bug trackers, but I failed to find any relevant bugs.

Am I the only one with this problem?

Saving documents as *.sxw avoids this behavior though it's annoying.

---

### Post by _lynX on 2006-10-31
> **silentb said:**
> I have installed Edgy with OpenOffice 2.0.4-0ubuntu2.

Unfortunately OpenOffice often won't keep the formatting when saving a document as *.odt. Opening the *.odt as *.zip and looking inside styles.xml shows that just the style names are saved, not the information they contain.

I have searched in Ubuntu's and OpenOffice's bug trackers, but I failed to find any relevant bugs.

Am I the only one with this problem?

Saving documents as *.sxw avoids this behavior though it's annoying.

I've never heard of this bug, though I suppose it's possible. Which version are you using?

---

### Post by silentb on 2006-10-31
I use OpenOffice 2.0.4-0ubuntu2.

---

### Post by towsonu2003 on 2006-10-31
I'm using 2.0.4 from openoffice.org (not by ubuntu) and don't have this. so I guess this would be reported to launchpad.net. if you report it, it might be a good idea to attach a before and an after .odt file for demonstration...

try closing OOo, moving your profile ```
mv ~/.openoffice.org2 ~/.openoffice.org2-old
``` and restarting it...

---

### Post by silentb on 2006-10-31
I already tried removing Oo's configuration files. Doesn't help, though :(.

---

### Post by towsonu2003 on 2006-10-31
what about reinstalling it (I mean, all packages related to OOo)? In synaptic, search for "openoffice" in name field and check "Mark for Reinstall" those that are already installed. Not sure if it will work, but nothing to lose :)

you can also file a bug here: [https://launchpad.net/distros/ubuntu/+source/openoffice.org/+filebug](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+filebug)

---

### Post by silentb on 2006-11-01
That's been the first action I took - "apt --purge remove [..]".

It's time to file a bug report.

Thanks for the answers, lynx & towsonu.

---

