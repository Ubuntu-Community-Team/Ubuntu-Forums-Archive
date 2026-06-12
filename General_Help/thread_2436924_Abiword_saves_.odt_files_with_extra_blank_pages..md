---
title: "Abiword saves .odt files with extra blank pages."
date: 2020-02-15
forum: General Help
---

### Post by 2CV67 on 2020-02-15
Hi!

I recently switched my little old Netbook from Ubuntu 16.04 to Lubuntu 18.04.
I am generally very pleased with the result - a new lease of life for outdated material.

One major part of Lubuntu is the use of lightweight Abiword instead of the very heavy LibreOffice.

I have a lot of LibO documents in .odt format & I was pleased to find Abiword would open, display & print them OK.

But when it came to modifying & re-saving .odt files, I started to hit problems.
Nearly every time I re-save an .odt, the next time I open it, it has an additional blank page.
Usually the new blank page is at the start, sometimes at the end & very occasionally both at the start & at the end...

Of course I can easily remove these blank pages to work on & print the document but when I again save & re-open the file, the blank pages are back.

On a couple of occasions it has even been impossible to re-open just-saved test documents, but that may be a different problem.

Saving as .abw files shows no problem.

I tried installing Abiword in Ubuntu 18.04.3 on my main PC.
Saving a new simple document as .odt, then closing & re-opening gives the same problem of additional blank pages.
So this seems to be a general problem.

Of course I can see possible solutions, including:
1. Resaving all my old .odt's as .abw's
2. Switching my Lubuntu to LibO
but before doing either of those, I wonder if anybody knows about this problem & any potential solutions?

Surprisingly, there doesn't seem to be an active forum for Abiword (is there?).

Maybe I need to report this as a bug?

---

### Post by sudodus on 2020-02-15
In the developeing release, Focal Fossa to become Lubuntu 20.04 LTS, they are abandoning Abiword and start to provide LibreOffice. The reason is what you are talking about, the lack of maintenance of Abiword.

If you have a very old computer, you may prefer Abiword anyway, but be prepared to live with some bugs.

---

### Post by dragonfly41 on 2020-02-15
You could try pandoc in a script which pipes the doc to AbiWord through its command line options.

---

### Post by 2CV67 on 2020-02-17
Thanks for those comments.

I decided to try switching to LibO again.
I was surprised to find I could install just Writer rather than the whole LibO suite, without seeing how much that saved. (On the Netbook, as opposed to my main PC, I don't use any of the other parts of LibO).
The little old EeePC Netbook runs OK with LibO Writer & no more problems with extra pages.
I uninstalled Abiword.

So - end of story!

---

