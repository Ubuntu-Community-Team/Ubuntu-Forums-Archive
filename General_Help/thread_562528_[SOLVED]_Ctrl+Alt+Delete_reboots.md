---
title: "[SOLVED] Ctrl+Alt+Delete reboots?"
date: 2007-09-28
forum: General Help
---

### Post by FuturePilot on 2007-09-28
Is that normal? One of the screensavers didn't agree to well with Compiz Fusion and it kind of froze. So I tried everything. Ctrl+Alt+Backspace and a bunch of others. Nothing worked, so out of desperation I pressed Ctrl+Alt+Delete and it dumped me to a tty and started rebooting. But now I press Ctrl+Alt+Delete and it does nothing. Does it only do that when it's frozen or something?

---

### Post by JBAlaska on 2007-09-28
I noticed it works in a CLI, my guess is when x stopped on you Ctrl+Alt+Delete works to initiate the reboot.

---

### Post by FuturePilot on 2007-09-28
I was kind of thinking the same thing. It probably only reboots like that from a tty, but not X.
I think that's what happened. I pressed Ctrl+Alt+Delete a few times and I think I pressed it after X stopped and that's what happened.

---

### Post by FuturePilot on 2007-09-29
Yep, that's what happened. I guess Ctrl+Alt+Delete reboots if you're in a tty.

---

