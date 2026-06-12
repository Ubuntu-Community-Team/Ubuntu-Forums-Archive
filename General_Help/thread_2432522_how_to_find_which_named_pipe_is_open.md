---
title: "how to find which named pipe is open?"
date: 2019-12-03
forum: General Help
---

### Post by Skaperen on 2019-12-03
i would like to find which unix named pipe/sockets a process has open.  the *man page* for [COLOR=#0000cd][FONT=courier new]**lsof**[/FONT][/COLOR] suggests i can get this with the [COLOR=#0000cd][FONT=courier new]**+E**[/FONT][/COLOR] option.  but all i get is the PID at the other end.  i'm particularly looking for those a process is waiting for a process to connect to (listening) and want the path that can be connected to by a client.

---

### Post by HermanAB on 2019-12-04
Hmm, List Open File (lsof) should work?  I don't get why it doesn't.  Maybe what you want is visible with ps.

---

### Post by Skaperen on 2019-12-04
i haven't found ways to list anything more than processes with [COLOR=#0000cd][FONT=courier new]**ps**[/FONT][/COLOR].  it's a classic tool following the "*do one thing well*" principle.
as mentioned in [#1]("https://ubuntuforums.org/showthread.php?t=2432522&p=13913689#post13913689"), it seems from the *man page* for [COLOR=#0000cd][FONT=courier new]**lsof**[/FONT][/COLOR] that i should get the _unix socket path_, but i don't.  *maybe i misunderstand the options or context*.

---

