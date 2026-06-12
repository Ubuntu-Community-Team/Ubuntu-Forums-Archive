---
title: "Execute Command in Different TTY?"
date: 2007-05-09
forum: General Help
---

### Post by kd7swh on 2007-05-09
Does anyone know how to execute an application from the terminal (X) in a different TTY (outside of X)?

I am looking to multi-task with a shell script.

Thanks!

---

### Post by lloyd_b on 2007-05-09
Is there a reason you can't just run the program in question in background?
```
someprog &
```

Lloyd B.

---

### Post by kd7swh on 2007-05-09
I would like to be able to monitor the application although running it in the background works, verbosity would be ideal.

---

### Post by engla on 2007-05-09
Run it in a screen session. GNU Screen is a very versatile application, look it up

---

### Post by kd7swh on 2007-05-09
If I wanted to use screen to open program1 in tty2 from tty1 would this be the proper syntax?

```
screen -r tty2 program1
```

The man page for screen makes me want to cry sort of the same way I did when I typed man emacs for the first time.

---

### Post by engla on 2007-05-09
screen doesn't really do that. 

Now here is an example what you can do:

start screen:
screen 
run your program in the foreground:
program1
send it all to the background:
ctrl-A, ctrl-D (in succession)

Now you can bring the session back from any tty you are at by issuing
screen -r

I hope this in some way is useful the way you want it. Note that you can have many "windows" per screen session. Type ctrl-A,ctrl-C to create a new window and ctrl-A,ctrl-N to go to the next window...
good luck, and pm me or so if you have more questions..

---

### Post by kd7swh on 2007-05-10
Screen is great. I have heard people talk about it before but I never used it. Even though it wasn't exactly what I was looking for. It does the trick, and it gets me thinking about other applications for it. Thanks for the suggestion. I am glad I conquered the man page too. :)

---

