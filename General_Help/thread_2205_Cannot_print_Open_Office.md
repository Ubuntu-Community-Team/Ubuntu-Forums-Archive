---
title: "Cannot print Open Office"
date: 2004-10-26
forum: General Help
---

### Post by montgomj on 2004-10-26
New to this os.  Things went well until I tried to change the Open Office printing by using the OO Print Administration program.  Changed the printer from A4, which it allways seemed to be, to US Letter.  Exited and now no printing from that printer.  The printer now has no size properties (blank) and the printing command is "lpr".  All other programs are printing fine.  Anyone know an easy way to fix the OO printing?

Thanks in advance.

montgomj

---

### Post by kamstrup on 2004-10-26
What happens when you change it back?

---

### Post by j_baer on 2004-10-26
montgomj,

I suffered the same fate. I noticed the date of the ISO (10/20) on the web was newer than the ISO I was using. On a chance I re-downloaded the ISO and re-installed.

Printing works correctly now.

Good luck ...

---

### Post by montgomj on 2004-10-26
Thanks

Kamstrup, I can no longer change any option of printers in OO.  Nothing was there!  Tried to delete and still no luck (that option is now greyed out).  Cannot add another printer as it will only add a fax or a PDF device.

I removed the cups-managed printer in Gnome and then reinstalled.

Same problems.

I do not yet want to reinstall....................

Still searching for a solution.  Next might remove OO and then reinstall that.  Printer still works under Gnome.  Just not in OO.

montgomj

---

### Post by WW on 2004-10-26
I have the same problem.  There is a work-around described in the bug report that I  filed in bugzilla:

    [https://bugzilla.ubuntu.com/show_bug.cgi?id=1925](https://bugzilla.ubuntu.com/show_bug.cgi?id=1925)

---

### Post by montgomj on 2004-10-26
Thanks WW.  Got to read all the neat info with that bug report, made the change, and got back my printing in OO.

Did have to adjust properties to switch the print command to lpr -P "printer" where printer is the cups "name" of my printer.

Back to work and thanks very much for pointing me in the right direction.  I am not very familiar with bugzilla but should learn more.

montgomj

---

### Post by DCuser on 2004-10-28
I'm just trying out Ubantu, and I noticed this printing problem in OpenOffice.  I downloaded the latest version (1.1.3) from the Openoffice.org website and followed their installation instructions.  It works fine and prints correctly, but it couldn't put links in the Gnome Application listing for Openoffice, so I made a launcher icon on the desktop that pointed to the proper script (I use the Word Processor, so I put a link to the swriter script).

I also noticed that AbiWord defaults to a paragraph style that is en-UK, and the Page Setup continuously reverts to A4.  I have tried to change the Normal template, but even that has not stopped the A4 problem.  I can click on "File" "New" and select  the US-Letter template, but I would like to simply go into AbiWord with the Normal template giving me a US-Letter format.  I think I could do this by installing a fresh version from the Abisource site, but, being a novice, I'm a bit shy about trying this.  :-k

---

### Post by DCuser on 2004-10-31
Just wanted to mention that I found using OpenOffice 1.1.3 had a few glitches, but by starting it with a "sudo" command on some occasions, I got it to properly update some configuration options.  Other than that, it works great.

Also, on a side-note, AbiWord defaults to loading a UK template that puts in the A4 pagesize.  I found that, by using the root terminal, I was able to copy the US-Letter template to a different file (US2), then rm the UK template, and then copy the US2 file to the UK template name.  Now AbiWord "thinks" it is working in the UK, but it gives me a US letter format.

---

### Post by kamstrup on 2004-11-10
I think you can safely call that "a hack" ;P

---

