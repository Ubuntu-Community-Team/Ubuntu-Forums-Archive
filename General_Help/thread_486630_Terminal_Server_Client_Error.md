---
title: "Terminal Server Client Error"
date: 2007-06-28
forum: General Help
---

### Post by ettienne on 2007-06-28
I keep getting an error message when closing a terminal server client session.
See attached screenshot.

---

### Post by andrewisett on 2007-07-27
I get the same error message as well.  Their is a bug report : [https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/122805]("https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/122805")

I believe there is also a way to suppress the error,  If anyone has a link to that directions they would be appreciated.

Here is one person's solution:

[https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/8422/comments/24]("https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/8422/comments/24")

---

### Post by andrewisett on 2007-07-27
Here's the solution's which worked for me:

Choose RDP v5 on the **General** Tab.  Then specify your exact keyboard type on the **Local Resources** Tab.  The above link and this link also helped:

[https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/66997/comments/3]("https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/66997/comments/3")

---

