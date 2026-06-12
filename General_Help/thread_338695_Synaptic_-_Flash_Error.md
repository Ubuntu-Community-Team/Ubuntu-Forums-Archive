---
title: "Synaptic - Flash Error"
date: 2007-01-14
forum: General Help
---

### Post by Skidpad on 2007-01-14
Greetings all. I believe I've bungled up my Flash plugin earlier today trying to install the FlashPlayer 9 b2.  I now can't see anything once I click the error message below and actually get into Synaptic - no packages or anything.

Here's the error:  
[B]E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/B]


**edit**: I just looked through my document/download folder, and there is a 170mb file called "core.4653" that contains "Program Crash data".  The time stamp on it relates to my Flash troubles mentioned above...

I'd love to be able to use Synaptic again; any comments/help greatly appreciated!

---

### Post by rabid9797 on 2007-01-14
if your using firefox 2.0 just download flash directly from adobe(or go to a site with flash), you can download and setup flash through firefox easily and its alot faster and less painful than trying to fix this error.

---

### Post by Skidpad on 2007-01-14
> **rabid9797 said:**
> if your using firefox 2.0 just download flash directly from adobe(or go to a site with flash), you can download and setup flash through firefox easily and its alot faster and less painful than trying to fix this error.

Here's my terminal output (same error) when trying to install Flash:
[B]
jim@LinuxLaptop:~$ sudo apt-get install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.
jim@LinuxLaptop:~$ 
[/B]

:???:  I'm lost

---

### Post by Skidpad on 2007-01-14
[SIZE=2]Well, "I" seem to have fixed it...Thanks to **lime4x4**and his post from Dec.
([http://www.ubuntuforums.org/showthread.php?t=310548&highlight=E%3A+The+package+flashplugin-nonfree+needs+to+be+reinstalled%2C+but+I+can%27t+find+an+archive+for+it.+Internal+error+opening+cache+%281%29.+Please+report](http://www.ubuntuforums.org/showthread.php?t=310548&highlight=E%3A+The+package+flashplugin-nonfree+needs+to+be+reinstalled%2C+but+I+can%27t+find+an+archive+for+it.+Internal+error+opening+cache+%281%29.+Please+report).)

Anyway, as lime4x4 did, I deleted the following text from the /var/lib/dpkg/status file:

[B]Package: flashplugin-nonfree
Status: purge reinstreq half-installed
Priority: optional
Section: web
Version: 9.0.21.78-3v1ubuntu0[/B]

I then ** sudo aptitude install flashplugin-nonfree** and let it install.  When it finished, I had this error (**automatic installation failed due to network problems or upstream changes**) but Synaptic now works again.

:D[/SIZE]

---

