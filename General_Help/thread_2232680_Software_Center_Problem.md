---
title: "Software Center Problem"
date: 2014-07-03
forum: General Help
---

### Post by prusakjakub on 2014-07-03
When I try to open software center through shortcut/terminal it opens and then closes. In the top bar next to the internet signal I get an icon with this message:

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_i18n_Translation-en%%5fGB, E:The package lists or status file could not be parsed or opened.

Thanks

---

### Post by slickymaster on 2014-07-03
Hi prusakjakub, welcome to the forums.

Open a Terminal and run the following commands one at a time:```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```See also [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

### Post by prusakjakub on 2014-07-03
After following the instructions the error is still there.

---

### Post by slickymaster on 2014-07-03
Try following steps 2-5 in the link I provided you.

---

### Post by prusakjakub on 2014-07-03
Thanks, it worked :)

---

### Post by slickymaster on 2014-07-03
Glad you've got it fixed and working. Happy *buntuing.

---

