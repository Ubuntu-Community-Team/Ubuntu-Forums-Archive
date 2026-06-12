---
title: "Problem with gvfs and WebDAV share with Digest authentication"
date: 2012-12-21
forum: General Help
---

### Post by spazzeri on 2012-12-21
On Ubuntu 12.04 I try to connect to a WebDAV share on the local network, from Nautilus.


  This works with cadaver and davfs (both of which seem to depend on a library called neon to do their work).


  However it does not work with **gvfs**: Nautilus displays 'Error: not a WebDAV-enabled share'.


  On the Apache2 server, access.log shows 

```
"OPTIONS /location HTTP/1.1"  200  229 "-" "gvfs/1.12.1"
```  The configuration follows this writeup: [https://help.ubuntu.com/community/Apache2WebDavDigestAUTH](https://help.ubuntu.com/community/Apache2WebDavDigestAUTH)
[URL="https://help.ubuntu.com/community/Apache2WebDavDigestAUTH"]
[/URL]
  Is it a known gvfs bug ?

---

### Post by spazzeri on 2012-12-23
**Update**:

It fails with the same error in Nautilus when Basic authentication is required instead of Digest.

gvfs is used successfully to connect to remote webdav spaces over https, such as mydrive.ch

Why this simple connection over a local network fails is beyond me.

---

