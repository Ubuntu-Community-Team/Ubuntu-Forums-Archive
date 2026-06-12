---
title: "ia32-libs"
date: 2012-11-21
forum: General Help
---

### Post by a.kazemi on 2012-11-21
Hi dear all
I have recently remove samba packages from my ubuntu12.04 x64bit because it causes some problems in my system. now I want to install teamviewer software which is not in the synaptic or software center and I have downloaded its .deb package for ubuntu from its official website.
when I double clicked on its packages Software Center open it and tell me 
> Error Cannot install 'ia32-libs'

however before these I had installed it by this method and Software Center do it without any errors and it worked fine!
now when I search ia32-libs in Software Center it finds these two packages:
> Multi-arch versions of former ia32-libraries
Ia32 shared libraries - transitional package

and when I want to install each of them it shows me these errors:

for the first package:
> Package dependencies cannot be resolved

This error could be  caused by required additional software packages which are missing or not  installable. Furthermore there could be a conflict between software  packages which are not allowed to be installed at the same time.

Details:
The following packages have unmet dependencies:
ia32-libs-multiarch:i386: 


for the second package:
> Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details:
The following packages have unmet dependencies:
ia32-libs: Depends: ia32-libs-multiarch but it is a virtual package


also when I open file explorer through nautilus in terminal when I want to delete a file or folder it gives me this warning:

> ** (nautilus:2907): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist

I asked these two issue at same post because I think may be they are related to each other and also mentioned that I have removed samba packages through synaptic because I think these issues emerged after that uninstallation!

please help me

---

