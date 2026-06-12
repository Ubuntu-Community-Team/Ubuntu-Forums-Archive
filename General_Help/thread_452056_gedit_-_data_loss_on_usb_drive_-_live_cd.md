---
title: "gedit - data loss on usb drive - live cd"
date: 2007-05-22
forum: General Help
---

### Post by TravMan63 on 2007-05-22
I've been testing ubuntu-ce 7.04, it's mostly going well.  (Also Kubuntu 7.04 and Ichthux 6.09)

I have been running the live cd, (installed os is XP pro) and using a usb drive with a text file for documenting my changes... learning etc.

However, on a recent system reset, the entire file was wiped out (0 bytes).  Luckily there was a backup that gedit made, however it was unreadable.  Windows chkdisk was able to 'fix' that (and rewrote to the usb drive (not a good idea))

The question is - (and I think I have an answer) - why did I lose the data?  I had saved the file.. then instead of  restarting normally - I hit the reset button.  

Is it possible that this data was in the swap file and/or wasn't closed with the umount during a normal system shutdown?  I could see losing the new data, but all of it (it had been saved and edited on windows systems also)

When I rebooted - I couldn't write to the usb drive in ubuntu - and a lock icon appeared on the files.
Rebooting to windows - stated there were disk errors.

Lesson learned: Always use the 'eject' option and/or shutdown properly

Insight appreciated.
Thanks...
TM

---

### Post by scrooge_74 on 2007-05-22
I think you answer the questions yourself

Tough luck!

---

### Post by Eric the Red on 2007-05-23
Lol, yeah kind of sucks but as for the lock icon I believe that you have to change the owner of the file. Then you can get to it.

---

### Post by TravMan63 on 2007-05-26
Two comments:

1) - The lock icon appeared on files I had previously edited/created.

2) - A similar occurance in Xubuntu with mousepad (? the text editor).  The machine stopped responding
(during a live cd session, and attempting to 'install' software) - but in this instance - no data was lost.

So - I'm guessing it's 1) XFCE, Mousepad, or luck .... that this occured.

---

