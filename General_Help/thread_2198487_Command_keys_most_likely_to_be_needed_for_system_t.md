---
title: "Command keys most likely to be needed for system tasks?"
date: 2014-01-09
forum: General Help
---

### Post by bcschmerker on 2014-01-09
I am in the process of specificating an upgrade keyboard for my Asus® CM1630-06 as part of an Ubuntu® installation in planning (specifically, 14.02b2 Trusty Tahr™, for debugging prior to system finalization at the release of 14.04.1-LTS to market).  The best available frame for a dedicated LinUX keyboard, as of January 2014, appears to be the up-to-126-key Unicomp® Model M1, used as of January 2014 for both a PC122 model (an Emulator with specific firmware for use with the stock libraries and drivers in Microsoft® Windows® 5-up) and several stock-replacement keyboard FRU numbers for EBCDIC terminals from International Business Machines Corporation; a 124-key configuration should cause the least trouble with most systems' stock BIOS keyboard code (which treats all submodels except the PC122 in the same manner as IBM® P/N 6450200, an 84-key Model F orig. sold with the IBM® P/NN 5170-0xx microcomputers).  I have not yet determined whether Scan Code Set 2 or 3 is default for CM1630-06 BIOS 0804.

I already plan on relocating a few keys from the 101- through 109-key ISO standard due to potential need for Reset and Enter keys in my anticipated configuration.  For a 124-key Model M, the top twenty-four keys are the most logical for Program Functions, Console Selection, Text colors/attributes, Cursor attributes &c; the cursor-control section will handle Insert/Copy, Delete/Cut, Program Attentions, directional Move/Mark, Rule/alt-Home, Page Up and Down, &c.  The far-left ten will handle, among other functions, Secure Attention/alt-System Request, Escape, and a single Control shift key.  TN3270 aside, what command keys are most likely to be needed in the Terminal for specific system tasks?  References would be appreciated.

---

### Post by 3rdalbum on 2014-01-09
> **bcschmerker said:**
> I am in the process of specificating an upgrade keyboard for my Asus® CM1630-06 as part of an Ubuntu® installation in planning (specifically, 14.02b2 Trusty Tahr™, for debugging prior to system finalization at the release of 14.04.1-LTS to market).  The best available frame for a dedicated LinUX keyboard, as of January 2014, appears to be the up-to-126-key Unicomp® Model M1, used as of January 2014 for both a PC122 model (an Emulator with specific firmware for use with the stock libraries and drivers in Microsoft® Windows® 5-up) and several stock-replacement keyboard FRU numbers for EBCDIC terminals from International Business Machines Corporation; a 124-key configuration should cause the least trouble with most systems' stock BIOS keyboard code (which treats all submodels except the PC122 in the same manner as IBM® P/N 6450200, an 84-key Model F orig. sold with the IBM® P/NN 5170-0xx microcomputers).  I have not yet determined whether Scan Code Set 2 or 3 is default for CM1630-06 BIOS 0804.

I already plan on relocating a few keys from the 101- through 109-key ISO standard due to potential need for Reset and Enter keys in my anticipated configuration.  For a 124-key Model M, the top twenty-four keys are the most logical for Program Functions, Console Selection, Text colors/attributes, Cursor attributes &c; the cursor-control section will handle Insert/Copy, Delete/Cut, Program Attentions, directional Move/Mark, Rule/alt-Home, Page Up and Down, &c.  The far-left ten will handle, among other functions, Secure Attention/alt-System Request, Escape, and a single Control shift key.  TN3270 aside, what command keys are most likely to be needed in the Terminal for specific system tasks?  References would be appreciated.

I don't think I've seen so many ® and ™ symbols on this forum before. That's got to be some kind of record. BTW, I don't think the internal codenames for Ubuntu releases are actually trademarks.

I think your post is in the wrong section (nothing about it has anything to do with Desktop Environments) and it's quite difficult to follow. It seems like you're saying you will be testing Ubuntu 14.04 and you want to know what keys are necessary or useful on the keyboard in order to use the terminal to debug Ubuntu 14.04.

The answer to that is: The regular modifier keys: Shift, Alt, Control and Super. Plus the Pr Sc key (SysRq) in case you need to kill the X server. Sorry I don't have any references and I couldn't tell you the keycodes or how to remap them to fit your unusual keyboards.

---

### Post by oldos2er on 2014-01-09
Moved to General Help.

---

