---
title: "how do i execute a program from terminal [Resolved]"
date: 2007-03-05
forum: General Help
---

### Post by lavinog on 2007-03-05
Just curious is there a command that i can use that executes a program from the terminal without having the shell wait for the program to terminate.
something equivalent to winxp's start command

---

### Post by ffxr on 2007-03-05
Alt-f2

---

### Post by laidback on 2007-03-05
If you know the command just type it in, e.g.
$gedit   loads the geditor program
$firefox loads the browser

or press Alt + F2 from the desktop, then either type in the command or choose it from the list.

Hope this helps

---

### Post by 23meg on 2007-03-05
The "Run Applications" dialog (Alt + F2) works best if you don't need the program's output in the terminal (usually if it's a daemon or a graphical app). If you do, launch a terminal and put "&" at the end of it. 

```
fileschanged & 
```

will give you a new instance of the app "fileschanged" without obscuring the terminal. The shell will also return a job number and process ID that you can use to access and kill the process at a later time.

---

### Post by lavinog on 2007-03-06
> **23meg said:**
> The "Run Applications" dialog (Alt + F2) works best if you don't need the program's output in the terminal (usually if it's a daemon or a graphical app). If you do, launch a terminal and put "&" at the end of it. 

```
fileschanged & 
```

will give you a new instance of the app "fileschanged" without obscuring the terminal. The shell will also return a job number and process ID that you can use to access and kill the process at a later time.

That was exactly what i was looking for.
Thank you

---

### Post by bionnaki on 2007-03-06
what does & do?

---

### Post by 23meg on 2007-03-06
> **bionnaki said:**
> what does & do?

It tells the shell to give you the prompt, a job number (in square brackets) and the process ID of the program before it, instead of giving its output and blocking the prompt.

More here: [http://www.linuxcommand.org/lts0080.php#practical_example](http://www.linuxcommand.org/lts0080.php#practical_example)

---

### Post by scxtt on 2007-03-06
"backgrounds" the process ... lets it execute 'on its own' independent of the terminal it was executed from ...

---

### Post by lavinog on 2007-03-06
how did this thread become resolved?
is that automatic or should i be doing that?
just curious

---

### Post by 23meg on 2007-03-06
You normally edit your first post in the thread (in advanced mode) and check the "Check box if your thread **IS** resolved" box.

---

