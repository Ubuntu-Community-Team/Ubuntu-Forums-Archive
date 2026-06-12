---
title: "Using Office 2000 with Wine"
date: 2008-06-10
forum: General Help
---

### Post by dstein on 2008-06-10
I tried installing Office 2000 using Wine. I get similar errors as described here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5124](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5124). For example, I can not actually use the software because it repetitively prompts for the CD-key. Also, the installer does not seem to respond to customized Software selections. For example, if I select to not install Microsoft Outlook, which is the root element on its corresponding tree, proceeding levels of the tree are not automatically deselected, as they would be when installing on Windows.

Does anyone know if my problems would be solved by purchasing CrossOver Linux? I believe that it was developed by the same people that developed Wine, so my guess is that it would be no more compatible, although its site suggests otherwise. Please let me know if CrossOver by codeweavers does a better job running Office 2000 on Linux, or if you know of any method to successfully use Office with Wine. Thanks for any help. Also, I am using the latest builds of everything.

---

### Post by a1z on 2008-10-14
PART 1/3:

Installing Office 2K in Hardy is done with Wine v1.1.2.

1) install wine 1.1.2
2) extract office 2000 ISO (or zip or rar file)
3) install using setup.exe

====================
PART 2/3:

My question:

MS Word 2000 uses CPU all the time. My CPU meter on the task applet bar shows full usage of CPU when MS Word 2000 is opened and being used. The performance is smooth, nonetheless. When I minimize the window, the CPU relaxes.

What is going on? Is there a way to control the workload of CPU by MS Word 2000? Will this affect the performance of the word processor?

====================
PART 3/3:

SUMMARY:

I see this heavy usage of CPU under these conditions:

1) Hardy + Wine1.1.2 + Office 2000
2) Hardy + Wine1.1.2 + Office 2003
3) XP + Office 2000 (mentioned above)

But it is okay when I open and edit a document under these conditions:

1) XP + Office 2003
2) Hardy + Wine0.9.59 + Office 2003

Thanks in advance!

-a1z

---

### Post by alllenwilkyrobertson on 2008-10-14
> **dstein said:**
> I tried installing Office 2000 using Wine. I get similar errors as described here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5124](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5124). For example, I can not actually use the software because it repetitively prompts for the CD-key. Also, the installer does not seem to respond to customized Software selections. For example, if I select to not install Microsoft Outlook, which is the root element on its corresponding tree, proceeding levels of the tree are not automatically deselected, as they would be when installing on Windows.

Does anyone know if my problems would be solved by purchasing CrossOver Linux? I believe that it was developed by the same people that developed Wine, so my guess is that it would be no more compatible, although its site suggests otherwise. Please let me know if CrossOver by codeweavers does a better job running Office 2000 on Linux, or if you know of any method to successfully use Office with Wine. Thanks for any help. Also, I am using the latest builds of everything.
I also had no luck getting MS Office working so I downloaded Sun Open Office from openoffice.org

It is free and very compatible with Office files, with a very similar look/feel. More info at [http://www.sun.com/software/openoffice/index.jsp](http://www.sun.com/software/openoffice/index.jsp)

---

