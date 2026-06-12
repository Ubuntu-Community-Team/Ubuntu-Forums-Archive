---
title: "1-click shutdown - security issue"
date: 2008-02-10
forum: General Help
---

### Post by phatsteve on 2008-02-10
I have managed to get a 'shutdown' and 'reboot' icon on my desktop by editing /etc/sudoers and adding:
 
[my user name] ALL=(ALL) ALL

and also commenting out

 %sudo ALL=NOPASSWD: ALL

The shutdown icon has the command 'sudo halt' and the working path is /sbin/
The Reboot icon has the command 'sudo reboot' and same work path.
Both work perfectly for 1-click shutdown or reboot.
My concern is security by allowing 'NOPASSWD: ALL'.
Is there a better way to edit sudoers to allow NOPASSWD for just these 2 actions?
This is on a laptop with only myself having access.
I am running Gutsy Kubuntu, but I imagine the basics will still apply to Kubuntu.

---

### Post by kerry_s on 2008-02-10
yeah, you shouldn't do that, that's no security at all.
you should only allow nopasswd for the commands your using.

i use "shutdown -r or -h now" so i just allow /sbin/shutdown with no password.
so since you use reboot and halt->
%sudo ALL=NOPASSWD: /sbin/halt, /sbin/reboot

here's what mine looks like->

---

### Post by phatsteve on 2008-02-10
kerry_s, thanks for reply, I have just received this reply on the Kubuntu forums which lets me leave sudoers alone

a simpler way:
the dcop call for reboot
Code:

dcop ksmserver ksmserver logout 0 1 0

while the one for shutdown
Code:

dcop ksmserver ksmserver logout 0 2 0

I tried it and it works fine.
Thankyou

---

### Post by kerry_s on 2008-02-10
yeah, that would work if you have kde, i don't.
anyways, at least you know how to do it, if you use something other than kde down the line.

---

