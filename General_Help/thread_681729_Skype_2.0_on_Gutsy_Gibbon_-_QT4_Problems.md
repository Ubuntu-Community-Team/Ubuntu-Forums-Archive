---
title: "Skype 2.0 on Gutsy Gibbon - QT4 Problems"
date: 2008-01-29
forum: General Help
---

### Post by johnnycakes on 2008-01-29
Hi folks. I am super excited at the prospect of video in Skype for linux.

I'm running Ubuntu 7.10 on a Dell D630. Installed Skype from Medibuntu and all the dependencies but when I run skype from the command line I get the following:

skype: symbol lookup error: /usr/lib/libQtDBus.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

I've Googled for over an hour to find a solution but no success... since I don't speak Hungarian!

Any ideas/suggestions? Need any more information?

Thanks,
J.

--

It turns out that another piece of in-house software had installed its own "versions" of the Qt4 libraries. With different headers to those in the version installed with/by the Skype .deb file. Having relocated these altered libs I reinstalled Skype and voila... ca marche.

J.

---

### Post by app on 2008-02-19
Same installation, same problem on IBM Lenovo Thinkpad z60m.

---

