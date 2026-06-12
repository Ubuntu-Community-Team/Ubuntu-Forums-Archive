---
title: "Restarting X w/ Ctrl+Alt+Backspace - Questions..."
date: 2007-08-15
forum: General Help
---

### Post by n00buntu NJ on 2007-08-15
Hello all!

Thanks in advance for any help!

My question is this:  when making use of the Ctrl+Alt+Backspace shortcut to restart X, how are the running processes handled?
Are they purged from memory?  Are only certain applications purged from memory (e.g. it seems like services/servers are not affected; such as Samba, FTP, SSH, etc)?

OR, do these active processes need to be explicitly killed?

Thanks for the info!

Best Regards.

---

### Post by ddrichardson on 2007-08-15
Any processes spawned by gdm or x are killed.

---

