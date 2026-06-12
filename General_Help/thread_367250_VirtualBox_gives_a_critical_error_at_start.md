---
title: "VirtualBox gives a critical error at start"
date: 2007-02-21
forum: General Help
---

### Post by Mochtroid-X on 2007-02-21
I installed VirtualBox on Ubuntu Edgy with all the required dependencies, user permissions, and a restart, but it gives me this error when i try to use it (i dont know the terminal command to run it):

```

Failed to create the VirtualBox COM object.

This application will now terminate.
Callee RC: 0x80004004
```

---

### Post by baobab68 on 2007-02-23
I had VirtualBox 1.3.2 running for a couple of weeks. Upgraded last night and the new version gives me the same error.

I renamed ~/.VirtualBox/VirtualBox.xml to hide it from the app, and now VirtualBox launches. Seems like something was corrupted in there.

I hope this works for you too.

Bao

---

