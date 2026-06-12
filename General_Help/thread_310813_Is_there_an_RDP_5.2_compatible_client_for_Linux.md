---
title: "Is there an RDP 5.2 compatible client for Linux?"
date: 2006-12-01
forum: General Help
---

### Post by Balut on 2006-12-01
I have a Windows 2003 R2 Terminal Server with TLS authentication/encryption enabled for client connections.  Does a linux rdp client exist that is able to access this server?  Specifically it would have to support certificate based server authentication.  The Windows RDP client version that supports this is 5.2 which comes with the Windows 2003 Server.

Any help is greatly appreciated,

Thanks.

---

### Post by ciscosurfer on 2006-12-02
You can use Terminal Server Client under Applications > Internet.

If that doens't suit your fancy, then you can go to your Places menu, go to Connect to server.

Otherwise, you can install VNC or the like.

---

### Post by Balut on 2006-12-02
Thanks for the reply,

Unfortunately, none of those solutions would be able to connect to a remote desktop session on the Windows 2003 Server, because of the TLS authentication requirement.

The tsclient that is included with Ubuntu is only capable of RDP or RDPv5 connections.  Even the RDP client that is included with Windows XP is not compatible & needs to be upgraded to the RDP 5.2 client that comes with Windows 2003 Server.

VNC would need to be installed on the Windows Server, which isn't an option.

---

### Post by ciscosurfer on 2006-12-04
Balut,

I found this .deb that you may find useful (provided by getdeb.net): [http://www.getdeb.net/category.php?id=21](http://www.getdeb.net/category.php?id=21)

---

### Post by Balut on 2006-12-04
I had high hopes for the upgraded rdesktop, but unfortunately, still no support for 5.2.  Thanks for looking out.  I'm still searching.

---

### Post by ciscosurfer on 2006-12-04
> **Balut said:**
> [...]Thanks for looking out.  I'm still searching.As will I :KS

---

### Post by gurgle on 2007-01-05
any word on support for this yet?

---

### Post by ubuntology on 2007-10-24
Has anyone found an RDP 5.2 client for Linux yet?

---

### Post by tech4him on 2007-11-21
Still looking for this myself. 

Actually just compiled the rdesktop 1.5.0 client source and still not seeing tls/ssl support. This is really only the last thing keeping us from being able to move forward with Ubuntu on desk/laptops since 7.10 was released.

Anyone????

---

