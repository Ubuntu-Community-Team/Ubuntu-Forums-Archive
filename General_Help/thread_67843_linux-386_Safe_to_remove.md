---
title: "linux-386: Safe to remove?"
date: 2005-09-21
forum: General Help
---

### Post by zugvogel on 2005-09-21
Hi - Can anyone tell me if is or is not safe to remove the package "linux-386"?

The background to this is that I'm trying to remove the already-present madwifi drivers as suggested by this thread: [http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)

It suggests to remove the "linux-restricted" packages, and in order to do that synaptic also wants to remove "linux-386". I want to just make sure that linux-386 isn't some crutial package (after all, I don't want to uninstall the OS linux!)

Thanks.

---

### Post by skoal on 2005-09-21
Zugvogel, I believe the 'linux-386' is just a meta-package, whose basic purpose is just to have the following packages as dependencies, so they get installed: linux-image-2.6.*, linux-image-386, linux-restricted-modules-*, linux-restricted-modules-386, and nvidia-kernel-common.

All the packages which end with '386' (in your case here) should just be meta packages, which basically pull in the real deal (like 'linux-image-2.6.*', ...).

* So, to answer your question, it should be safe to remove this 'linux-386'.  I only run a custom kernel, so I cannot try it out myself first.  Worst case, just see what Synaptic says it will uninstall first before you actually say "ok". There should be a list for you to read.

\\//_

---

### Post by zugvogel on 2005-09-21
I think you're right and it is a metapackage as you describe. I have now uninstalled it and haven't had any problems.

Many thanks.

---

