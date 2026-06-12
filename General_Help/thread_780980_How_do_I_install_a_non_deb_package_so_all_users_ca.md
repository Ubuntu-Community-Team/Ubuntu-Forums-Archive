---
title: "How do I install a non deb package so all users can access it?"
date: 2008-05-03
forum: General Help
---

### Post by 3pinner on 2008-05-03
I have downloaded and unpacked a 3rd party application.
Properties show it to open with application/x-shellscript.

Where (or how) do I install this app so all users on my computer can access it?

Thanks!

---

### Post by warp99 on 2008-05-03
> **3pinner said:**
> I have downloaded and unpacked a 3rd party application.
Properties show it to open with application/x-shellscript.

Where (or how) do I install this app so all users on my computer can access it?

Thanks!
Prefix the script with 'sudo' and install the application to '/usr/local' since that's the default location for third party applications to be installed per Debian guidelines.

---

