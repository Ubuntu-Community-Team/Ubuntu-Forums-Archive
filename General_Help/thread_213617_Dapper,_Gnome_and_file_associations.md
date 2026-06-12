---
title: "Dapper, Gnome and file associations"
date: 2006-07-11
forum: General Help
---

### Post by rquint on 2006-07-11
One of the major problems I have found with Gnome usability is the less than transparent connection between applications and their associated files.  Under MSWindows, MacOSes and even KDE it is easy to associate a file type with an applicationso that left clicking on a files icon will cause the file to be opened in the desired application.  When Ubuntu with Gnome is first installed things work this way for many files types, but after new applications are 

installed the associations often are broken and if a new association is desired for a newly installed application it can be very difficult to get it to work.  I know that under MS Windows the file association method is very simplistic, the file name's extension decides what association is made, while Gnome uses MIME types, but many different applications now use the same MIME type, e.g., text/XML or text/plain.



Let me be specific.  I use Maple (Maple 10) as a CAS.  It saves its worksheets as type XML document, MIME type application/xmlfiles with an extension, mw. After installing Maple and opening a worksheet by right clicking and selecting open with other application and then selecting Maple I now have a Maple.desktop file in /home/<me>/.local/applications and can get Maple to open when I right click on a maple worksheet's icon. However this does not associate Maple with its worksheets for opening by left clicking on a worksheet's icon.  Furthermore some workseets are opened in Maple when I use the right click -> open with Maple and others are not, Maple opens but with a new worksheet just as if I had launched it directly.  As far as I can tell, location of the worksheets and file permissions are identical.



A second problem has come up with TeX source files.  Initially they are associated with gedit.  I've installed Winefish and the file association is now with Winefish, but if an an execution bit is set in the file permissions left clicks on the file's icon are ignored and the open with Winefish option doesn't show in the right click menu.  (I know there is no reason to have an execute bit set but these are often files moved en mass from another OS's file system.)



Finally although I was able to get an icon associated with Maple mw files in Hoary and Breezy none of the methods I used now work in Dapper.  Any suggestions?  All my googling has just brought up the info I used before.

---

