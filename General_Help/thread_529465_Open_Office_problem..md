---
title: "Open Office problem."
date: 2007-08-19
forum: General Help
---

### Post by igor54 on 2007-08-19
Feisty Fawn (alternative iso download)
Installed fine, went to update (via wizard) - reported errors with OO.o update.
Tried installing a few things since, and have config errors relating back to OO.o
Original error started with [quote]
/var/lib/deforma:failed to write cache
[end quote]
Other messages with different font names were there, too.
Tried uninstalling OO.o - failed because of the same errors - - - WTF????

Any insights ??

---

### Post by gobbles414 on 2007-08-19
Hi igor54,

Why did you chose the alternative iso? The answer will assist me, and other members of the forums, in helping you to solve your problems.

---

### Post by igor54 on 2007-08-20
> **gobbles414 said:**
> Hi igor54,

Why did you chose the alternative iso? The answer will assist me, and other members of the forums, in helping you to solve your problems.

I downloaded it (the alternative) from the ubuntu site because they described it as not including the Live CD (which I didn't need), and as having a text-based install, which would be handy for installing on some older PC's we have. I recall SuSE having a minimum RAM requirement for their graphical install, and assumed Ubuntu would be similar.

Just to fill you in, I'm not a Linux n00b - I've just been away from it for a few years. Comfortable with the command line, (first thing I installed was Eterm), sudo, etc. Last distro I ran full time was SuSE 8.4 (don't like the new SuSE distro, though - hence the decision to go with Ubuntu.

With regard to the problem, I've tried completely uninstalling OOo (via Synaptic), and re-installing, but the same error occurs. Also occurs when trying to install other pkges, too (envy, for example).

Hope that helps

Igor54

---

### Post by gobbles414 on 2007-08-20
Hey igor54,

I'm baffled. Sometimes a program that didn't install correctly will keep asking to be installed every time you're in Synaptic. However, the error message should stay the same.

Here is one easy thing you can try: enable backports by going system --> administration --> software sources --> updates --> unsupported updates (backports). This may force the update of some packages that have been broken.

Another possibility is there is a terminal command that you can use to delete all installer packages on your computer without deleting the installed programs themselves. Sorry, I can't remember the command at the moment.  

Lastly, you might try reinstalling Ubuntu from the standard ISO. I'm sorry that I haven't been more helpful.

---

### Post by marties on 2007-08-30
This thread solved the problem for a fresh install  [http://ubuntuforums.org/showthread.php?t=516162]("http://ubuntuforums.org/showthread.php?t=516162")

---

