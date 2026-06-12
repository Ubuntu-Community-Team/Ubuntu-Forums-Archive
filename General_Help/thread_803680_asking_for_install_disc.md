---
title: "asking for install disc"
date: 2008-05-22
forum: General Help
---

### Post by DiGiTY on 2008-05-22
I'm trying to install some programs with apt-get and it prompts me to insert the 7.04 beta disc I used to install Ubuntu. I obviously don't have it anymore, so how do I set up Ubuntu to not ask for the install disc during installation of programs anymore (and download whatever dependencies it needs instead)?

TIA

P.S. - I'm running 7.10 (yes, i did an upgrade using Update Manager some time ago)

---

### Post by sisco311 on 2008-05-22
System > Admin > [B]Software Sources
[/B]In the Third-Party Software tab deselect the cdrom entry.

---

### Post by DiGiTY on 2008-05-22
thanks for the quick reply.

there is no CD-ROM entry in the Third Party tab.

There is CD-ROM entry checked in the Installable from CD-ROM/DVD section of the Ubuntu Software tab, but it says Ubuntu 7.10 'Gutsy Gibbon' not Ubuntu 7.04 beta like the CD I was prompted for. Will unchecking that work eventhough it's not the same version?

---

### Post by grepgav on 2008-05-22
As long as you are able to download the software from online repositories, go ahead and uncheck any listing for software from a CD/DVD source. As long as the only available sources are online repositories you should not be prompted to insert the CD.

---

