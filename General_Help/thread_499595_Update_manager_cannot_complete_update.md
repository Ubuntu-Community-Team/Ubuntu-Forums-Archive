---
title: "Update manager cannot complete update"
date: 2007-07-12
forum: General Help
---

### Post by christianj on 2007-07-12
Hi,

I am running Fiesty 7.4 on a standard PC.

Due to a power blackout while updating via Update Manager I now have the continual problem of a permanent update logo reminding me to update and the Update Manager unable to complete it task.

It has updated11 out of 13 updates and cannot find the other 3.

Any suggestions.

> Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?

> 
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.2.0-1ubuntu4_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.2.0-1ubuntu4_i386.deb)
  404 Not Found

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.2.0-1ubuntu4_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.2.0-1ubuntu4_all.deb)
  404 Not Found

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.2.0-1ubuntu4_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.2.0-1ubuntu4_i386.deb)
  404 Not Found



---

### Post by figgles on 2007-07-22
Have you tried running synaptic (gksu synaptic & or the "System > Administration > Synaptic Package Manager menu in gnome) and then click on the lower left of the synaptic application on the button "Custom Filters" then clicking on "broken" on the upper left to see if it lists anything? If it does then go to "Edit > Fix broken packages"

---

