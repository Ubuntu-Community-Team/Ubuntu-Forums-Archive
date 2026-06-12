---
title: "Login Error."
date: 2006-10-16
forum: General Help
---

### Post by Roasted on 2006-10-16
User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by other users.

How do I fix this? I assume I need to assign 644 octal permissions to the $Home/.dmrc file, and make it read only to user's. But how, exactly?

---

### Post by ayoli on 2006-10-16
try:
```
chmod 0755 ~/
```
and
```
chmod 0644 ~/.dmrc
```

---

