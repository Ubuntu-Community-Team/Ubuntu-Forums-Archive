---
title: "Ed2k/Overnet core and ed2k_gui on Ubuntu Hoary?"
date: 2005-08-29
forum: General Help
---

### Post by Panthios on 2005-08-29
Hi.
I have been running Debian testing before I switched over to Ubuntu.
I have always liked the Overnet core client: [http://forum.edonkey.com/viewtopic.php?t=69145](http://forum.edonkey.com/viewtopic.php?t=69145) and ed2k_gui: [http://ed2k-gtk-gui.sourceforge.net/download.shtml](http://ed2k-gtk-gui.sourceforge.net/download.shtml) - cause I can use the core without the gui if I like, and it has always been running very fast on my system.

But can I install them on my Ubuntu system? Someone told me that I shouldn't mix Debian packages into the system.
What to do?

---

### Post by arnieboy on 2005-08-29
[QUOTE=Panthios]Hi.
I have been running Debian testing before I switched over to Ubuntu.
I have always liked the Overnet core client: [http://forum.edonkey.com/viewtopic.php?t=69145](http://forum.edonkey.com/viewtopic.php?t=69145) and ed2k_gui: [http://ed2k-gtk-gui.sourceforge.net/download.shtml](http://ed2k-gtk-gui.sourceforge.net/download.shtml) - cause I can use the core without the gui if I like, and it has always been running very fast on my system.

But can I install them on my Ubuntu system? Someone told me that I shouldn't mix Debian packages into the system.
What to do?[/QUOTE]
try download and installing them with 
sudo dpkg -i <package_name>
if there are any errors or dependency problems, dpkg will let u know. u can download and install the deps (if they are lib dependencies, apt-get them dont try to install debian debs). if there are any irreconciliable deps, dpkg will tell u that too. if some of the deps are debian specific, well then hard luck what can I say?
u can give it a try though. nothing wil break. even if a couple of broken packages get installed, u can always remove them from synaptic (in the broken packages section)

---

### Post by Panthios on 2005-08-29
Alrighty, thank you.
No dependencies problems.

So, a general rule, I can install Debian packages aslong they don't cause any dependencies problems?

Best regards

---

### Post by arnieboy on 2005-08-29
[QUOTE=Panthios]Alrighty, thank you.
No dependencies problems.

So, a general rule, I can install Debian packages aslong they don't cause any dependencies problems?

Best regards[/QUOTE]
yes u can but make sure they are not lib or dev packages cuz that might break your system.

---

