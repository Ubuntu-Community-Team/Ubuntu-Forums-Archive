---
title: "grub savedefault not working"
date: 2007-02-02
forum: General Help
---

### Post by nickb834 on 2007-02-02
I use the following options in my menu.lst:

default      saved


and for each boot entry:

savedefault


For some reason this doesn't work, I went to a grub command prompt and typed:

savedefault

which was met with "Error 27: Unrecognized command"

Has this feature been removed from grub? I've used Ubuntu since hoary and this feature has always worked.

Help!

---

### Post by LotsOfPhil on 2007-02-02
Can you paste menu.lst? What you have written looks right.

---

### Post by nickb834 on 2007-02-02
I can post the menu.lst but given that Grub 0.97 on Feisty Fawn doesn't recognise the "savedefault" command when entered at a grub command prompt - negates any setting errors I made in the menu.lst

I've just tried running "savedefault" on an Edgy install at a grub command line and it worked ok.

Methinks something has changed in the Feisty version of grub that I'm not aware of.

---

### Post by nickb834 on 2007-08-15
Ok After a long Hiatus I tried this again on my Feisty system and it sill doesn't work.

Grub basically ignores the savedefault option and always boots Feisty. At the grub prompt if I enter "savedefault" this is returned "Segmentation fault (core dumped)"

This hasn't worked since after Edgy and frankly it's annoying the hell out of me, should I raise it as a bug or is this in hand?

My Menu.lst is absolutely correct (trust me on that) and has the option "default saved" near the top, each  OS choice has "savedefault" option.

Other than this Grub and the menu.lst work exactly as intended.

I'm tempted to force install the Edgy version of Grub just to get this working again.

Any thoughts?

---

### Post by Xyem on 2008-03-19
Just in case anyone comes across this while having the same issue, [savedefault is ( was? ) broken in GRUB 0.97]("http://linux.derkeiler.com/Mailing-Lists/Debian/2006-02/msg01467.html")

---

