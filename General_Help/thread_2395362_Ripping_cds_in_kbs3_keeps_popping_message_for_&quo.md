---
title: "Ripping cds in kbs3 keeps popping message for &quot;gvsfd-cdda&quot;"
date: 2018-06-30
forum: General Help
---

### Post by droyduser on 2018-06-30
I recently clean installed ubuntu 18.04.  I switched from Windows 10 and have been starting with ripping my cd library to flac files.  However, every time I try to rip one, I get the attached message.  I can still press, "Quit the other applications" and it will rip the cd, but it does make me wonder what the message is referring to.  Does anyone have an idea what this might be?[ATTACH=CONFIG]280259[/ATTACH]
P.S.  If my screenshot doesn't enlarge when clicked upon please let me know.

---

### Post by bodhin2 on 2018-06-30
give ripperX a try.  i used a couple of times before without any issues.

---

### Post by Holger_Gehrke on 2018-07-01
gvfs is the Gnome Virtual File System, a set of tools that make things that are not really file systems seem as if they were. A Compact Disc Digital Audio (cdda) does not really have a file system, just some tracks and an index telling the player were the tracks begin. That you can open a cdda in the file manager and see a list of files is due to gvfsd-cdda. You could actually rip your CD in the filemanager by just copying those files to your HD. Of course a real ripper has some additional capabilities (meta-data look-uo, read-error recovery, file format conversion ...).

Holger

---

