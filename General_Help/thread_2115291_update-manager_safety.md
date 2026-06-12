---
title: "update-manager safety"
date: 2013-02-12
forum: General Help
---

### Post by lookabout on 2013-02-12
hello, just now update-manager downloaded an update to adobe-flash-plugin.

I watched in fascination as the download progress stuttered, jumped forward and backward, and repeatedly dropped by a few kilobytes, seemingly discarding a few packets for every few it moved forward.  

is there any kind of security built in to these downloads?  is there an md5 check done at various points during the download?  

this particular update could be a huge leverage point for hackers seeking to inject data into an otherwise tight operating system.  aren't graphics drivers kernel-mode and aren't there many reports of safety concerns regarding adobe flash plugins recently?

:popcorn:

---

### Post by snowpine on 2013-02-12
There's some good general info here: [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

Unlike most open-source software provided by Ubuntu, the Flash plugin is a proprietary, closed-source product of Adobe Corp, and there is no particular reason why you should trust it from a security standpoint.

---

### Post by d4m1r on 2013-02-12
I think he means the integrity of the download....And you have nothing to worry about if you are using official repo's/sources. Update manager will rarely (if ever) install a corrupted piece of software, especially one that corrupted during the download.

---

### Post by snowpine on 2013-02-12
I understood the question; if you read the link I provided, it says that apt checks the md5sum of downloaded package files (but only if the repository has been secured with the correct---if not you will see a "WARNING: The following packages cannot be authenticated!" message).

---

