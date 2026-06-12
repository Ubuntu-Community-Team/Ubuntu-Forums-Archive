---
title: "No Display - Monitor turns off on Ubuntu start"
date: 2006-11-27
forum: General Help
---

### Post by satcross on 2006-11-27
My monitor turns off when Ubuntu starts.
My monitor works when I turn on computer.  I can see start up, bios, etc.  When Ubuntu starts to load, it shows the first couple of checks where Ubuntu ok;s processes.  Then the monitor, turns off.
Obviously there is something wrong in the Ubuntu set up, but I have no access to Ubuntu to fix it.
Does this mean I have to reinstall?  And when I do reinstall, how do I set up so monitor will work?
Any suggestions appreciated.

---

### Post by xfile087 on 2006-11-27
> **satcross said:**
> My monitor turns off when Ubuntu starts.
My monitor works when I turn on computer.  I can see start up, bios, etc.  When Ubuntu starts to load, it shows the first couple of checks where Ubuntu ok;s processes.  Then the monitor, turns off.
Obviously there is something wrong in the Ubuntu set up, but I have no access to Ubuntu to fix it.
Does this mean I have to reinstall?  And when I do reinstall, how do I set up so monitor will work?
Any suggestions appreciated.

I probably don't have the same problem as you, but similar. I have an Intel Mac Mini and sometimes while booting I will select Linux and the monitor will go off. I have to reboot and usually the next time I select Linux it works this time. Annoying.

Have you tried rebooting a few times? Does the LiveCD boot okay?

---

### Post by satcross on 2006-11-27
Rebooting does not help.  Problem happens every time.
It seems to me that Ubuntu switches video mode (from what the PC uses)as it goes to user login display.
Thanks for the suggestion

---

### Post by satcross on 2006-11-28
Partly worked this one out.  I am adding this to help anyone else searching on this prob
  Going into bash means the monitor restarts.
Then reconfigure xserver, so that the video card is properly detected.  Use sudo dpkg-reconfigure xserver-xorg
What I forgot to say in previous post was that this was a new installation of Ubuntu. 
Therefore the problem I have now is that I cannot start Gnome yet as the installation process needs to complete.
Does anyone know what instruction to enter in terminal for install to complete?

---

### Post by Johnsie on 2006-12-06
I have this same problem too... I've already reconfigured xserver and that hasnt fixed it.

---

### Post by UnknownFear on 2008-05-04
I have this EXACT same proble, and I have reconfigured the xserver. It started to happen after I updated from 7.10 to 8.04. Any help on this will be GREATLY appreciated. I don't want to have to restart 7.10.

---

