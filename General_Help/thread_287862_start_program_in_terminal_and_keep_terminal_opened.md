---
title: "start program in terminal and keep terminal opened?"
date: 2006-10-29
forum: General Help
---

### Post by loko on 2006-10-29
hello,

i want to start a program from the menu.
i chose "start in terminal" and this works, but if i close the program, then the terminal gets closed too.

what should i set to keep the terminal open after i close the program?

---

### Post by invalid on 2006-10-29
I am not sure this is possible. How about just opening the program from a terminal instead of the menu?

---

### Post by DaveBorealis on 2006-10-29
> **loko said:**
> 
what should i set to keep the terminal open after i close the program?
Hello,

If you open the terminal first and put an ' &' after the command, you'll get the command prompt back:
```
/usr/bin/firefox &
```

But even if you don't use the ' &', when you close the program the terminal will still be there.

Best regards,
Dave

---

### Post by loko on 2006-10-29
i did know this with the &, but it doesn't work.

the terminal gets closed if i use it with or without &.

---

### Post by llamakc on 2006-10-29
loko,

Open a Terminal from the menu.

Type the name of your program with the ampersand. The Terminal will not close.

Or are you trying to create a launcher that opens a Terminal, runs a program & leaves the Terminal open?

---

### Post by strabes on 2006-10-29
I think he wants to do the latter. I don't know how to do that sorry.

---

### Post by DaveBorealis on 2006-10-29
Yep, just like llamakc said, go to 'Applications -> Accessories -> Terminal'.
Type at the prompt something like 'gnome-calculator &' (without the quotes).
And the calculator will appear, and you can still use the terminal to run other commands.
Close the calculator, and the terminial with its other processes will still be up an running.

Dave

---

### Post by ianmacgregor on 2006-10-29
He wants to launch an app that opens a terminal and runs, but he wants the terminal to stay open after the app finishes running. Like ALT+F2, type in:

```

gnome-terminal -x sudo updatedb

```and have updatedb run but the terminal stay open when updatedb is finished.

And I'd like to know how to do that too. This is good for making a launcher for a cli app that may or may not need user intervention when the app runs inside gnome-terminal.

---

### Post by Rui Pais on 2006-10-29
hi,
try to check my suggestions on this thread [here]("http://ubuntuforums.org/showthread.php?p=1613694").

---

### Post by loko on 2006-10-29
ianmacgregor,

you're right.

imagine the following.

i start a program from the start-menu, but i want to see the output, so i checked with alacarte "start in terminal".

So if the program crashes, the terminal will get closed, but i want to keep it up that i can see what the error was in this case.

---

