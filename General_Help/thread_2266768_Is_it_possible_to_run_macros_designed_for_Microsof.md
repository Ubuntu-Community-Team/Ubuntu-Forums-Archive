---
title: "Is it possible to run macros designed for Microsoft Office within Ubuntu?"
date: 2015-02-25
forum: General Help
---

### Post by SiddharthaWolf on 2015-02-25
Hi, I've been asked by my employer to do work involving some .bas macros. I usually use Ubuntu for all my work, but I'm not very experienced with macro usage and when trying to use these .bas macros in Libreoffice, have no idea how to get them running. I've been asked to use Windows for the work instead, but my Windows is being problematic, in addition to hideously slow and unworkable, so I was hoping to ask here as a last resort what I could do in this situation. Am I going to have to use Windows? Or is there an alternative on Ubuntu?

---

### Post by Holger_Gehrke on 2015-02-25
While both LibreOffice and MS Office use (a dialect of) Basic as macro languages, they are different. Especially the API for all office-specific functionality is completely different (LO uses the UNO-Library, which is language-agnostic, so you can write macros in any language that offers bindings for UNO; it's quite common to find extensions / macros for LO / OO / StarOffice written in Java, JavaScript or Python).

If the macros are supposed to work in MS Office, working on them in LO is not going to work. You might try to get MS Office running in Wine, if getting your Windows to behave is to much trouble.

---

### Post by sgage on 2015-02-25
My macros work fine in Word running under Wine.

---

