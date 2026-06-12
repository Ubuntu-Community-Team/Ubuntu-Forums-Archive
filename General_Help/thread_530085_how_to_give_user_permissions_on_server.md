---
title: "how to give user permissions on server"
date: 2007-08-20
forum: General Help
---

### Post by mandeep kaur on 2007-08-20
Hi,

I have to give permissions to a user so that he can access data on the server but I am not able to do that.

Is somebody their to help me out please

Thanks & Regards

Mandeep Kaur

---

### Post by Soarer on 2007-08-20
Hi Mandeep,

We may need some more information to help you.

First, I assume the server is running Ubuntu?

If the client is also, then NFS would be the thing to use. Install on the server, share the folder(s) and give the user access.

If the user has Windows, then Samba is what you want. Again, install 'samba' on the server & share the folder(s).

You could also use FTP and/or ssh, depends on what you are trying to achieve.

---

