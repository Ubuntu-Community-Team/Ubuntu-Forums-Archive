---
title: "[SOLVED] Enlarge size of xterm when opened by a script"
date: 2006-10-31
forum: General Help
---

### Post by kent41 on 2006-10-31
Hi 

Is it possible to enlarge an xterm window ( 80 X 24 ) when started from a script?
I have a script displaying data and it wraps I would like to extend the size so the data displayed line by line does not wrap.

Is there an xterm config file I could change ?

Also can the "echo" command print to the terminal in** BOLD**

---

### Post by kent41 on 2006-10-31
The part about enlarging the xterm window size has been solved
by

[this]("http://www.ubuntuforums.org/showthread.php?t=289632")

I still need to know if text in an echo command can be made bold.

This form is great.\\:D/

---

### Post by po0f on 2006-10-31
kent41,

You will want to look up *escape sequences*.  Something like the following should echo text in a bold white font:
```
#!/bin/bash
echo -e "\033[1;37mShould be bold and white\033[00m"
```

The **\033** sends a signal to bash saying whatever follows is a special sequence of characters it should interpret rather than directly display.  **1;37m** is the code for white, bold text.  The **\033[00m** "resets" the terminal to print regular text.  If you don't do that, you'll have weird stuff printed for the remainder of the shell's life, or until you give it another escape sequence.

In the above command echo's **-e** argument is essential;  the escapse sequences won't be interpreted otherwise.

---

### Post by kent41 on 2006-10-31
> **po0f said:**
> kent41,

You will want to look up *escape sequences*.  Something like the following should echo text in a bold white font:
```
#!/bin/bash
echo -e "\033[1;37mShould be bold and white\033[00m"
```

The **\033** sends a signal to bash saying whatever follows is a special sequence of characters it should interpret rather than directly display.  **1;37m** is the code for white, bold text.  The **\033[00m** "resets" the terminal to print regular text.  If you don't do that, you'll have weird stuff printed for the remainder of the shell's life, or until you give it another escape sequence.

In the above command echo's **-e** argument is essential;  the escapse sequences won't be interpreted otherwise.


The sequence works great and I appreciate the explanation of the escape sequences. I was making changes and also printed in BOLD and black.

Thanks again for your interest in my question - Problem solved

---

