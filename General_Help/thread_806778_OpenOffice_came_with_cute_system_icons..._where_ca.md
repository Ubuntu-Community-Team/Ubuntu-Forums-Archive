---
title: "OpenOffice came with cute system icons... where can I get them again?"
date: 2008-05-25
forum: General Help
---

### Post by Sarah L on 2008-05-25
Hi guys,

I've just installed the latest version of OpenOffice from the .DEB packages that are provided by OpenOffice.org. The new version works great, but unfortunately it overwrote the cutesy-looking round icons that came with the default Kubuntu installation, and replaced them with the nasty, gray, generic ones.

Does anyone know where to find the nice pretty icon set for the OpenOffice suite? My KMenu would appreciate it very much! ;)

Thanks,
Sarah

---

### Post by sub2007 on 2008-05-25
In OOo:

Tools > Options

Under the OpenOffice.org expanded section (on the left) click View... Then under Icon Size and Style change whatever is in the right hand box to Crystal (which I think is the default in KDE).

Click OK and it should have changed the icons to the nice ones.

If you don't have the Crystal icons installed (I think you should have) then you can install them using

```
sudo apt-get install openoffice.org-style-crystal
```

---

### Post by Sarah L on 2008-05-25
Thanks, but I was referring to the system icons - the ones that appear in the menu and the file browser.
They were round and pretty and I want them back! :)

---

### Post by sub2007 on 2008-05-25
Ah OK. I know that's provided by the KDE integration package which is in repositories (openoffice.org-kde) but I don't know if the version that's in repos will work with your new version.

You could try checking to see if that package in installed and if not installing it, but otherwise I don't know what else to suggest.

---

