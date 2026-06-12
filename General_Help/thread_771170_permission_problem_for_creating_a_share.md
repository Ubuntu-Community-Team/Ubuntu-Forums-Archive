---
title: "permission problem for creating a share"
date: 2008-04-27
forum: General Help
---

### Post by dondad on 2008-04-27
I am working on getting a Hardy setup done. One of the items that I want to do is to create a shared folder so that my other computer can access it (it is running Gutsy right now) I had no problem setting it up in the Gutsy install on this box, but in Hardy it gives me the error below. I have been using a samba share. Samba is installed, configured, and I have added myself as a user. Any idea how I can get the permission to set this up?
```

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share

```

I figured it out. I brought up nautilus with gksudo and set the share. That worked.

---

