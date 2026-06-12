---
title: "finding installed programs"
date: 2004-10-26
forum: General Help
---

### Post by chibo on 2004-10-26
where can i find programs i just installed by using synaptic?

---

### Post by SFN on 2004-10-27
In the banner across the various packages, click the left most header (the one above the little boxes. Clicking it once should turn the boxes solid. Solid boxes indicate installed packages. You should now have all of your installed packages at the top.

---

### Post by chibo on 2004-10-27
ok, thanks.  next question is how do i manage to start those programs. i found something in /usr/bin/ -directory. should i run them from there?

---

### Post by shufla on 2004-10-27
Hello,

Daemons are usualy started via /etc/init.d/daemon-name start (Ubuntu package managment system is starting them after installation and enabling them to start at boot) or via inetd superserver.

If you want to start user-space program, type it's name in terminal or in "Run..." (Alt-F2 AFAIR) in Gnome.

Best regards,
Lukasz Nowak

---

### Post by HungSquirrel on 2004-10-27
*which programname* and/or *whereis programname* are two commands that can help you find things you've installed.  apt installs most binaries to /usr/bin .  I've found that running something from /usr/bin will usually work.  However, many of the packages you install automatically add entries to your Applications menu, so you might want to look around there first.

---

### Post by kyle on 2005-02-02
Thanks, that helped alot

---

### Post by axcairns on 2005-02-02
[QUOTE=kyle]Thanks, that helped alot[/QUOTE]
 You can find out what files a package installed by looking at the properties of the package in synaptic. Usually the ones that are listed in a bin directory are your executables.

Cheers,

Allan

---

