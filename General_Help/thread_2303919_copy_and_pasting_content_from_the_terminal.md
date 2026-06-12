---
title: "copy and pasting content from the terminal"
date: 2015-11-22
forum: General Help
---

### Post by zak3 on 2015-11-22
hey guys, 

is it possible to copy some content that's being displayed on the terminal and then paste it back into the terminal? 

I ask in the following context: when I run 'pidof ...' for a program (usually an internet browser with lots of tabs open etc) it gives me a string of PID numbers -- I want to know if its possible to just copy these numbers so that I can paste them after, for example, the 'kill' command so that I don't have to type all of them out individually which can be quite monotonous.... 

thanks!

---

### Post by grahammechanical on 2015-11-22
Yes. Select the text and then select the terminal's edit menu and select copy. There is also a paste option. Or Shift+Ctrl+C for copy and Shift+Ctrl+V for paste.

---

### Post by yetimon_64 on 2015-11-22
> **grahammechanical said:**
> Yes. Select the text and then select the terminal's edit menu and select copy. There is also a paste option. Or Shift+Ctrl+C for copy and Shift+Ctrl+V for paste.

Or a slightly quicker method is to highlight the text/code and press the _*middle*_ mouse button/wheel (dependent on mouse type) to paste the selected code. Cheers, yeti.

---

### Post by papibe on 2015-11-22
> **grahammechanical said:**
> 
[LIST]
[*]Select the text and then select the terminal's edit menu and select copy. There is also a paste option.
[*]Or Shift+Ctrl+C for copy and Shift+Ctrl+V for paste.
[/LIST]

+1

You can also copy and paste the selected text by getting the right click menu on the terminal.

Regarding your concern of saving time. The command 'killall' could do the 2 actions in 1 command. For example:
```
killall firefox
```
would kill all process named firefox.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Bucky Ball on 2015-11-22
> **yetimon_64 said:**
> Or a slightly quicker method is to highlight the text/code and press the _*middle*_ mouse button/wheel (dependent on mouse type) to paste the selected code. Cheers, yeti.

+1. You can even use this method between apps, say if you have some code on a website, highlight it, go back to the terminal, click middle mouse button. Voila! Works in reverse, too (from terminal to a new post here, for instance). :)

---

