---
title: "Disabling console reboot through /etc/inittab"
date: 2007-02-11
forum: General Help
---

### Post by cookfromfrozen on 2007-02-11
Hi

I am trying to disable console rebooting with ctrl+alt+del through /etc/inittab.

See [Ubuntu Guide Page](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_disable_Ctrl.2BAlt.2BDel_from_restarting_computer_in_Console_mode)

However, since Upstart in Edgy, /etc/inittab has disappeared.

Where can I set this option now?

thanks

---

### Post by llamakc on 2007-02-11
/etc/event.d is where the upstart stuff is controlled.

---

### Post by cookfromfrozen on 2007-02-14
*bump*

I see nothing there that lets me disable ctrl+alt+del in the console -- the line which you previously needed to comment out is not there to comment out.

Any suggestions?

---

### Post by keybuk on 2007-02-15
comment out the "on" line in /etc/event.d/control-alt-delete

---

