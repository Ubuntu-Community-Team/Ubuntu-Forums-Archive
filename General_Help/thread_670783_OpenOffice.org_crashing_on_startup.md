---
title: "OpenOffice.org crashing on startup"
date: 2008-01-17
forum: General Help
---

### Post by gururise on 2008-01-17
Hey guys,

I'm running Gutsy and I can't start OpenOffice.org.

When trying to run oowriter, I get the following error message:
> Error forking '/usr/lib/openoffice/program//soffice': 'Failed to execute child process "/usr/lib/openoffice/program/soffice" (Bad address)'

The funny thing is, when I run 'soffice', then open office writer starts up fine.

Any suggestions?

---

### Post by laney on 2008-02-01
Bump as I've just started seeing this too. Any ideas?

edit: not just oowriter, all other OO apps too

---

### Post by Hagar Delest on 2008-02-01
First, you can try to rename your OOo user profile (~/.openoffice.org2), a new one will be created with new configuration files.

If there is no improvement, you can try to install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by cdtech on 2008-02-06
Did you ever get this worked out?

I have the same problem with mine, running on 64 but if I type openoffice on a command line it works fine.

I can't use oowriter, oocalc or any other command line shortcut to open, I just get the same error.

I put a custom application launcher on my panel to launch openoffice calling the command line openoffice.

**EDIT:**
I did the "remove all openoffice" from synaptic package manager, renamed and removed my ~/.openoffice.org2 directory.  After I reinstalled using the apt-get install openoffice.org, then I found I could just type openoffice in a terminal to run it.

---

### Post by laney on 2008-02-07
> **Hagar de l'Est said:**
> First, you can try to rename your OOo user profile (~/.openoffice.org2), a new one will be created with new configuration files.

If there is no improvement, you can try to install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Thanks, installing manually like that worked (I had to do --force-architecture to get it to install on amd64, but it seems ok). I'll go back to the Ubuntu versions once hardy releases, but these will do great for now!

---

