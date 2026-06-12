---
title: "access denied"
date: 2006-12-25
forum: General Help
---

### Post by jasin on 2006-12-25
I get an access denied to /home/jasin/.local/share/Trash/files/
when I try to delete all the contents of the trash bin.

How do I fix this?

---

### Post by cilynx on 2006-12-25
I thought the trash bin was at ~/.Trash   Did they move it on me?

---

### Post by jasin on 2006-12-25
I didn't move it that's where it's telling me it's located when it gives me that access denied error message. I think this is a security restriction. How do I fix this? I am the owner, I have the root password, so there shouldn't be any issues with changing the security settings.

Oh and also, I am on kubuntu not ubuntu, if that makes a difference.

---

### Post by cilynx on 2006-12-25
aha.  I bet it's a KDE thing.  That's out of my scope.  From a command line perspective (and this may very well break KDE is there are pseudo-files in there) you should be able to:
```

sudo rm -rf /home/jasin/.local/share/Trash/files/*

```

---

### Post by jasin on 2006-12-25
That command worked. I did that from the command line as root. it wouldn't show up as deleted until I restarted the computer though.

---

