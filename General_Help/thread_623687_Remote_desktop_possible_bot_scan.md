---
title: "Remote desktop possible bot scan"
date: 2007-11-26
forum: General Help
---

### Post by Monkey77 on 2007-11-26
Hi,

I have a quick question.  Last night I was playing World of warcraft on my recently upgraded 7.10 when about 3 times the game would lag for about 30 seconds and then I would see a message saying something like remote desktop connection ended.

I have the remote desktop enabled with a password and not to prompt the user, I set this up before my upgrade from 7.04 to 7.10 and have not touched it since.

My guess is that some bot is scanning for the VNC port 5900 and trying standard passwords.  Has anybody else see this?

Regards
Phil Hannent

---

### Post by hikaricore on 2007-11-26
I noticed this before with both VNC and SSH.
Just change it to a non-standard port and most of these botnets will miss you entirely.

I also believe that VNC connection attempts are logged somewhere, not sure where but I can't imagine them not being.

---

