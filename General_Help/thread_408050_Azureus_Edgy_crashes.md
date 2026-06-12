---
title: "Azureus Edgy crashes"
date: 2007-04-12
forum: General Help
---

### Post by thesheqq on 2007-04-12
I downloaded and installed azureus and it loaded fine the first time.  I was gonna try and install the plugin update but azureus started crashing.  It will load the splash screen and a quick flash of the console before crashing again when I try to open the app.  I typed azureus into a Terminal:

michael@michael-desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb0528d02, pid=5151, tid=3085096624
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid5151.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
michael@michael-desktop:~$

---

### Post by mac.ryan on 2007-04-13
Is your problem the one described in [this bug]("https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/68020")? If yes, you might try one of the workarounds described there, and/or you might wish to complete the mask appearing below the editing window (the one with the link to launchpad). My understanding is that when the bug will be fixed, a notice will be published on related threads...

...or am I wrong?

---

