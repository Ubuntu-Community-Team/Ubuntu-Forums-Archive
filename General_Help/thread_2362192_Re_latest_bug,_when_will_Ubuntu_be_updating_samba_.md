---
title: "Re: latest bug, when will Ubuntu be updating samba v4.3.11?"
date: 2017-05-25
forum: General Help
---

### Post by da2357 on 2017-05-25
It was announced just yesterday that there's a new-and-serious Samba bug. Information about it can be found here:


[http://www.theregister.co.uk/2017/05/25/fatthumbed_dev_slashes_samba_security/](http://www.theregister.co.uk/2017/05/25/fatthumbed_dev_slashes_samba_security/)


[COLOR=#0000cd]*"In CVE-2017-7494, a malicious client can "upload a shared library to a writable share, and then cause the server to load and execute it.""*[/COLOR]


On my 16.04 LTS server, I ran 'samba --version' and got back: 4.3.11


When I followed the link in the article to Samba's website, it indicates fixes for some versions, but not for Samba 4.3.11. Does anyone know when Ubuntu/Canonical will be making an update for Samba available to us?


-- David Allie

---

### Post by howefield on 2017-05-25
Thread moved to the "*General Help*" forum.

---

### Post by howefield on 2017-05-25
What's the output of.. (assuming you have already done a "sudo apt update")

```
apt-cache policy samba
```

The patched version looks like 2:4.3.11+dfsg-0ubuntu0.16.04.7

---

### Post by da2357 on 2017-05-25
@howefield, thanks for the quick reply.

Yes, I get the same result as you posted: 2:4.3.11+dfsg-0ubuntu0.16.04.7

and while I did run 'sudo apt-get update' and 'sudo apt-get upgrade' yesterday, I don't remember noting any Samba items being upgraded.

---

### Post by howefield on 2017-05-25
You should be able to view the changelog with..

```
apt changelog samba
```

which should include the latest update..

```
samba (2:4.3.11+dfsg-0ubuntu0.16.04.7) xenial-security; urgency=medium

  * SECURITY UPDATE: remote code execution from a writable share
    - debian/patches/CVE-2017-7494.patch: refuse to open pipe names with a
      slash inside in source3/rpc_server/srv_pipe.c.
    - CVE-2017-7494

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Fri, 19 May 2017 14:18:13 -0400
```

Or view from packages.ubuntu.com/xenial/samba

---

### Post by da2357 on 2017-05-25
I just ran 'apt changelog samba' per your suggestion and it does indeed look (if I read it correctly) it has already been patched. I simply don't remember seeing it, but I'm glad it is patched. This is what I got:

```
samba (2:4.3.11+dfsg-0ubuntu0.16.04.7) xenial-security; urgency=medium


  * SECURITY UPDATE: remote code execution from a writable share
    - debian/patches/CVE-2017-7494.patch: refuse to open pipe names with a
      slash inside in source3/rpc_server/srv_pipe.c.
    - CVE-2017-7494


 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Fri, 19 May 2017 14:18:13 -0400
```

Thanks again for your help!

---

