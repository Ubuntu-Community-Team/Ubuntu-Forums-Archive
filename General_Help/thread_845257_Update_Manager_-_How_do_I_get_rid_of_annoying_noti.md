---
title: "Update Manager - How do I get rid of annoying notifications?"
date: 2008-06-30
forum: General Help
---

### Post by bruparel on 2008-06-30
I had apt-get installed a number of ruby related libraries and packages which  I apt-get removed and built from the source and custom-installed in a different location than installed by the apt-get package manager.

The update manager however, keeps insisting that an update is available for the ruby package(s) that I have already removed.  How do I stop it from telling me that?  At the same time, I do want to get other upgrade notifications so that I can keep my system up to date.

For example, it is telling me that an update is available for Ruby 1.8 p 36 whereas I have built from source and installed Ruby version 1.8.6 p 111.  Apparently, the apt-get uninstall did not do too well and the Update manager still thinks that I have Ruby (and other related packages and libraries) still on my system.  They are, but not under the Update Manager's control since I hand installed them?

I would love to be able to get rid of update messages that I don't want and at the same time keep getting auto updates for other packages.

Thanks.

Bharat

---

### Post by y-lee on 2008-06-30
You can probably lock the troublesome packages. Locking the version on a package prevents it from being upgraded. To do from the GUI open Synaptic and find the packages you wish to lock and click Package > Lock Version. :)

Hope this helps.

---

