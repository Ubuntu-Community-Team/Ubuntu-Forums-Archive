---
title: "Alternative to Remastersys/UB/UCK"
date: 2015-05-01
forum: General Help
---

### Post by maud2 on 2015-05-01
Hey guys,

I'm eager to use my respin of Ubuntu 14.04 on my other machines. The problem is that since Remastersys and Ubuntu Builder are discontinued, it's hard to find a good alternative. For some reason UCK won't work on my computer (even with various tweaks people post to make it work). It doesn't have to be a GUI program, but at least a bit usable. I also want to customize Ubiquity and install it with a USB. The system will be used within my company.

Thanks in advance!

---

### Post by sudodus on 2015-05-01
Welcome to the Ubuntu Forums :-)

A. What you can do is to create an OEM installed system

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

 Limitation of porting an installed system: You must avoid proprietary drivers (or the installed proprietary drivers must work in all target computers).

B. and copy or clone that installed system. I can suggest two alternatives:

1. Use ***Clonezilla*** to make a compressed image, and expand that compressed image into the other computers.

[http://clonezilla.org/](http://clonezilla.org/)

Limitation of Clonezilla: Can only install into a drive of the same size or bigger.

2. Use the ***One Button Installer*** to make a tarball, a compressed tarfile, and use the One Button Installer to install the system into the other computers.

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

Limitations of the OBI: One root partition and one swap partition (does not work with separate home partition). Does not work with UEFI.

[COLOR=#696969]If you are interested in the OBI method, you can try an improved tool (still being developed) to create a tarball, ***zmktbl***

[/COLOR][[COLOR=#696969]http://phillw.net/isos/linux-tools/torios/2015-04/zm/[/COLOR]]("http://phillw.net/isos/linux-tools/torios/2015-04/zm/")[COLOR=#696969]

zmktbl should be installed into the system, where you have the OBI, normally Lubuntu Trusty 32-bit. You can make a tarball of a 64-bit system.[/COLOR]

---

