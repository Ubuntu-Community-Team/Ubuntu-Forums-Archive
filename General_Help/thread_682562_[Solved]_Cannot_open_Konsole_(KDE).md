---
title: "[Solved] Cannot open Konsole (KDE)"
date: 2008-01-30
forum: General Help
---

### Post by MSar on 2008-01-30
I just had the problem that on trying to open a terminal using Konsole the terminal just popped open and immediately closed again.

The thread [http://ubuntuforums.org/showthread.php?t=307449]("http://ubuntuforums.org/showthread.php?t=307449") helped me by suggesting to try to open xterm using Alt-F2 (run command). Within the xterm there was an error message that /bin/tcsh was not found.

So the original source of the error was the capability to assign the tc-shell to a newly created user (using kuser) without having the tc-shell installed.

Hope this helps anyone having a similar problem.

---

