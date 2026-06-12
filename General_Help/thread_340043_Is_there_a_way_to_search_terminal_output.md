---
title: "Is there a way to search terminal output?"
date: 2007-01-16
forum: General Help
---

### Post by Peepsalot on 2007-01-16
I want to know if there is a way to search through the previous output of the terminal, for occurences of a substring or regex match.  I know about using grep, but I am talking about searching the output that gnome-terminal saves for scrolling through(i have mine set to keep the last 4096 lines.)

I am using gnome-terminal simply because it is the default, but if there is another program that would allow me to do that, I have no problem switching.

---

### Post by 23meg on 2007-01-16
You can search even further back with the *history* command. ```
history | grep search_term
```

---

### Post by majoridiot on 2007-01-16
assuming you use bash as your default terminal, the hidden file ~/.bash_history is the history
buffer.  you can open it with gedit or whatever and scroll through, search, etc.

---

### Post by Moldz on 2007-01-16
He does not want to search the commands he typed, he wants the actual output.  Are you familiar with a program named screen?  It is a sort of "virtual terminal" that is very useful.  Among other things, it will let you search through the history.

It can be difficult to pick up at first, but once you understand what is does and how to use it, you will never login again without it.  Here's a link to the manual:

[http://www.delorie.com/gnu/docs/screen/screen_toc.html#SEC_Contents]("http://www.delorie.com/gnu/docs/screen/screen_toc.html#SEC_Contents")

---

