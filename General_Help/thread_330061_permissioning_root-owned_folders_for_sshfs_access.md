---
title: "permissioning root-owned folders for sshfs access"
date: 2007-01-02
forum: General Help
---

### Post by jgb2185 on 2007-01-02
I have an older machine running Ubuntu 5.10 that I am using as a server, and a newer machine under Ubuntu 6.06 as my desktop. I have installed the XAMPP stack on my server, and would like to mount the server's /opt/lampp/htdocs/ folder on the desktop via sshfs for ease of editing files.

The /opt/lampp/ folder and most of its children are chmod 755 and owner:group root:root or nobody:root. I have identically named login user accounts on the server and the desktop. What is the best (read: most secure) way to set up access to the /opt/lampp/htdocs/ folder for my user account on the desktop, so that the sshfs mount will give me access from the desktop? I am assuming that I should minimize the involvement of root on both sides, but I am not at all certain how to proceed.

Many thanks...

JGB

---

