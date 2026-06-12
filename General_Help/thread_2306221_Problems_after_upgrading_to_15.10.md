---
title: "Problems after upgrading to 15.10"
date: 2015-12-13
forum: General Help
---

### Post by Camilia on 2015-12-13
I recently upgraded to ubuntu 15.10. In spread sheet I can not change the font size and the bold affect does not work. When I click on the font size the are where font sizes is usually is blank in spread sheet and writer sheet. In writer sheet the bold works. 

If this is in the wrong section please move it.

Got a report that files opened had crashed. Ubuntu software restored the files and now no problems. That was just for a few minutes. Now cut and paste not working in spread sheet or writer sheet. Undo buttons not working in spread sheet or writer sheet. I closed the sheets open. Now again it is working. Seems to be an off and on problem. Solved by closing and starting and opening the sheets again.

---

### Post by netcom61 on 2015-12-13
Have you tried simply re-installing the application? Sometimes, just sometimes, it's as easy as that.

[https://wiki.ubuntu.com/LibreOffice#Installing_LibreOffice](https://wiki.ubuntu.com/LibreOffice#Installing_LibreOffice)

---

### Post by grahammechanical on 2015-12-13
This is a Libreoffice problem and not Ubuntu 15.10 problem. Is it Libreoffice version 5?

My advice would be to open the document and then open a blank document and copy & paste all the information into the new document. You can then save the document with the same name which will over-write the existing document of that name. That may solve this problem. If it is a Calc document you may need to use the Paste Special command to copy & paste any formula that are in the existing document.

Closing Libreoffice with documents still opened will produce that message about documents needing to be restored. It is Libreoffice that is doing the restoration from its automatic backups.

Regards.

---

### Post by Camilia on 2015-12-13
> **grahammechanical said:**
> This is a Libreoffice problem and not Ubuntu 15.10 problem. Is it Libreoffice version 5?

yes it is version 5.

---

### Post by Camilia on 2015-12-13
> **netcom61 said:**
> Have you tried simply re-installing the application? Sometimes, just sometimes, it's as easy as that.

[https://wiki.ubuntu.com/LibreOffice#Installing_LibreOffice](https://wiki.ubuntu.com/LibreOffice#Installing_LibreOffice)
Reinstalled and got this answer
Failed to fetch [http://ppa.launchpad.net/libreoffice/libreoffice-4-2/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/libreoffice/libreoffice-4-2/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found
Only time will tell if it did anything.

---

### Post by oldos2er on 2015-12-13
I would remove that PPA since it has no Wily version, and try reinstalling the application again.

---

### Post by Camilia on 2015-12-13
> **oldos2er said:**
> I would remove that PPA since it has no Wily version, and try reinstalling the application again.
How do I do that?

---

### Post by Geoffrey_Arndt on 2015-12-13
That is the problem with LibreOffice . . . you can remove/delete that PPA via System Settings>Software & Updates>Other Software (tab).  Then just uncheck that PPA, and close the window to reload the updated source list.   You will be asked for your password at least a couple o' times.    

So, in a prior version of Ubuntu, you added that PPA so you could get the latest LibreOffice.   It's no longer needed in Wiley Werewolf (15.10).   Be sure to fully uninstall and reinstall via Ubuntu Software Center.

Note . . . you might want to peruse the official Ubuntu documents to read about "Software Sources" . . . . very important to ensure stability - especially before next update.

---

### Post by Camilia on 2015-12-14
> **Geoffrey_Arndt said:**
> That is the problem with LibreOffice . . . you can remove/delete that PPA via System Settings>Software & Updates>Other Software (tab).  Then just uncheck that PPA, and close the window to reload the updated source list.   You will be asked for your password at least a couple o' times.    

So, in a prior version of Ubuntu, you added that PPA so you could get the latest LibreOffice.   It's no longer needed in Wiley Werewolf (15.10).   Be sure to fully uninstall and reinstall via Ubuntu Software Center.

Note . . . you might want to peruse the official Ubuntu documents to read about "Software Sources" . . . . very important to ensure stability - especially before next update.
Wow, that was simple. Got a link to the documents about software sources?

---

### Post by Geoffrey_Arndt on 2015-12-17
Here is a basic explanation . . . but there is more detail if needed.

[https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html](https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html)

---

