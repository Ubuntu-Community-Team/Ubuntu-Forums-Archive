---
title: "copy or cut of text seem to have no effect"
date: 2008-04-30
forum: General Help
---

### Post by stephanecharette on 2008-04-30
Looks like both copy and cut of text sometimes doesn't work.  The example I just ran into:

Several instances of gedit open.  I highlight and copy several words of plain English-language text.  Move mouse to a new gedit window, and hit paste.  But instead of the line I copied, it instead pastes something from hours ago that is somehow still in the clipboard buffer.

I tried to copy/cut using the following:

1) CTRL+INS
2) CTRL+C
3) CTRL+X
4) clicking on Edit->Cut
5) clicking on Edit->Copy
6) right-mouse-clicking the highlighted text and selecting Copy
7) right-mouse-clicking the highlighted text and selecting Cut

Pasting was done using:

1) SHIFT+INS
2) CTRL+V
3) clicking on Edit->Paste
4) right-mouse-clicking and selecting Paste

Same result no matter how the text was copied, cut, or pasted.  I just couldn't get any new text into the clipboard buffer.  Also tried to copy/cut a URL from Firefox into a gedit window with the same result.  Looks like the clipboard wasn't latching to the new text.

The only thing that "solved" it was to reboot.

8.04-64bit, upgraded from 7.10 three days ago.  Uptime when the problem happened was probably 2 days.

$ uname -a
Linux stephane-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

---

### Post by fjgaude on 2008-04-30
I've been using Hardy for weeks and have not had troubles cutting, copying, pasting text from one program to another, even going through VMware virtual OSs.

It might be wise to enter a bug report of your issues.

---

