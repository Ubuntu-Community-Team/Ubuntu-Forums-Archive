---
title: "What is getty, and whay I have 6 running instances of it?"
date: 2005-06-14
forum: General Help
---

### Post by SGC on 2005-06-14
I read the manual page for getty , but still I didn't understand what it actually did. and why I have six running instance all the time?

---

### Post by Knome_fan on 2005-06-14
I think it's basicly the program responsible for the login prompt you get on your consoles. (Pressing ctrl+alt+F[1-6]).

It just sits there waiting for you to log in.

---

### Post by SGC on 2005-06-14
[QUOTE=Knome_fan]I think it's basicly the program responsible for the login prompt you get on your consoles. (Pressing ctrl+alt+F[1-6]).

It just sits there waiting for you to log in.[/QUOTE]
 Do i realy need it?

---

### Post by petrol on 2005-06-14
Yes, you need it. It supplies terminal access. There are some that you can shutdown if they are running on serial interfaces etc.

---

### Post by angkor on 2005-06-14
If you don't need em all you can comment out some in /etc/inittab

---

### Post by lotusleaf on 2005-06-14
[QUOTE=angkor]If you don't need em all you can comment out some in /etc/inittab[/QUOTE]

Doing so also frees up memory, which is useful if they are never used.

---

### Post by SGC on 2005-06-14
[QUOTE=angkor]If you don't need em all you can comment out some in /etc/inittab[/QUOTE]
 How do i know which one is needed and which one is not.

---

### Post by Knome_fan on 2005-06-14
What is needed does of course depend on what you do.

If you really want to comment some gettys out, why not simply leave the first two running and comment out 3-6.
This way you'll always have to login prompts to fall back on in case you need them, but don't waste the memory for the other prompts you probably don't use. (Although I doubt that it uses that much memory to make it really worthwhile stoping them, but this may of course also depend on your setup).

---

### Post by SGC on 2005-06-14
[QUOTE=Knome_fan]If you really want to comment some gettys out, why not simply leave the first two running and comment out 3-6.
This way you'll always have to login prompts to fall back on in case you need them, but don't waste the memory for the other prompts you probably don't use. [/QUOTE]
 Thanks, it seems like a good advise, I will try it.

---

### Post by az on 2005-06-14
Hey Knome_fan, I had no idea you could do that!  Good to see you!

Any idea how much memory they take up?

---

### Post by skoal on 2005-06-14
[QUOTE=angkor]If you don't need em all you can comment out some in /etc/inittab[/QUOTE]
Alternatively, if you made your own custom init level (like 4 or 5), you can just change the inittab default runlevel to 5 and it will only load up 1 (by default), which is what I do in runlevel 5 (my minimal X session).

\\//_

---

### Post by Seth on 2005-06-15
On my system the gettys have a VmSize of 1,528. Not worth shutting down.

---

