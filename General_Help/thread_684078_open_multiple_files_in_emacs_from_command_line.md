---
title: "open multiple files in emacs from command line"
date: 2008-01-31
forum: General Help
---

### Post by apobrien on 2008-01-31
Hello,

I want to descend through a directory tree visiting a java source file
**and** one other file, preferably in split view, in each subdirectory.

Getting the file list isn't hard but what I can't figure out is how to
get emacs to open two files at once through the command line.

Any suggestions on where I might look?

(I'm interested in interactively editing the files so batch mode
isn't of use to me)

TIA

---

### Post by FaBi3ttO on 2008-02-03
well, I haven't understand your question perfectly.
Do you want to edit 2 files at once.
What about opening emacs, split the window with CTRL 3 and open a file in each window?
There are also commands like emacs-diff that can help you in editing this 2 files.
Maybe you can also edit the .emacs file so using a keyboard stroke you can open the next files in the list but I dunno how to program using LISP.

My 2 cents,

---

### Post by apobrien on 2008-02-04
Thanks for the reply.

I have a directory structure where students' Java programs and an html grading template are stored.  I want to write a script that descends through the directory structure opening these two files (one copy of the grading template per student/directory) in split-window mode with as little manual intervention as possible.  Ideally, I would edit, save and exit and the next set would open.

I can open one file using find or a loop in bash but can't figure out a way to open two or more.  I realize I could bind the opening of the second file to some keyboard shortcut but was hoping for a more elegant solution.

Any other suggestions?

---

