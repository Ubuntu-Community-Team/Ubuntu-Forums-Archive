---
title: "Word Processor"
date: 2008-02-24
forum: General Help
---

### Post by Segstro66 on 2008-02-24
I'm getting very frustrated.  I used Open Office for the longest time in both Windows and Linux.  A few months ago I switched over to using just Ubuntu, no other distros or Windows, and since then I haven't been able to get dictionaries and all that working.  No matter what I try, I've looked at posts and I follow the advice but the program crashes while trying to download the dictionaries, thesaurus, hyphenation etc.  I'm not really asking for help with Open Office, I've given up on it, I've reinstalled the OS, the program many times, retried the same process and tried different ones... I'm done with that.  I don't need help with that anymore, I'm looking for an alternative.

I've downloaded and will try AbiWord, but I'm wondering what else there is out there.  My main problem with leaving Open Office is the print to PDF feature that I use a lot.  I don't have a working printer in Ubuntu, and so I always print to PDF and then email it or put it on a flash drive and print on another computer.  Those other computers are always Windows though and so it doesn't work unless it's a PDF.

Anyone have any other word processors or easy to install PDF creators?  I'm looking for both of them so I can try a lot of them and see what works best for me... computers are mainly personal preference I've found.

Thanks,

Matt

---

### Post by ENB on 2008-02-24
You might try this: [http://www.arsgeek.com/?p=1720](http://www.arsgeek.com/?p=1720)

It details printing to a "PDF Printer" using cups-pdf.

---

### Post by hugmenot on 2008-02-24
Why the verbosity?
AbiWord, Save as: "Potable Document Format PDF".

---

### Post by Segstro66 on 2008-02-24
I just wanted to add something to my old post, I was tinkering around in AbiWord and I found that it can indeed print to PDF, just not print, you can save it as a PDF file.  That's a huge plus and so I would still appreciate any advice that people have but AbiWord is quickly rising to the top of my list!

Matt

---

### Post by ENB on 2008-02-24
Well, if you follow the guide I gave you, it will tell you how to add a sort of "virtual printer" that outputs to PDF. So you could use that with OpenOffice for instance. And then print the PDF using evince?

---

### Post by Crafty Kisses on 2008-02-24
> **hugmenot said:**
> Why the verbosity?
AbiWord, Save as: "Potable Document Format PDF".

Yep.

---

### Post by Hagar Delest on 2008-02-26
> **Segstro66 said:**
> I switched over to using just Ubuntu, no other distros or Windows, and since then I haven't been able to get dictionaries and all that working.  No matter what I try, I've looked at posts and I follow the advice but the program crashes while trying to download the dictionaries, thesaurus, hyphenation etc.
For information, I've experienced that also, I fixed it by running OOo just once as root. You can also download the files and install them manually, see section 2 of that thread: [[Tutorial] Spell check and Language configuration](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=67).

Note that the PDF export in OOo keeps internal hyperlinks (like TOC, cross-references), I'm not sure other applications can (virtual printers cannot).

---

