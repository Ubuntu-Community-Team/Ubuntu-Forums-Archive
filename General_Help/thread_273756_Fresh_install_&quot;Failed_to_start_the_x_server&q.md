---
title: "Fresh install: &quot;Failed to start the x server&quot;"
date: 2006-10-08
forum: General Help
---

### Post by eric.brissette on 2006-10-08
I've been running Dapper Drake on my laptop for a month, and decided to replace Windows XP with Dapper on my desktop, but the install isn't working out.

At the beginning of the installation, after the progress bar and checklist finishes, I get the following error: "Failed to start the x server" 

It gives a yes or no question that I can't quite read; it boots me to the command prompt before I can read the rest of the message.

I looked at
/var/log/Xorg.0.log
and the last line says Fatal server error: no screens found

in xorg.conf
Section Device, the driver is set to "ati"

I've got an ATI X800 XL PCIe, AMD 64, DFI Lanparty Ultra-D motherboard.

I've tried changing the driver to "vesa" but no joy, I can't startx.

Any help would be greatly appreciated.

---

### Post by eric.brissette on 2006-10-08
Well, I was able to finally get it installed, but I haven't been able to use the ATI drivers.. but I'll continue to work on it.

---

### Post by ballyhoo on 2006-10-12
don't know if this will help but it worked for me [http://users.bigpond.net.au/hermanzone/p7.html]("http://users.bigpond.net.au/hermanzone/p7.html")

---

### Post by mrgraz on 2006-10-14
I installed ubunutu in vmware on windows xp and then upgraded the install of ubunutu.  Then the gui would not work and got the message Failed to start the x server.  I followed instructions on the link [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html) and now its back up and running.  Thanks for the info:)

---

