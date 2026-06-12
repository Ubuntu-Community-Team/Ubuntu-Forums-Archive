---
title: "Hibernation problem"
date: 2007-06-08
forum: General Help
---

### Post by sdrawkcaBdepyTI on 2007-06-08
I tried hibernation for the first time, and found it behaved more like a shutdown than a hibernation - everything works fine when I come back up, but nothing is remembered from my desktop state. Here's a (possibly) useful snippet from /var/log/messages:

Jun  8 08:14:19 I-SEE-YOU gnome-power-manager: (morgoth) An unknown error occured code='32' quark='g-exec-error-quark'
Jun  8 08:14:19 I-SEE-YOU gnome-power-manager: (morgoth) Resuming computer
Jun  8 08:14:19 I-SEE-YOU kernel: [ 2676.601251] ohci1394 does not fully support suspend and resume yet

Does this mean that my firewire driver is incompatible with hibernation? 
Is there any fix available for this?

And sorry if I'm missing something obvious here - I'm still a newbie. 


Thanks in advance!

---

### Post by locksmart342 on 2008-01-07
I have the same problem as u.

---

