---
title: "Is it possible to script (automate) keyboard strokes?"
date: 2008-05-30
forum: General Help
---

### Post by YAOMTC on 2008-05-30
There's this tedious thing I'm doing that involves the following keystrokes:

Context menu, E, Home, Ctrl+Right, Ctrl+Right, Right, Right, Delete, 2, Enter, Up

and repeat.

How can I make a script that repeats this set of keystrokes 317 times?

---

### Post by HalPomeranz on 2008-05-30
While I don't know of a way to automate a sequence of keyboard strokes like you want, another way to solve the problem may be to create a script that accomplishes whatever it is that you're doing with all of that keyboard input.  For example, if you're modifying the contents of a file, it would probably be possible to create a script that accomplishes the modifications without all of the manual typing.  So maybe you could share what the task is that you're trying to accomplish?

---

### Post by YAOMTC on 2008-05-30
I'm doubling the duration of GIF frames in GIMP, one-by-one. The closest thing GIMP has to automation is:
```
-b, --batch=<command>          Batch command to run (can be used multiple times)
--batch-interpreter=<proc>     The procedure to process batch commands with
```
I don't think this will work in this instance, though.

---

### Post by HalPomeranz on 2008-05-30
Mmmm, yeah.  I see your problem.

What you need is some command-line tools that will do the same thing that you're doing manually.  Then you could script the whole thing.  It's possible that the "imagemagick" or "netpbm" packages contain tools that would allow you to do this from the command-line, but I'm not really certain.

---

### Post by YAOMTC on 2008-05-30
Okay, now I've tried both... and I have no idea how to use either one. It seems they're both just a bunch of tools all thrown together into one package, without any central command such as `imagemagick --help'... I'd rather not spend time looking through a bunch of uncentralized manuals when there might not even be a tool that can help me in there...

Thanks for the suggestion, though.

---

### Post by YAOMTC on 2008-06-02
Time to give this another try.

---

### Post by YAOMTC on 2008-06-06
I guess I'll just do it manually. Already halfway done, might as well finish.

---

### Post by kevdog on 2008-06-06
Shoot -- there was a thread about this topic about 4 months ago -- and yes there was a way to do this - for the life of me I cant find the thread.

---

### Post by YAOMTC on 2008-06-06
Daaang.

---

### Post by william willson on 2011-09-07
I was just looking for the same thing and (I know it's an old thread but) I'm posting a useful utility I found so that it gets archived. 

It's a package called xvkbd that can do that using the option -text

xvkbd -text foo

i don't know if it works only for text strings though

---

