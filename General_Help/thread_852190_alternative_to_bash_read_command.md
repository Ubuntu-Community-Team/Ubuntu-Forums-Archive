---
title: "alternative to bash read command?"
date: 2008-07-07
forum: General Help
---

### Post by leptogenesis on 2008-07-07
I'm trying to write a shell script that reads input from stdin.  The input could be quite long--perhaps requiring more than one line in the terminal to display it.  

"read" does the job, but not well.  First, arrow keys don't work; there's no way for the user to go back and insert something into what he's already typed.  Backspace does work, but if the user types enough that the input drops down to the next line, he can backspace all the way to the left edge of the terminal, but once there the cursor won't jump back to the previous line.  It will keep deleting characters, it just won't show the characters as deleted, nor does the cursor move.

I'd also like to avoid forcing the use of an external editor like vim; it seems like it should be possible to keep this in bash.

Any ideas?

---

### Post by blackhatbrigade on 2008-07-07
Don't mean to come up with a stupid answer, but just in case you hadn't considered it, maybe try a scripting language?  Something like perl or ruby would be able to handle what you're looking for... then again it's a little more in-depth to implement if you don't know the language already.

Sorry, I can't really help with the bash scripting.  I stick to Ruby normally.

---

### Post by ghostdog74 on 2008-07-07
> **leptogenesis said:**
> I'm trying to write a shell script that reads input from stdin.  The input could be quite long--perhaps requiring more than one line in the terminal to display it.  


Any ideas?
you can try cat
```

echo "Enter some text, press Ctrl-D to quit"
cat >> outfile


```

---

### Post by leptogenesis on 2008-07-07
> **blackhatbrigade said:**
> Don't mean to come up with a stupid answer, but just in case you hadn't considered it, maybe try a scripting language?  Something like perl or ruby would be able to handle what you're looking for... then again it's a little more in-depth to implement if you don't know the language already.

Sorry, I can't really help with the bash scripting.  I stick to Ruby normally.

I probably should have said that I'm improving on a 1000+ line script written for ksh o_O

[QUOTE=ghostdog74]
you can try cat
```

echo "Enter some text, press Ctrl-D to quit"
cat >> outfile

```
[/QUOTE]

Sounded like a good idea, but I tried it and seems to have the same issue as with read.  :-/

Still looking for ideas...

---

### Post by dje on 2008-07-07
**EDIT: I should read the first post more carefully lol**

try this:
```
echo -n "Enter some text: "
read text
echo $text
```

hope that helps,
dje

---

### Post by blackhatbrigade on 2008-07-07
> **leptogenesis said:**
> I probably should have said that I'm improving on a 1000+ line script written for ksh o_O

Perfect way to learn another language!  Port some code!  Excited?  ...  yeah, I wouldn't be either. ;)  Good luck with the bash :)

---

### Post by ghostdog74 on 2008-07-07
> **leptogenesis said:**
> I probably should have said that I'm improving on a 1000+ line script written for ksh o_O



Sounded like a good idea, but I tried it and seems to have the same issue as with read.  :-/

Still looking for ideas...

seems like you want user to use a makeshift editor in *nix command line (terminal) ?? 2 ideas
1) use menu like options. Give them menus and choices to do change lines, instead of asking them to type themselves. Then at the backend, use sed/awk or simple bash to change the file.
2) Use a graphical interface. If you can program a web page, all the better.

---

### Post by patrick295767 on 2012-05-27
I would be you, I would use python. It needs only 5 lines for that 

replace read txt

by

VAR=` python filepromtpread.pl  `

---

### Post by sisco311 on 2012-05-27
Old thread closed.

[[img]http://ompldr.org/tYzBtcQ[/img]](http://ompldr.org/vYzBtcQ)

---

