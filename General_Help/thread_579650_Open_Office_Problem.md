---
title: "Open Office Problem"
date: 2007-10-18
forum: General Help
---

### Post by titctoc on 2007-10-18
Hi guys. I've recently installed Ubuntu 7.10 on a clean h/drive. Everything looks good and works 'out of the box', but one problem exists with Open Office.

When i select 'Database' or Presentation' it automatically opens up a data recovery window, and when this window is cleared, it opens up the wordprocessor. This happened the first time i selected either options, and have subsequently repeated everytime i try to use the applications.

Word and spreadsheet work fine, it's just the other 2 i cannot use. There were no errors generated during install, and no problem with open office when using OpenSuse or Debian 4.0.

Any help would be of great help please.

Regards Tictoc

---

### Post by Inxsible on 2007-10-18
I have had problems with the pre-installed version of OO. I simply removed it and re-installed using the rpms from openoffice.org. No problems since.

This was in Feisty tho. you might want to try it, you might not want to. :)

---

### Post by rfurman24 on 2007-10-18
> **titctoc said:**
> Hi guys. I've recently installed Ubuntu 7.10 on a clean h/drive. Everything looks good and works 'out of the box', but one problem exists with Open Office.

When i select 'Database' or Presentation' it automatically opens up a data recovery window, and when this window is cleared, it opens up the wordprocessor. This happened the first time i selected either options, and have subsequently repeated everytime i try to use the applications.

Word and spreadsheet work fine, it's just the other 2 i cannot use. There were no errors generated during install, and no problem with open office when using OpenSuse or Debian 4.0.

Any help would be of great help please.

Regards Tictoc


This happens for me as well as many others. Do you have a theme in use other than the default? There seems to be a problem with using other themes and have openoffice.org-gtk installed. I do not not know about others but I do not want to have to use the default theme to use OO. I do not want OO to not blend with my desktop. There are no problems with this in Feisty with the old OO.

---

### Post by titctoc on 2007-10-18
Everything is set at the default install. I haven't adjusted or installed anything else yet, and was just going through each item in the menu list. :(

Tictoc

---

### Post by rfurman24 on 2007-10-18
You might try to uninstall openoffice.org-gtk and see if it takes care of it. I have seen a few people have issues related to compiz but your problem sounds just like mine. The only band aid I could come up with was what I just mentioned.

---

### Post by titctoc on 2007-10-19
I found the reason for the OpenOffice problem,...It's the 'CRUX' theme. I have wiped and re-installed Gutsy 3 times and the problem is re-producable (on my system). If i use any other theme apart from 'CRUX', then OpenOffice works without problems, but as soon as 'CRUX' is enabled, i cannot use the Database or Presentation as it flags up a document recovery error.

Regards Tictoc

---

