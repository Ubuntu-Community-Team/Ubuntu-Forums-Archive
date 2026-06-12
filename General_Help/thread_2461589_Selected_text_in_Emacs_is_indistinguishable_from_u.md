---
title: "Selected text in Emacs is indistinguishable from unselected text; how to fix this?"
date: 2021-05-03
forum: General Help
---

### Post by GwibberFooey on 2021-05-03
I have recently started using Ubuntu 21.04, and I am already encountering strange behavior when I use Emacs. When I open a buffer in the Emacs GUI, and then do the keystroke ```
C-x h
```, then the cursor reappears at the start of the buffer. But the strange thing is that there is no visual indication of any text having gotten selected. For comparison: in Gedit, if I hold CTRL and then press A, then all text in the file gets visually highlighted with an orange background. In Emacs, the text does seem to be getting selected, because I can do operations like kill or save-kill. But it seems like a bug, that there is no visual indication when some text gets selected. Is there anything I can do to get Emacs to visually indicate it, when text is selected?

---

### Post by Holger_Gehrke on 2021-05-04
If you're using Emacs in X you can set 'Highlight Active Region' in the Options menu. The same can be done with 'M-x transient-mark-mode'.

Edit: As far as I can tell this isn't activated by default because it gets distracting if you use mark in it's alternative function as a transient bookmark (see 'exchange-point-and-mark' (C-x C-x) which allows you to jump back and forth between two places in your text).

Holger

---

### Post by GwibberFooey on 2021-05-04
'Highlight Active Region' is only a partial solution. Apparently there is an Emacs configuration setting that controls the color of selected text, and it seems the default color of that setting is 'invisible'. The method of Micah Elliott from stack overflow, together with 'Highlight Active Region' solves the issue for me. [https://stackoverflow.com/questions/18684579/how-do-i-change-the-highlight-color-for-selected-text-with-emacs-deftheme](https://stackoverflow.com/questions/18684579/how-do-i-change-the-highlight-color-for-selected-text-with-emacs-deftheme)

---

