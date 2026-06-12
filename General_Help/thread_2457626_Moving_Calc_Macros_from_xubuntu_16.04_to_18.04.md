---
title: "Moving Calc Macros from xubuntu 16.04 to 18.04"
date: 2021-02-05
forum: General Help
---

### Post by Ralph L on 2021-02-05
When I move from older versions of Xubuntu to newer ones, I usually do a fresh install for various reasons.  When I moved from xubuntu 14.04 to 16.04, I copied the files ~/.config/libreoffice/4/user/basic and ~/.config/libreoffice/4/user/config from 14.04 to 16.04 and libreoffice (writer and calc) worked fine (as near as I could tell).  All my calc macros moved fine.  When I moved from 16.04 to 18.04, I did the same thing (moving the "basic" and "config" files from 16.04 to 18.04).  However, this time calc did not see my calc macros.
I have googled a lot and everybody says to go to calc main menu>Tools>Macros>Organize Macros>LibreOffice Basic>Organizer>Libraries and Import the missing macros.  My calc macros (from 16.04) are in the form "basic/Standard/Name.xba".  However, I can't seem to import them.  If I make a new macro under calc (18.04 version) I see a new file added to "basic/Standard" folder named Module1.xba.  Examining this file, it looks just the same as the .xba files from 16.04, but calc sees the new macro and doesn't see the old macros.
Anybody know how to import .xba macro files into a running calc program?

---

### Post by HermanAB on 2021-02-07
Howdy,

The problem may be very subtle.  What I would do, is to launch calc from the command line and then try to load a macro file.  You should then see many error messages on the console screen, which should give you a clue.

---

### Post by Ralph L on 2021-02-08
Just to follow up on the solution I found for this in case anyone else encounters the problem.  Please see the answer I got in the LibreOffice Questions website:  [https://ask.libreoffice.org/en/question/291659/how-to-move-macros-from-xubuntu-1604-to-1804/](https://ask.libreoffice.org/en/question/291659/how-to-move-macros-from-xubuntu-1604-to-1804/)

---

