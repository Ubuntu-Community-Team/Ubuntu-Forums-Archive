---
title: "Wine keyboard focus"
date: 2005-04-23
forum: General Help
---

### Post by Jack000 on 2005-04-23
Hi, I'me very new to linux and have just switched from windows a few weeks ago.

I am trying to install photoshop but wine seems to be having keyboard focus problems. I have tried wine in managed, unmanaged, and desktop modes, but without success, the input fields remain empty when I type.

I understand that this is a common problem in wine, so if there is anything that I'm missing, I'd appreciate the help.

thank you  :smile:

---

### Post by nick58b on 2005-04-25
Same problem for me, except I'm trying to install Acrobat 5 Pro (need full pdf form support).

I did a few searches in this forum and google, but I could only find the "use desktop mode" answer, which does not work.  What is sad is that the mouse works, so I'm typing stuff into gedit and copy/pasting into acrobat :(

BTW, I'm using a USB keyboard through a KVM switch, if that makes a difference.


*edit* keyboard works fine (in all modes) after the install

---

### Post by WirelessMike on 2005-05-24
Same here.

Any relief on this?

---

### Post by WirelessMike on 2005-05-24
> **Originally Posted by nick58b:**
**edit* keyboard works fine (in all modes) after the install*

Still broken here.  What did you install?

---

### Post by WirelessMike on 2005-05-30
I have discovered recently that the keyboard focus problem SEEMS to lie with the application "winesetuptk" available in the repositories.

Once I uninstalled winesetuptk, deleted the .wine directory under my profile and allowed wine to automatically set up the necessary directories under "drive c" (also created automatically), everything worked as advertised.

---

### Post by orb_nsc on 2005-06-10
Hi there, I'm having the same problem (successfully installed Blade Runner, but Wine doesn't let me use the keyboard in it), but I'm a bit confused by your solution.  It was Winesetuptk that configured Wine for me in the first place, so how would I configure it after removing that application and the .wine directory in my profile?  Wouldn't that pretty much kill my wine installation and fake_windows directory too?

---

