---
title: "Please help or i'm going to have to reformat :("
date: 2008-06-16
forum: General Help
---

### Post by Rob2008 on 2008-06-16
:(Need some urgent help or i'm going to have to admit defeat and reformat and poss go back to windows :confused:

I am having trouble installing anythin in ubuntu (heron) getting the following error:- dpkg pharse error i fi try to install anything in package manager or via applications.

PLEASE HELP...

Been using Ubuntu now for about 2months and so far its been excellent! , but one reason for changing to Linux from windows was so i don't have to reformat- reinstall etc etc
With windows i would have a crash (quite often) then have no way to repair it leaving me having to start all over again.

---

### Post by ad_267 on 2008-06-16
Try running "sudo apt-get update" and see if that fixes it.

If that doesn't work can you post that section of the file. You could use something like:

```
head -153550 /var/lib/dpkg/available | tail -50
```

---

### Post by kpkeerthi on 2008-06-16
Looks to me like your package database is corrupted. I'm not sure if this is really "fixable".

---

### Post by Rob2008 on 2008-06-16
> **ad_267 said:**
> Try running "sudo apt-get update" and see if that fixes it.

If that doesn't work can you post that section of the file. You could use something like:

```
head -153550 /var/lib/dpkg/available | tail -50
```


Tried the update but still getting same error :(

---

### Post by ad_267 on 2008-06-16
You could try renaming that file to a backup and then doing the update. Maybe remove anything except the main ubuntu repositories from your sources.list file first. I don't have any experience with this happening so you might want to wait for someone else's opinion.

---

### Post by ad_267 on 2008-06-16
You could also try just editing that file yourself. It looks like that should be "libxdmcp6" not "li`xdmcp6"

I don't know how that could have got that way in the first place though so maybe there's a deeper problem that I don't understand.

---

