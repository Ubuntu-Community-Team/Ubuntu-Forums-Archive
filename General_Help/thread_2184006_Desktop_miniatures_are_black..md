---
title: "Desktop miniatures are black."
date: 2013-10-27
forum: General Help
---

### Post by QNEPFmr on 2013-10-27
Hi all, 

I have Xubuntu 13.10 installed and ran Bleachbit to clean things up.
After a reboot I found that pictures being saved on my desktop won't show themselves as a little picture anymore.
The're little black squares.

Does anyone know how to get the previous setting back?

Greetzz.

---

### Post by ibjsb4 on 2013-10-27
Bleachbit is usually worry free so I thought this may be a new 13.10 bug, but not finding any at launchpad.

[https://launchpad.net/bleachbit](https://launchpad.net/bleachbit)

edit omit

edit2:  [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo dpkg --configure -a && sudo apt-get -f install
```

Look for errors.

---

### Post by ibjsb4 on 2013-10-27
You can also sign up with Launchpad and ask the question at the above link, I have found good help at Launchpad.

going off line

---

### Post by QNEPFmr on 2013-10-27
I rebooted twice and the tiny pics are back, so I suppose I don't have to "sudo dpkg --configure -a && sudo apt-get -f install"?

Doing this tells me to remove these packages...

hyphen-en-us libreoffice-base-core libreoffice-help-en-gb
  libreoffice-help-en-us libreoffice-help-nl libreoffice-l10n-en-gb
  libreoffice-l10n-en-za libreoffice-l10n-nl libreoffice-math
  libreoffice-writer mythes-en-au mythes-en-us openoffice.org-hyphenation

What do you think? Leave them where they are?

---

### Post by philinux on 2013-10-27
> **QNEPFmr said:**
> I rebooted twice and the tiny pics are back, so I suppose I don't have to "sudo dpkg --configure -a && sudo apt-get -f install"?

Doing this tells me to remove these packages...

hyphen-en-us libreoffice-base-core libreoffice-help-en-gb
  libreoffice-help-en-us libreoffice-help-nl libreoffice-l10n-en-gb
  libreoffice-l10n-en-za libreoffice-l10n-nl libreoffice-math
  libreoffice-writer mythes-en-au mythes-en-us openoffice.org-hyphenation

What do you think? Leave them where they are?

I was just about to suggest a reboot. Just do this.

```
sudo apt-get autoremove
```

Apt will remove redundant packages.

---

### Post by QNEPFmr on 2013-10-27
Remove redundant packages?
I autoremoved my Libre-office writer with it...not really redundant imo.

---

### Post by philinux on 2013-10-27
> **QNEPFmr said:**
> Remove redundant packages?
I autoremoved my Libre-office writer with it...not really redundant imo.

Just reinstall it then. I've never had a problem with autoremove in the past. I do always check what it's going to do though.

---

### Post by QNEPFmr on 2013-10-27
I did, but it should not remove my writer, weird.

---

