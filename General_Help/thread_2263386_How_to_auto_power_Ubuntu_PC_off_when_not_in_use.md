---
title: "How to auto power Ubuntu PC off when not in use?"
date: 2015-01-31
forum: General Help
---

### Post by carmen2012 on 2015-01-31
My family uses Ubuntu 14.04 on our desktop and laptop computers.  I've been trying to reinforce to my kids to shutdown their devices at the end of the night to save on power but my kids are young and often forget.  As such, devices can sometimes be on for 24 hours in a day.

Rather than rely on the kids, is there any setting that can be enabled within Ubuntu that would perhaps power the desktop PC and/or laptop off when not in use for a certain period of time (eg 2 hours)?

Thank you

---

### Post by ajgreeny on 2015-01-31
You can certainly set the computer to either suspend, or even hibernate (if you enable hibernation), after a certain period of inactivity, but I'm not sure about shutting it down; the problem with that would be any programs that are left running would lose everything not saved whereas if hibernated, all would still be on disk for you when started next time.

---

### Post by carmen2012 on 2015-02-01
> **ajgreeny said:**
> You can certainly set the computer to either suspend, or even hibernate (if you enable hibernation), after a certain period of inactivity, but I'm not sure about shutting it down; the problem with that would be any programs that are left running would lose everything not saved whereas if hibernated, all would still be on disk for you when started next time.

I didn't realize that there was a difference between suspend and hibernation.  Does hibernation use even less power and are there downsides to it?

I went to dash, typed in power and got to the power icon.  Within there, there is an option to suspend after a certain period of activity but I don't see an option to hibernate.  Is that located somewhere else?

---

### Post by ajgreeny on 2015-02-01
You will have to enable hibernation to be able to use it.
See [http://ubuntuforums.org/showthread.php?t=2219403](http://ubuntuforums.org/showthread.php?t=2219403) for details of this, and how to find out if your machines will hibernate successfully before you make these changes by running **sudo pm-hibernate** in terminal.  You will also need as much swap as you have ram for hibernation to be successful.

The difference is that suspend still requires a small power supply to keep all your open applications running; if you use a laptop not plugged into a mains power supply, all will be lost if the battery runs down completely.

If you hibernate, everything open is put onto the swap partition and then retrieved when you restart.  It needs no power at all so all is safe, but beware if you dual boot as hibernating one OS and then booting the other can cause big problems.

---

