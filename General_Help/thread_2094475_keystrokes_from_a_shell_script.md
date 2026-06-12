---
title: "keystrokes from a shell script"
date: 2012-12-13
forum: General Help
---

### Post by Randy Schilling on 2012-12-13
I would like to write, or have, a bash script called tab which, when executed,
implements the tab keystroke, in a specified active program.  The program,
I guess, would be a parameter of the script.

I would like to have such scripts for other keys, such as enter to select an item or
ctrl + c to copy the content of a cell into the cut/paste buffer, as well.   In short,
I want to be able to surf through a program with a script, do anything I might dream of doing with a sequence of keystrokes from my keyboard.

I suspect that I have not presented you with a well-defined idea.  If you could correct this, I guess tell me what I'm doing, I would be for grateful for that too.  If there are obstacle then please point out one or two of them and provide references.   I'm motivated and willing to work, just need some direction.

Thanks and many kind regards, Randy

---

### Post by Vaphell on 2012-12-13
*xdotool* to generate keypresses and manage windows
[http://manpages.ubuntu.com/manpages/lucid/man1/xdotool.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/xdotool.1.html)

management of the copy/paste buffers: *xsel*
[http://manpages.ubuntu.com/manpages/hardy/man1/xsel.1x.html](http://manpages.ubuntu.com/manpages/hardy/man1/xsel.1x.html)

---

### Post by Randy Schilling on 2012-12-14
Thanks Vaphell.  One more question.  Can the keyboard implemented programatically with a programming language like C++ or Java as as from the shell?
 
Randy

---

