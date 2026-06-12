---
title: "Sudo commands not working"
date: 2007-10-01
forum: General Help
---

### Post by chejrw on 2007-10-01
Hey everybody, I need a hand.

I have a server machine that's running Feisty (no GUI), and it's randomly decided that I'm no longer a sudoer, and none of my sudo commands will work.  I don't get any error messages or anything, it just returns to the command line without doing anything.

Consequently I can't edit the sudoers file, or ever restart the machine.

Help?

---

### Post by machoo02 on 2007-10-02
There is a way to safely reboot the machine using the [Magic SysRq Key]("http://en.wikipedia.org/wiki/Magic_SysRq_key").  Also, I'm not exactly sure about this, but you should probably be able to, following a reboot, select the recovery console at your GRUB menu and start the machine as root.  Then you could edit the sudoers file and restart up normally.

---

