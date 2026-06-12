---
title: "Compatibility with Adobe Postscript"
date: 2007-04-22
forum: General Help
---

### Post by Flying_OE on 2007-04-22
Hi all,

I've been trying to solve this compatibility problem, but to no avail. Could kind soul help me check this out:

My system: Kubuntu Edgy (but this doesn't matter, since the error occurs in Ghostscript)
I printed a simple 2-line MS Word document printed from my friend's Windows XP-based PC. The printer used on that machine was Adobe's Generic Postscript Printer downloadable from their site.

When I copy the resultant PS file to my system, though, Ghostscript always reports the following error when I try to convert it to PDF (or to view it on screen):
%%[ Error: typecheck; OffendingCOmmand: defineresource ]%% ESP Ghostscript 815.02: Unrecoverable error, exit code 1

I'm also attaching the file with problem here. (BTW, I also tested with some other documents, but all of them exhibited the same error. So I'm just giving you the simply one with 2-lines of text.)

---

### Post by Lux Perpetua on 2007-05-13
> **Flying_OE said:**
> Hi all,

I've been trying to solve this compatibility problem, but to no avail. Could kind soul help me check this out:

My system: Kubuntu Edgy (but this doesn't matter, since the error occurs in Ghostscript)
I printed a simple 2-line MS Word document printed from my friend's Windows XP-based PC. The printer used on that machine was Adobe's Generic Postscript Printer downloadable from their site.

When I copy the resultant PS file to my system, though, Ghostscript always reports the following error when I try to convert it to PDF (or to view it on screen):
%%[ Error: typecheck; OffendingCOmmand: defineresource ]%% ESP Ghostscript 815.02: Unrecoverable error, exit code 1

I'm also attaching the file with problem here. (BTW, I also tested with some other documents, but all of them exhibited the same error. So I'm just giving you the simply one with 2-lines of text.)Did you solve your problem?

I'm seeing the text "Stupid Dark PANDA" and a few Kanji. 

I ran your file with the following command: ```
gs -sDEVICE=x11alpha -dBATCH resume.prn
```I'm puzzled that it didn't work for you. Make sure the file wasn't corrupted. (For example, opening the file in a text editor and saving it, even without modification, would probably corrupt it.)

---

