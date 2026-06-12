---
title: "[SOLVED] I need to 'SHUTDOWN' using keyboard combination"
date: 2008-01-25
forum: General Help
---

### Post by dryder on 2008-01-25
Hi

I need a key combination that will shutdown the computer without using the mouse or terminal.

Can anybody help please? All the research I have done use launchers or terminal or passwords. I need something (preferably that I can assign the key combination) like " Ctrl-S-D" or whatever. (assigning it makes it more secure)

Many thanks,
David

---

### Post by steveneddy on 2008-01-25
> **dryder said:**
> H

Huh - looks like he figured it out.

:p

---

### Post by dryder on 2008-01-25
No - the whole post just didn't go through - see edit

---

### Post by aaaantoine on 2008-01-25
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Remember this phrase:
**R**aising **E**lephants **I**s **S**o **U**tterly **B**oring

What you do is hit Alt-SysRq-R, then wait a few seconds, then Alt-SysRq-E, wait a few more seconds, and so on.  This safely Restarts the computer when nothing else works.

If you'd rather shut down the computer, replace "Boring" with "Ordinary", according to the Wiki article above.

You can also set the power button to behave as a power off switch.  By default in Ubuntu it asks you what you want to do.  If you'd rather keep the default functionality, you can press the power button, and then press Alt-S to shut down when the prompt comes up.

---

### Post by dryder on 2008-01-25
Hi aaaantoine

Thanks for your reply.

Is there a way I can simplify or reduce the keystrokes - I am unable to press 3 keys so far apart at the same time?

David

---

### Post by jpeddicord on 2008-01-25
> **aaaantoine said:**
> [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Remember this phrase:
**R**aising **E**lephants **I**s **S**o **U**tterly **B**oring

What you do is hit Alt-SysRq-R, then wait a few seconds, then Alt-SysRq-E, wait a few more seconds, and so on.  This safely Restarts the computer when nothing else works.

If you'd rather shut down the computer, replace "Boring" with "Ordinary", according to the Wiki article above.I really wouldn't recommend this unless your computer is frozen. There is a chance you can do a lot of damage with it rather than shutting it down manually.

dryder:

See System > Preferences > Power Management, General tab. Change "When the power button is pressed" to "Shut Down." When you press the power button now (don't hold it) it will do a proper shutdown procedure.

Jacob

---

### Post by dryder on 2008-01-25
Thanks jacobmp92 !

That is exactly what I need.

David

---

