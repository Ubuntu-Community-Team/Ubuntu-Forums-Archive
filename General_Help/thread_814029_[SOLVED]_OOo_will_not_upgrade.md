---
title: "[SOLVED] OOo will not upgrade"
date: 2008-05-31
forum: General Help
---

### Post by x1a4 on 2008-05-31
Hi,

I last upgraded on Thursday and there were a few updated GNOME libraries which upgraded OK.  Today I tried to upgrade again and got a bunch of OpenOffice packages which were automatically kept back.  There were no errors.  I tried both the primary server and the Canadian mirror and got the same result.  This is my output:
```

~/# aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  openoffice.org-base [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-base-core [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-calc [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-common [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-core [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-draw [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-filter-binfilter [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-impress [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-java-common [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-math [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-officebean [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-style-andromeda [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-style-crystal [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-style-human [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-style-tango [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-writer [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  python-uno [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
The following packages have been kept back:
  openoffice.org [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-gcj [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-gtk [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
  openoffice.org-style-industrial [1:2.4.0-3ubuntu6 -> 1:2.4.1~rc1-1ubuntu1] 
0 packages upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      

```

Any ideas on how to diagnose and fix this? 

Thank you.

---

### Post by Sam Lars on 2008-05-31
The OOo packages are also not available to upgrade for me.  They probably depend on some other package that is not available at this time.

---

### Post by simontol on 2008-05-31
The localization packages aren't ready yet.

Look for openoffice.org-help- and openoffice.org-l10n-, they are still 2.4.0.

---

### Post by igoddard on 2008-05-31
Note that the new versions listed are only release candidates.  It might be best to wait for the final release unless you're wanting to test the RC.

Ian

---

### Post by Nathan_M on 2008-05-31
Yeah, it was bugging me so much having the new updates icon when I couldn't update that I removed the proposed updates option (System > Administration > Software Sources. Updates tab),

---

### Post by x1a4 on 2008-06-02
Updated en-gb language packs have now been added and OOo upgraded successfuly.

---

