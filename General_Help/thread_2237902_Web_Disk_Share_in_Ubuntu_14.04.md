---
title: "Web Disk Share in Ubuntu 14.04"
date: 2014-08-04
forum: General Help
---

### Post by foberle on 2014-08-04
Does anyone know how to set up a Web Disk Share in Ubuntu 14.04, specifically a WebDAV share?

I want to use it for updating my web pages to the server in the background.

The support at my ISP confirmed that this used to work with Nautilus back in Ubuntu 9.x, but now that Nautilus shows up as "Files 3.10.1" in Ubuntu 14.04, I was wondering if Canonical removed or altered this capability along the way.

Thanks much for any assistance.

---

### Post by TheFu on 2014-08-04
I don't know the answer. WebDAV is known for having SERIOUS security issues both on the server AND client sides, so nobody uses it.
The best way to have copy/paste for remote files is over sftp - if the host supports ssh, then they support sftp.  And if they don't support ssh - well - FIRE THEM.

Just use sftp:// as the URL.
From Windows, filezilla or **WinSCP** can be used, as well as **rsync** or any of the backup tools based on librsync that transfer using ssh.  This is extremely secure AND really easy, unlike all the other options.

---

### Post by foberle on 2014-08-04
Thanks much for the info. I'd never used any service of that ilk before, so wasn't aware of the issues.

I'll stick to sftp as you suggest.

Again, thanks for the quick response.

---

