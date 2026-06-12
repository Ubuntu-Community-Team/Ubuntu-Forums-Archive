---
title: "Having troubles installing winrar."
date: 2007-05-15
forum: General Help
---

### Post by HybridGhost on 2007-05-15
I have the install.exe on my desktop, I go to run it and it says..

"Cannot open /home/jory/Desktop/WinRARCrystal.exe: No application suitable for automatic installation is available for handling this kind of file."

So I try and run it through the terminal and I get this...

jory@jory:~/Desktop$ ./WinRARCrystal.exe

bash: ./WinRARCrystal.exe: Permission denied

jory@jory:~/Desktop$ 


Pernissions are set to "Read and Write"

Can someone explain why I can't install this?

Regards,

---

### Post by bukwirm on 2007-05-15
Several Reasons:
1. The permissions must be set to read and execute for something to be runnable.
2. A .exe file is probably for windows, and will not do anything under linux.
3. The better way to install applications under linux is to install from the repositories using [Synaptic]("https://help.ubuntu.com/community/SynapticHowto") or [aptitude]("https://help.ubuntu.com/community/AptitudeSurvivalGuide").

---

### Post by HybridGhost on 2007-05-15
Doh >.< I forgot about that... Thanks a lot.

Regards,

---

