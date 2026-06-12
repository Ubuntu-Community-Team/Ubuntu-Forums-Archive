---
title: "Folder Permissions?"
date: 2007-02-05
forum: General Help
---

### Post by Zander_Z on 2007-02-05
I'm attempting to install NSplugginwrapper and I'm having some difficulties. I found a pretty great howto but it seems I don't have permissions to access a folder because it belongs to the root, and my account. I did some searching and could not find a way to login as root to change the file permissions or allow the file to be executed. Is there a way I can change the file permissions under my account using the sudo command?

---

### Post by raul_ on 2007-02-05
I'm not sure what u mean, but if i'm correct try
```

sudo nautilus

```
and enter your password. You'll be browsing in root mode and can access any folder

---

### Post by closetpirate on 2007-02-05
simply before your commands type 
sudo yourcommand

then you will  be prompted for you password 

voila

you can change the write permissions for that folder with chmod if necessary

---

### Post by raul_ on 2007-02-05
> **closetpirate said:**
> you can change the write permissions for that folder with chmod if necessary

Sure, but it's not that safe :)

---

### Post by Zander_Z on 2007-02-05
Nautilus did the trick! Thanks a lot :D!

---

