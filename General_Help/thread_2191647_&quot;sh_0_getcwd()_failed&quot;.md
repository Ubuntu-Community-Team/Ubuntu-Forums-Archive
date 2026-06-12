---
title: "&quot;sh: 0: getcwd() failed&quot;"
date: 2013-12-03
forum: General Help
---

### Post by expphoto on 2013-12-03
At random times I've been getting the following error. "sh: 0: getcwd() failed: No such file or directory"

During an uninstall of Metasploit, While running the Android Emulator, and while running apt-get update.

I've googled and have yet to find a solution. Anyone got any idears?

I'm on Xubuntu 13.04. Initially installed as Ubuntu, and then changed over to XFCE.

---

### Post by Toz on 2013-12-03
You'll get this error if you try to run some commands from a directory that doesn't exist anymore. Simply change to an existing directory and re-run the command. Its also possible that the uninstall script has a bug in it where it is trying to run some commands where the working directory is no longer valid.

---

### Post by expphoto on 2013-12-03
Ah! That makes sense. I feel smart now. hah. Thank you Toz!

---

