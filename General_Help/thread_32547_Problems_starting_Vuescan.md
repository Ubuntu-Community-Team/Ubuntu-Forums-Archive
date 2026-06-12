---
title: "Problems starting Vuescan"
date: 2005-05-08
forum: General Help
---

### Post by Spoofhound on 2005-05-08
I've been running Ubuntu for about a month now and i'm really enjoying it. I've learned a lot from these forums, particularly the HOW-TOs which are a great help to a noob like me.

I'm currently dual booting with Windows, but have hardly used windows in the last month except when using my Nikon Coolscan IV scanner, and this is one of the last reasons i have for not making the full move to linux.

I now want to try the Linux version of Hamrick's Vuescan but have had real problems starting it in Ubuntu. Download and unzip went fine, but on starting from the terminal I get the following error

"error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

According to Hamrick's release notes and what I've found on Google, gtk can give problems starting Vuescan, but that this can be solved by setting the LANG environment variable to C. I've tried this, but no joy.

Is anyone using Vuescan in Ubuntu and can shed any light on this?

---

### Post by tread on 2005-05-08
libgtk1.2 isn't installed, by default, libgtk2.0 is. Fire up synaptic, and search for libgtk, and install the needed version.

---

### Post by Spoofhound on 2005-05-08
[QUOTE=tread]libgtk1.2 isn't installed, by default, libgtk2.0 is. Fire up synaptic, and search for libgtk, and install the needed version.[/QUOTE]

Excellent, first scan with Vuescan is already done.

Many thanks for the assistance

---

### Post by tojan on 2005-11-23
For me it doesn't startup at all. No error message or anything happens at all..
In the terminal it says; bash: vuescan: command not found
Both libs installed too.

---

