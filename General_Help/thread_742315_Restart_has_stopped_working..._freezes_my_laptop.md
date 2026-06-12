---
title: "Restart has stopped working... freezes my laptop"
date: 2008-04-01
forum: General Help
---

### Post by kobinasucks on 2008-04-01
Hey You Good Community Folk,

Whenever I try to restart Ubuntu, everything shuts down alright, my desktop switches to a brown screen... and then it just stays there.

It never used to do this and I am not sure what exactly I have broken (or when). Could anyone tell me where to begin looking? 

Shutdown works just fine. But if I make the mistake of telling the computer to restart, it just stops after the desktop vanishes.

Strange...

---

### Post by Slushdoot on 2008-04-01
Try booting the failsafe kernel from Grub.  This'll automatically log in as root printing all the messages to the screen.  Run reboot and watch and see if it stalls at any one point that you can read.

---

### Post by kobinasucks on 2008-04-11
Thanks Slashdoot...

... didn't really work though. Curiously when I reboot in grub as root everything restarts perfectly: no funny messages/output at all.  The same applies to rebooting through a terminal.

But my restart option doesn't work. Neither does Ctrl+Alt+x, which also starts the process of restarting but freezes on a blank brown screen.

Any other suggestions?

---

### Post by kobinasucks on 2008-04-15
Bump

---

### Post by kobinasucks on 2008-04-16
Actually, consider this one solved. Not entirely sure what happened - probably Slushdoot's advice - but after a few reboots through the terminal, Restart has started working again.

Go figure.

Thanks Slushdoot.

---

