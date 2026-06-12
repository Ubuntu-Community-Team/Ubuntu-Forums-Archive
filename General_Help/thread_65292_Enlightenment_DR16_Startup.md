---
title: "Enlightenment DR16 Startup"
date: 2005-09-13
forum: General Help
---

### Post by sinbad782 on 2005-09-13
Hi,
 I recently tried out the eLive live cd on my notebook and am impressed by Enlightenment (DR16 and DR17). I'd like to be able to run DR16 on my Ubuntu desktop, but after installed the enlightenment package(s) from the Ubuntu repos, I can't seem to find an option to start an enlightenment session at the gdm login screen.

Am I being really dense and missing some obvious setup step?

Thanks, PJS

---

### Post by wvslkr on 2005-09-13
It should have been added to the sessions tab in gdm.  If the file to edit is /usr/share/xsessions.  Its pretty self-explanatory.

Desktop Entry]
Encoding=UTF-8
Name=E16
Comment=This session starts the Enlightenment (e16) window manager
Exec=starte16
Icon=
Type=Application

Mine under e-live should work for Ubuntu.

---

### Post by sinbad782 on 2005-09-13
Nice one - not sure why this wasn't automatic, but thanks

---

### Post by sinbad782 on 2005-09-20
That's nearly right - I had to just change 'starte16' to '/usr/bin/enlightenment' and it worked. Thanks again.

---

