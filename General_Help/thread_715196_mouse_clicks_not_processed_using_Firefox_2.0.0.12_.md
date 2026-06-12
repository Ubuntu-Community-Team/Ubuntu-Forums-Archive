---
title: "mouse clicks not processed using Firefox 2.0.0.12 on Gutsy"
date: 2008-03-04
forum: General Help
---

### Post by mjjnsmith on 2008-03-04
I can't find this exact problem reported anywhere, although it may be related to 
the bugs with suspend and resume.  That is, the only time it has happened I
have suspended and resumed many times.  After rebooting, the problem goes
away--like with other primitive OSes :(

I have Gutsy, with the latest updates, installed on a Lenovo 3000 N100.

Here is what happens:  Occasionally, when I'm using Firefox, the mouse
buttons stop functioning.  I can move the mouse around the screen, but
clicking has no effect--even on the Ubuntu menus.  The scroll wheel
doesn't work.  And Alt-Tab isn't recognized.  But Firefox is still alive, because
I can navigate with Tab, Ctrl-PgDn, etc, and I can select links with the Enter
key.  (All of those are working now.)

I crashed X with Ctrl-Alt-Backspace and logged back in.  Firefox was still
running, according to "ps aux".  I killed its process, then restarted Firefox
at the command line.  The same problem showed up.  (No error messages
in the xterm.)  Then I rebooted, and everything is working fine.

Thanks in advance for any help.

---

