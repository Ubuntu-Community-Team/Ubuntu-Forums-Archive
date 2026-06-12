---
title: "Picture card in Printer, can't see any pics"
date: 2007-05-15
forum: General Help
---

### Post by 90Brougham350 on 2007-05-15
I have an HP Photosmart 7660. Feisty recognized the printer fine, but doesn't show any picture cards in the printer. The printer display shows a card, and the number of pictures, but I get nothing with Ubuntu. Am I missing something simple?

Brian

---

### Post by scott_g on 2007-05-15
> **90Brougham350 said:**
> I have an HP Photosmart 7660. Feisty recognized the printer fine, but doesn't show any picture cards in the printer. The printer display shows a card, and the number of pictures, but I get nothing with Ubuntu. Am I missing something simple?

Brian

It would be easiest to install the HP-toolbox.  It's a printer utility that allows you to access the printer's extra features like photo cards, scanning, ink levels etc.  So, install (using terminal or synaptic) python-qt3.  Then run hp-toolbox in the terminal.  You can also add this to your programs list by editing the menus and create a launcher.

Hope it helps,
Scott

---

