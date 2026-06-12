---
title: "Upgrade openoffice.org-core ubuntu5.3 crashes"
date: 2008-02-05
forum: General Help
---

### Post by Michl on 2008-02-05
I have been using openoffice.org writer without any problems
in Gutsy.  DId an upgrade, and now openoffice.org writer
crashes right away -- opens into a document recovery
window.  Went and double-checked, and the version of
core that works is ubuntu5 and the version that crashes
is ubuntu5.3.

No, removing gtk does not solve the issue, and changing
themes also does not make a difference.

---

### Post by ptn107 on 2008-02-05
The current version of OpenOffice.org for Ubuntu 7.10 is 2.3.0 (package version *1:2.3.0-1ubuntu5.3*).  This update is downloaded from *main/gutsy-updates*.  If you are having troubles with this update, then you can have synaptic downgrade your OpenOffice.org packages back to *1:2.3.0-1ubuntu5*.

Fire up synaptic, search for your OpenOffice.org packages, select them, and go to the **Package** menu and click **Force Version**.  Select *1:2.3.0-1ubuntu5* click OK, then apply.  This might have to be done individually for each installed OpenOffice.org package.

---

### Post by Michl on 2008-02-05
> **ptn107 said:**
> The current version of OpenOffice.org for Ubuntu 7.10 is 2.3.0 (package version *1:2.3.0-1ubuntu5.3*).  This update is downloaded from *main/gutsy-updates*.  If you are having troubles with this update, then you can have synaptic downgrade your OpenOffice.org packages back to *1:2.3.0-1ubuntu5*.

Fire up synaptic, search for your OpenOffice.org packages, select them, and go to the **Package** menu and click **Force Version**.  Select *1:2.3.0-1ubuntu5* click OK, then apply.  This might have to be done individually for each installed OpenOffice.org package.

Thanks -- I had tried that right away forcing and downgrading the openoffice core to ubuntu5,
but then I made a mess of the dependencies.  I tried downgrading the meta-package and just
made a bigger mess.

P.S.:
I changed the repositories to get rid of gutsy upgrade, reloaded, installed ubuntu5, and
still had the very same crashes.  So I upgraded to Heron and the 2.3.1-3ubuntu3 does
not crash, at least not in Heron.

---

