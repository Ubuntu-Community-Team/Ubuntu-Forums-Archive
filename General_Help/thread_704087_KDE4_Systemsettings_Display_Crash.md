---
title: "KDE4 Systemsettings Display Crash"
date: 2008-02-22
forum: General Help
---

### Post by The_Doctor on 2008-02-22
Hi, I've got a Dell laptop with Intel graphics running KDE4. I recently reconfigured the X server, and now when I click on 'display' in systemsettings, the whole computer freezes, mouse won't respond, Ctrl Alt Backspace does nothing, and neither does trying to switch virtual consoles. The only solution has been a reboot. The same thing happens if I try to launch Krandrtray. Both of these were working before I reconfigured X.

Has anyone seen this error before or have pointers as to how I can fix it?
(I tried attaching my xorg.conf, but the page said the file was invalid)

---

### Post by umuro on 2008-03-02
It happened to me. I ended up removing kde4 repositories and removing anything kde4. kde4 systems settings is corrupting the settings sometimes and there is no easy recovery from that.

---

