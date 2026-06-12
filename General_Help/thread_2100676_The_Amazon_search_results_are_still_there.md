---
title: "The Amazon search results are still there"
date: 2013-01-02
forum: General Help
---

### Post by trifi34 on 2013-01-02
Even after removing it with this command
sudo apt-get remove unity-lens-shopping

and using the privacy setting and turning it off, I still see Amazon results. I'm trying to remove it.

---

### Post by Calinou on 2013-01-02
Are you sure you actually removed it (no error message when removing the lens package)? Try rebooting or logging out/logging in, too.

---

### Post by trifi34 on 2013-01-02
Yes, and I even went to the software manager and removed it there. Ubuntu must not want me to get rid of Amazon...

---

### Post by JiuJitsu500 on 2013-01-02
Try it in synaptic.

sudo apt-get install synaptic

Then search for amazon. Mark all packages, including the lens for complete removal. The Software Center only removes them, but keeps config files and at times doesn't really do more than disable them. In your case, something odd is going on.

Synaptic is a MUCH more powerful package manager. If you knew all the package names, you could remove them through the terminal. Be careful though, it might say you have to remove other packages when removing amazon packages. That's fine if it's ubuntu-desktop as this is only a meta-package that is useful for upgrading only... but make sure it doesn't remove anything important to you. Post what it says if this is true.

---

