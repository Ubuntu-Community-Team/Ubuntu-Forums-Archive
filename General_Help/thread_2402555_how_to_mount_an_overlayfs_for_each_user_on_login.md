---
title: "how to mount an overlayfs for each user on login?"
date: 2018-10-01
forum: General Help
---

### Post by syadnom on 2018-10-01
I have a java application that I want a number of users on a system to run.  This is a terminal server, so concurrent logins.

The app requires the user to be able to write into the application's directory.  Each user needs their own separate directory else they overwrite each other's data.  I cannot change the operation of the java application.

overlayfs seems the perfect fit.

/opt/Application
/home/user/ApplicationData
/home/user/Application <- overlay of base application and user's own files.

How can I have this automatically mount when the user logs in?

---

### Post by HermanAB on 2018-10-01
I would install multiple copies of the app in a chroot for each user.

---

### Post by syadnom on 2018-10-01
That adds more maintenance and file storage.  It's an option, but if I can get overlayfs or aufs to work on login that's a better fit.

---

