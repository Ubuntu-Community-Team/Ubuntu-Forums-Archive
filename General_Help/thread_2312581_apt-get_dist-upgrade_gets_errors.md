---
title: "apt-get dist-upgrade gets errors"
date: 2016-02-05
forum: General Help
---

### Post by Dan_OBrien on 2016-02-05
Trying to update today and I get this message:

dpkg: error: parsing file '/var/lib/dpkg/available' near line 15307 package 'pidgin-data':
 `Breaks' field, invalid package name `p)dgin-facebookchat': character `)' not allowed (only letters, digits and characters `-+._')

I tried removing pidgin and pidgin-data, those removed successfully, but each time I ran apt-get dist-upgrade, I got that same error.

I edited the file /var/lib/dpkg/available and searched for facebookchat, I found the line with 'p)dgin-facebookchat' then changed the ) to an i and saved.

re-ran the update and it ran without errors.

Looks like someone made a typo with that package?



I'm running:

Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

---

