---
title: "Failed to mount Windows Share: Permission Denied?"
date: 2021-10-01
forum: General Help
---

### Post by wyattwhiteeagle on 2021-10-01
When I try to access a shared folder on my fiance's Windows 7 laptop, Lubuntu allows me to access her system but not the shared folder.

I type in the access password and I get 2 messages...

> Failed to mount Windows share: Permission denied

> The specified location is not mounted

She has her's set to share what files I have on her laptop. (a sort of feeble backup of personal files).
But it seems Lubuntu needs to be configured to allow me to access the location on her comp.

Please help.

---

### Post by yancek on 2021-10-01
Do you do this with physical access to her computer or are you doing it over a local network?  If the former what are the permisisons on the shared folder?  If this latter, are you using samba to share?  If that's the case, what are the contents of the /etc/fstab file specifically relating to the shared folder?.

---

### Post by wyattwhiteeagle on 2021-10-01
> **yancek said:**
> Do you do this with physical access to her computer or are you doing it over a local network?  If the former what are the permisisons on the shared folder?  If this latter, are you using samba to share?  If that's the case, what are the contents of the /etc/fstab file specifically relating to the shared folder?.

There is no /fstab folder. If Samba isn't included with Lubuntu, it isn't installed.

If you mean the permissions on the shared folder that I'm trying to access, all permissions on that shared folder say forbidden, even after the access code is entered.

If you mean a shared folder or network sharing on my Lubuntu, I don't have any idea where the shared folder's are located.

I don't even know where to configure Lubuntu's sharing and share protection

I've looked through session settings, LXQt Settings, Advanced Network Configuration, all the system tools.

Nothing seems to be named in such a way to let me know that it is the sharing configurations.

---

