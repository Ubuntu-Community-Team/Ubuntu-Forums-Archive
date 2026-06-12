---
title: "Do I need an upgrade or is there something wrong?"
date: 2007-07-20
forum: General Help
---

### Post by pjrettin on 2007-07-20
My system:

Feisty / AMD AthlonXP 2400 / 512mb ram / nvidia 7800GS video card.
Latest nvidia binary drivers installed - and yes, direct render = yes

The Problem?

General lack of system response.

Example:  

From a fresh reboot, I open up a 1.3mb text file with the text editor, grab the scroll bar and attempt to scroll down into the file... the result is that the cpu goes nuts, the app grays out and basically craps out.


I don't remember this type of thing happening back when I had edgy installed.

---

### Post by ddrichardson on 2007-07-20
Run top in a terminal and see if something else is hogging resources when you do this.

---

### Post by pjrettin on 2007-07-20
> **ddrichardson said:**
> Run top in a terminal and see if something else is hogging resources when you do this.

Just the text editor...

---

### Post by ddrichardson on 2007-07-20
Is it only with gedit?

---

### Post by pjrettin on 2007-07-20
> **ddrichardson said:**
> Is it only with gedit?

Well, I opened it up in a terminal with vi and had no problem paging down to the end.

---

### Post by ddrichardson on 2007-07-20
You don't have Scintilla do you? The reason I ask is that there are a couple of bug reports on [gedit's bugtracker]("http://bugzilla.gnome.org/show_bug.cgi?id=408132") reference large files scrolling slowly and using 100% CPU.

---

### Post by pjrettin on 2007-07-20
> **ddrichardson said:**
> You don't have Scintilla do you? The reason I ask is that there are a couple of bug reports on [gedit's bugtracker]("http://bugzilla.gnome.org/show_bug.cgi?id=408132") reference large files scrolling slowly and using 100% CPU.

I don't even know what Scintilla is :P

---

### Post by ddrichardson on 2007-07-20
No matter - the bug report states that large files (which at 1.5MB is a large text file) seem to cause those symptoms.

I'd try another text editor until the bug is addressed.

---

