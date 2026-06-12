---
title: "confusion with terminal"
date: 2012-11-16
forum: General Help
---

### Post by usernamer on 2012-11-16
When I use the terminal, lines generally start with:

user@ubuntu:~$ 

and you type in your commands etc. but sometimes this disappears and there's nothing at the start of each line (i.e. if you open the terminal and type in grep -l file). 

The only way I know to get back to the 'normal' mode with user@ubuntu:~$ starting each line is to close the terminal and re-open it. I've tried typing stuff in i.e. exit, quit, q etc. but it just seems to ignore anything you enter... 

is there a way to get back to the normal mode / whatever it's called? Or have I effectively broken it  and just need to make sure I do things right so I don't get into that situation (which I guess would come with experience)...

any help on this would be great.

---

### Post by Vaphell on 2012-11-16
That usually means that your command is broken for whatever reason. When that happens, press ctrl+c to interrupt whatever is going on.
*grep -l file* is not complete, there are no files listed (and you get into the interactive mode where you type scanned text by hand), assuming the first word is the pattern you want to find
*grep -options pattern file(s)*

---

### Post by efflandt on 2012-11-16
The Ctrl+C thing usually helps if something is running that you want to stop, or sometimes Ctrl+Z then enter if something interactive is waiting for input.  Or Ctrl+D closes a terminal.

But if you **less** or **cat** certain files that turn out to be binary, and the binary code includes something that the terminal takes to be ansi screen codes to change text or background color or the prompt, you can sometimes end up with no prompt, sometimes no echo of characters typed, or sometimes totally black on black (or white on white) invisible text.  In that case you can type (blindly if you cannot read it):

```
stty sane
```hit Enter, and your screen should return to normal.

---

### Post by Lightstar on 2012-11-17
Ctrl+C is what I use the most as well, it seems to break / stop whatever the system is doing in the terminal.  And then it goes back to the user@system

---

### Post by Wim Sturkenboom on 2012-11-17
> **usernamer said:**
> ...(i.e. if you open the terminal and type in grep -l file). 
That command does exactly what you tell it to do ;
Grep takes (optional) options, a string to search for and an optional file specification. If you omit the last one, like you do, it will read from standard input (your keyboard).

As others stated, <ctrl>c will get you out.

I'm not on a Linux system to demonstrate.

---

### Post by usernamer on 2012-11-17
Thanks guys, I'd actually used ctrl C for stopping stuff (like infinite or just big loops) before, so surprised I hadn't tried that. Worked like a charm

Big ty for the help.

---

