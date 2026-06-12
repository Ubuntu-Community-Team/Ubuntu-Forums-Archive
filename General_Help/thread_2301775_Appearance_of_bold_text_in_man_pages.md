---
title: "Appearance of bold text in man pages"
date: 2015-11-05
forum: General Help
---

### Post by vasa1 on 2015-11-05
I want to know how to reduce the brightness of the **bold** text in *man* pages or to use some more restful shade of grey instead. 

This is for when I'm viewing man pages in my terminal (lxterminal or roxterm).

Thanks!

---

### Post by sudodus on 2015-11-05
I think you can change the preferences of your terminal emulator - change the high-light rendering to something you like better.

---

### Post by vasa1 on 2015-11-05
> **sudodus said:**
> I think you can change the preferences of your terminal emulator - change the high-light rendering to something you like better.

I'll try that but for now I dug out this code that does something when added to the end of my .bashrc:

```
man() {
    env LESS_TERMCAP_md=$'\E[01;38;5;74m' man "$@"
}

```
Now, I just have to mess with that line to understand what all those numbers do to see whether I can mute the blue a little more. 

BTW, *man termcap* claims that *termcap* is outdated and that one should use *terminfo* but that didn't do anything for me!

Edit: I can use the GUI of roxterm to change the color of bold text but can't do so in lxterminal.

---

### Post by Habitual on 2015-11-05
I like it!

---

### Post by sudodus on 2015-11-05
Do you want to create something general, or are doing it for yourself and one particular terminal emulator? If the latter, it should be easy with gnome-terminal, maybe not so easy with lxterminal ...

---

### Post by vasa1 on 2015-11-05
> **sudodus said:**
> Do you want to create something general, or are doing it for yourself and one particular terminal emulator? If the latter, it should be easy with gnome-terminal, maybe not so easy with lxterminal ...

It's just for me. I don't like bright colors and wanted to tone down the color of bold text in man pages.

I can get what I want with roxterm's gui or with the .bashrc code I posted earlier. I don't use gnome-terminal.

---

### Post by Habitual on 2015-11-05
worked for me in Terminator.

---

### Post by sudodus on 2015-11-05
It's a nice way to use ANSI escape sequences :-)

---

