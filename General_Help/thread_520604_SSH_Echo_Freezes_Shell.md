---
title: "SSH Echo Freezes Shell"
date: 2007-08-08
forum: General Help
---

### Post by steampunk on 2007-08-08
Hello! This is very probably a general Linux problem. I recently upgraded my home machine to 64 bit and installed the 64 bit version of Feisty Fawn. Since then, whenever I SSH to my home computer remotely the shell freezes if it attempts to echo more than a few lines back to me.

For example, if I use the 'top' command, it freezes. If I cat something or man something, freezes. I have to SSH in again and kill the prior shell.

It's not like the processor can't handle it. The computer itself doesn't freeze at all. In fact, everything locally works fine. This only happens from remote SSH connections.

*weeps!*

---

### Post by AlexThomson_NZ on 2007-08-08
That is so odd.  You might have to do some detective work- does this happen in both gnome-terminal and the actual console (Ctrl+Alt+F1)?  Is this happening after a certain number of bytes (256 per chance?)  Doe this happen when using the Live CD?  Is this hapenning when gnome-terminal starts scrolling?

//EDIT:  Ahh I see this is more likely happening at "the other end" rather than the client

---

### Post by steampunk on 2007-08-09
I think this might have something to do with my network (possibly firewall stuff) here at work. I was able to replicate the problem using another computer and SSH'ing to a friend's home computer. Thanks for the help! :)

---

