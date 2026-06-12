---
title: "[SOLVED] Permissions in Nautilus"
date: 2008-06-19
forum: General Help
---

### Post by Krydahl on 2008-06-19
I thought that I'd read that PolicyKit in Hardy would mean that if I tried to move a file somewhere I didn't have permission to put it using nautilus, I'd now get a prompt to enter my sudo password. This doesn't seem to be happening for me. Am I missing something or did I just misunderstand this?

---

### Post by siddartha on 2008-06-19
That's probably because you do have admin rights. There is someone out there who should be able to do just that. The other users on the system won't do it as long as they aren't on the sudoers list or admin list.

---

### Post by Krydahl on 2008-06-19
This is a home machine. I'm the only user on it and the account does have sudo rights.

---

### Post by Krydahl on 2008-06-21
Bump.

---

### Post by chrisccoulson on 2008-06-21
This functionality doesn't exist in Hardy. It may be possible to implement something like this in the future with Policykit, but it isn't there yet

---

### Post by Krydahl on 2008-06-21
OK - thanks.

---

