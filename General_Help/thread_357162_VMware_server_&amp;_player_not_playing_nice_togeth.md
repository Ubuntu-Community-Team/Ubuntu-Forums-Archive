---
title: "VMware server &amp; player not playing nice together"
date: 2007-02-09
forum: General Help
---

### Post by blacklobo on 2007-02-09
I understand that VMware server & player are picky about being installed at the same time.  I am trying to figure out which two version work well together.  Today I have:
VMware Server 1.0.0 build-28343
VMware Player 1.0.3 build-34682
I am not able to launch VMware Server.  I read that it is recommended that both programs use the same version.  The problem I noticed is that there is no 1.0.3 version for the server and I didn't see the 1.0.0 for the player out there to download.  Anyone have a suggestion?

---

### Post by veloce on 2007-02-09
My understanding was that you couldn't do it.  Installation of the second would disable the first (usually with a warning?)

Why do you want to have them both anyway?  Isn't server better in every respect to player?

Veloce

---

### Post by blacklobo on 2007-02-10
The player has a more streamlined view.  If you put the player on full screen you can't tell it is in a window.  However the server lets you create the virtual computers and add hardware to them.  So it would seem odd that the programs would be completely inoperable together.

---

### Post by LenzM on 2007-02-10
I'm not sure about Server, but I had this same problem with Workstation until I realized that Player is installed as part of Workstation.  Have you tried running 'vmplayer' from the command line?

---

### Post by blacklobo on 2007-02-10
History:
I installed Server first configured and built a WinXP virtual machine.
I then found VMplayer and installed it.


Present:
I can launch VMplayer successfully.  I am not able to launch VMserver anymore however.
I wouldn't really care about this but with out server I can't add virtual hardware (new network cards, USB devices, etc.) to the virtual PC.

---

### Post by veloce on 2007-02-11
I avoided VMPlayer by using rdp to connect to my VM Server virtual machines over the host only network.  However, this was more for consistency as I tend to have several remote machines from around the office running all the time.  There may be some performance issues doing it this way but I certainly haven't noticed any.  I also have a virtual firewall (IPCop) so that I can provide some limited connectivity to the work network (and internet when required).

---

