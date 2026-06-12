---
title: "How to create a keyboard shortcut for a specific unicode sign?"
date: 2024-10-26
forum: General Help
---

### Post by Wise Ferret on 2024-10-26
I need to create a simple keyboard shortcut for the unicode sign "&#8211;" (en-dash, U+2013) that will work always, independently of the currently selected keyboard layout.
How can I do that in ubuntu?

---

### Post by grahammechanical on 2024-10-26
I think that you are asking for the impossible. 

For example, with the English (UK) keyboard layout if I hold Ctrl + Shift and the press U followed by the four character Unicode (2013) and press Space I will will get the en dash. Here it is –  But if I change keyboard layout to Greek (Polytonic) and repeat the action I get 2013  That is it. 

Another example. The Unicode for the Euro currency sign is U+20AC   Here it is with the English (UK) keyboard layout  € Now I try with the Greek keyboard layout  20&#913;&#936;  That is what happens. The en dash is part of the General Punctuation Character block.

I only have the two keyboard layouts installed. So, I cannot experiment any further.

Regards

---

### Post by Wise Ferret on 2024-10-26
I tried using the command:
> xdotool key Shift+Ctrl+u 2 0 1 3 space
And it works well on terminal, but not when I use it in a custom keyboard shortcut. My guess is that the fact that I already have to use modifiers to activate the shortcut interferes with the process. xdotool's argument ---clearmodifiers should work around that, but unfortunately it does not work.

---

