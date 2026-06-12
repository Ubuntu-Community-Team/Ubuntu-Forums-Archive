---
title: "enabling cyrillic input"
date: 2005-05-24
forum: General Help
---

### Post by artemstar on 2005-05-24
My goal was to enable cyrillic input in x applications

Following advice of Cyrillic-HOWTO I installed 
t1-cyrillic and xfonts-cyrillic packages

Everything seems to work fine but the following warning is shown each time I call xfontsel:
Warning: Missing charsets in String to Fontset conversion
Warning: Unable to load any usable font set

This same warning comes up if I try to close emacs editor without saving the edited file first (which is when "Save file Yes/No" window pops up). 

Does anybody know where the problem is?


My other problem is that cyrillic characters are not displayed properly in emacs, although cyrillics look right in xterm and in vi. Cyrillic-HOWTO suggests the following added to .emacs:

(standard-display-european t)
(set-input-mode (car (current-input-mode))
   (nth 1 (current-input-mode))
   0)

This does not help in my case. I am using emacs21 version. Anybody has an advice?

---

### Post by lorap on 2005-05-27
hi!
it's very simple.
firstly go to the keyboard settings.
once you've them open go to the second tab (layout) and just add any language you just ever need.
after what press ok.
then place the mouse over the panel at the top, press the right button and choose from the list icon with the flags (i'm not at the pc right now so can't say its name but you won't mistake).
to change tha languages press alt+alt or by the mouse clicking on the language bar.
have a nice day.
pavel

---

### Post by artemstar on 2005-06-26
Dear Pavel,
Thanks for the advice. 
Firstly, the "Missing charsets in String..." warning when running xfontsel is still there and it does not seem to depend on available keyboard modes.
Of course I installed the russian keyboard. This is how I can type russian in xterm, as I say in my original question. 
It did not help with emacs though: when in russian keyboard mode I get russian characters but the wrong ones, capitals and lowercases mixed. Could be some kind of unmatching encoding problem. So far I got around this by using Valery Alexeev's russian.el: I am now able to use his "russian minor mode" to switch to russian in emacs. One more annoying problem remains: when copy-and-pasting (midle button) cyrillic characters screw up.
There is definitely something else I am missing in teaching my emacs russian.
Any more suggestions?
Thanks
Artem

---

