---
title: "A3 printer truncates output to A4"
date: 2014-08-26
forum: General Help
---

### Post by frisket on 2014-08-26
I have a HP K7100 A3 printer with duplex attachment which is working fine with A4 paper using the latest HPLIP driver in CUPS.

It is not possible to print A3 using the same printer name in CUPS; that is, you can't just specify A3 paper and expect it to work, you have to set up a new printer name for the same connection, and edit the preferences to specify A3 paper. I have no idea why this is, but it's always been like that: support for printers that can take different paper sizes has always been missing in CUPS (or is that HPLIP? Unlikely, seeing as it's their printer).

So if my default (A4) printer name is foo, I also set up a foo-A3, a foo-Ledger, and a foo-Letter so that I can print on the different paper sizes I have to deal with. Stupid, and ought to be unnecessary, but that's the way it is.

Now, suddenly, my foo-A3 connection is truncating the output image to 297mm (the height of A4). That is, it starts printing the A3 page (which is 420mm high), but when it has printed 297mm, it stops and goes to the next page.

a. does anyone know why it's doing this

b. has anyone ever managed to get a CUPS-defined printer to print on A3 without the need to create a separate printer name for it?

This thread describes the identical problem, but someone closed it prematurely without a solution: [http://ubuntuforums.org/showthread.php?t=1266193](http://ubuntuforums.org/showthread.php?t=1266193)  (this post in effect reopens the case).

---

