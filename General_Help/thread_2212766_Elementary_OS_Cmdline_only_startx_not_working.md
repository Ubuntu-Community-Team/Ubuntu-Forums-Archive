---
title: "Elementary OS Cmdline only startx not working"
date: 2014-03-23
forum: General Help
---

### Post by UltimateCat on 2014-03-23
I ran the cmd to uninstalling the amd driver and than rebooted. ( just wanted to install the new amd driver)
Well...upon rebooting it's a black screen so I tried cmdline (Ctrl+Alt+F2) to login.
That worked. So once I was logged in I tried startx.

I don't have the gui just this error-
```
failed to load 'gnome'

```

What can I do to fix this?

---

### Post by UltimateCat on 2014-03-26
Found out that this was a driver issue.

After uninstalling the amd-catalyst driver and the fglrx driver and a reboot the system was up and running again.

Found the new fglrx and the amd-amdcccle drivers in the repo. Just have to install them-

---

