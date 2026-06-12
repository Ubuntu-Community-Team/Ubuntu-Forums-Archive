---
title: "running program at longin..."
date: 2007-03-14
forum: General Help
---

### Post by Mia_tech on 2007-03-14
I want to have superkaramba started everytime I login, I've tried to use the bootup-manager but doesn't have an option to load programs or services that are not showing in there, is there any other way to get a prgram running at login time?

Thanks

---

### Post by pandu.rs on 2007-03-14
system->administration->sessions->startup programs

---

### Post by Famicommie on 2007-03-14
System->Preferences->Sessions->Startup Programs->Add

---

### Post by Mia_tech on 2007-03-14
I use that on my laptop which I have ubuntu, but also have kubuntu installed at home and no sessions-->startup programs, do you know how to do it from kubuntu?

---

### Post by pandu.rs on 2007-03-14
For kde there is a folder ~/.kde/Autostart

create a symlink in there

ln -s <program>_name <link_name>

---

### Post by Mia_tech on 2007-03-14
> **pandu.rs said:**
> For kde there is a folder ~/.kde/Autostart

create a symlink in there

ln -s <program>_name <link_name>

what's a symlink? is that like a shortcut?

and I tried the "ln -s" command on top and doesn't seem to recognize it

---

### Post by Mia_tech on 2007-03-14
> **pandu.rs said:**
> For kde there is a folder ~/.kde/Autostart

create a symlink in there

ln -s <program>_name <link_name>

my bad for the previous post it does work misspelled.....now where it says programs do you have to provide the complete path or just the name, and also in link_name avobe you can give it any name or does it have to be the name of the program 

thanks

---

### Post by thriff on 2007-03-26
In Xubuntu from the menu:
Xfce->Settings->Autostarted Applications

---

