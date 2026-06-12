---
title: "Tab lost in copy/paste into terminal"
date: 2019-04-30
forum: General Help
---

### Post by vschulz on 2019-04-30
I am unable to copy and paste a tab from eg gedit, calc , writer into a terminal (gnome terminal or terminator).  The tab just disappears, eg "Asdf	jkl" becomes "Asdfjk". Spaces are not lost.  Strangely, tabs are not lost when copying from one terminal window to another.  I believe that this is a new behaviour in the last few weeks possibly due to a recent update since I never noticed it before.  I am running Ubuntu 16.04.6 LTS.  This is a big problem since it can create garbage when copy pasting.
Thanks for any assistance.

---

### Post by Impavidus on 2019-04-30
When you type or paste a tab at the command line, the shell attempts to complete a filename. It doesn't matter whether you type or paste it, two different things to the terminal, just the same for the shell. For example, when I paste **Down<tab>foo** on my command line, it gets expanded to Downloads/foo, as Downloads/ is the only file/directory starting with Down. I would be surprised if it hadn't worked like that for decades. If filename expansion fails, the tab just disappears.

You can type a tab in the terminal, just not at the command line.

You write you can copy a tab from one terminal to another. How do you get a tab in that first terminal?

---

### Post by oldrocker99 on 2019-04-30
Also, you can highlight text and paste it by clicking the middle mouse button. Along with directory completion with TAB, one of the superior things about Linux.

---

### Post by Holger_Gehrke on 2019-04-30
I don't think it's the terminal swallowing the tab-characters, it's the shell. When I paste into nano in a terminal, the tabs get pasted, if I paste into the shell they get lost. Since the tab has a function in an interactive shell (auto-completion), that's not all that surprising. You can't enter a tab in bash without hitting 'ctrl-v' ('use next character verbatim') before it. If you examine the characters pasted from one terminal to another, you will probably find that the tab has been converted to multiple spaces.

Holger

Edit: Damn, ninja'd **twice** ...

---

### Post by vschulz on 2019-04-30
Thanks, that is very informative.  I inserted a tab into the terminal using control v control i.  I was incorrect about the tab being maintained, it appears that it is converted to four spaces that looked like a tab.

---

### Post by vschulz on 2019-04-30
Two more quick points...  
Using the middle mouse button does not affect the auto-completion, the tab is still lost.
The auto-completion can be turned off for the terminal session by entering
bind 'set disable-completion on'
and then the tab gets pasted properly and is retained.  The auto-completion can then be reverted back by entering
bind 'set disable-completion off'
and then the tab is again lost, and you get auto-completion back.

---

