---
title: "Screen: stay alive"
date: 2013-05-23
forum: General Help
---

### Post by hojjat on 2013-05-23
Sometimes when I need to run a command that takes hours, I use screen, run the command inside that screen session, then I detach from the session. Normally, the screen session stays alive only for a few minutes past the completion of the last command. Is there a way to make it stay alive indefinitely, so that I can go back and kill it by hand?

---

### Post by papibe on 2013-05-23
Hi hojjat.

I use 'screen' all the time.

How are you launching your command?
Are you launching as an argument in an screen command?

Regards.

---

### Post by hojjat on 2013-06-05
Sorry for the very late respond. I run screen, then in the command line I run a command, and then I press CTRL+A then D to detach.

---

### Post by papibe on 2013-06-05
That is very strange. The screen should stay alive running an interactive bash shell after the command ends.

By any chance are you running a bash script using the source command or the '.' option?
Does the screen not appear at all if you do an screen listing ( screen -ls )?

Regards.

---

