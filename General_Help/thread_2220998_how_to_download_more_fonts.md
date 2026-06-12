---
title: "how to download more fonts"
date: 2014-04-30
forum: General Help
---

### Post by christon74 on 2014-04-30
Hello fellow Ubunters :)
I have not yet figured out to download more fonts to use with Openoffice (Or LibreOffice)
There is one particular font I would like to have: 'Garamond'
Any tips highly welcome.

Thank you in advance for time and trouble.

Christophe.

---

### Post by mcduck on 2014-04-30
The easiest way (if you only need the font for your own user account) is to download the font files, and then place them in *~/.fonts* directory. If the directory doesn't exist yet, you can just create it. You might need to log out and back again for some programs to find the font, but in most cases simply restarting the program is enough.

To install the font for all users on the system, you'd place it in */usr/share/fonts/truetype* instead, and then you should run "*sudo fc-cache -f -v*".

---

### Post by qamelian on 2014-04-30
It's also worth checking the Ubuntu repos in Software Center/Synaptic/(whatever package manager you prefer). The Garamond font is available there.

---

### Post by Joentokyo on 2014-04-30
If you have synaptic package manager installed, use the search function and use this search, "465 free TrueType fonts by Brian Kent".

---

