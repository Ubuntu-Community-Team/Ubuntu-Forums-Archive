---
title: "[SOLVED] How do I make &amp;quot;Run in terminal&amp;quot; default?"
date: 2007-09-15
forum: General Help
---

### Post by eapache on 2007-09-15
I've already tried this: [http://ubuntuforums.org/showthread.php?t=44587](http://ubuntuforums.org/showthread.php?t=44587)

Unfortunately, there is no option for 'run in terminal', only 'run' which does not open the terminal window. Is there a way to do this (or just something to put at the beginning of a script to make it do it for that scrip only)?

---

### Post by por100pre1 on 2007-09-15
> **eapache said:**
> I've already tried this: [http://ubuntuforums.org/showthread.php?t=44587](http://ubuntuforums.org/showthread.php?t=44587)

Unfortunately, there is no option for 'run in terminal', only 'run' which does not open the terminal window. Is there a way to do this (or just something to put at the beginning of a script to make it do it for that scrip only)?

You can create a launcher and select Type: Application in Terminal.

**EDIT: Sorry, [this]("http://ubuntu-tutorials.com/2007/05/13/nautilus-open-terminal-terminal-quick-launch/") is what you are looking for.**

---

### Post by eapache on 2007-09-15
The launcher was what I was looking for (or a near-enough workaround) however for some reason launchers won't let you run scripts from them with ./

I ended up just moving the script to /usr/bin and calling it with a launcher. While a little more complicated, it does what I wanted it to.

---

