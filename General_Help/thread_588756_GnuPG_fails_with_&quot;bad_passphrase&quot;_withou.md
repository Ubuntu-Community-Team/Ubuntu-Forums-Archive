---
title: "GnuPG fails with &quot;bad passphrase&quot; without prompting for passphrase"
date: 2007-10-23
forum: General Help
---

### Post by utkjamie on 2007-10-23
I've been having problems with gnuPG under Kubuntu in which gnuPG fails decryption in both Kmail and Thunderbird/Enigmail with a "bad passphrase" error without ever prompting me for a passphrase.

Since the problem is occurring in both Kmail and Thunderbird, I suspect that the problem may be with gnupg-agent. Under Kgpg I check a box to "Use gnuPG Agent," click Apply and then Ok. When I open up the configuration again the box is unchecked.

gnuPG Agent is installed, so I'm not sure what's going on here.

---

### Post by mactimes on 2008-04-15
Solution:

sudo apt-get install pinentry-qt

Regards,
mactimes

---

### Post by cdyson37 on 2008-06-04
Did that solution work? I had problems with Thunderbird/enigmail. Fixed them by unchecking the use agent option and changing the shortcut to thunderbird to read

/usr/bin/env GPG_AGENT_INFO= thunderbird %u

---

### Post by tubbygweilo on 2008-06-25
utkjamie,
I have found that when using ThunderBird version 2.0.0.14 (20080505) and Enigmail 0.95.0 under Ubuntu 8.04 if entering an incorrect pass phrase I am indeed prompted to try again and all this with the "Use gnuPG Agent" option **Not** selected. 

I know I am using the Gnome desktop but I just thought you would like to know.

---

