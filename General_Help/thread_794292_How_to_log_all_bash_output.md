---
title: "How to log all bash output?"
date: 2008-05-14
forum: General Help
---

### Post by Martiini on 2008-05-14
I'd like to get a bash log file containing ALL events (input commands, bash output)

---

### Post by HermanAB on 2008-05-14
Use konsole and scroll back.

H.

---

### Post by jomiolto on 2008-05-14
I'm quite sure you can use the *tee* command for this, but I'm not exactly sure how to get the input in it too. For example, doing this:
```
bash | tee log.txt
```
will launch a new bash prompt and all the output of that prompt will go to log.txt, but this doesn't write the input in it :(.

EDIT: I just found a nice command for this, called *script*, but that will also write all the curses output (colour changes and such needed to control the terminal) to the log file, which may or may not be what you want. If you just want a plain text log, you could probably somehow remove the control sequences from the output of the *script* command.

---

### Post by tbroderick on 2008-05-14
Bash input should already be logged to a text file ~/.bash_history.

---

### Post by fissionmailed on 2008-05-15
$ script file_name

$ blah 
$ blah blah
$ hur hur hur

then either $ exit or ctrl d to stop the script

---

### Post by uraldinho on 2008-05-15
I have used > in the past. Eg:

$command > myfile.txt 

this writes the output to a text file. Using 2 > instead of 1 keeps the old file state and just continues from the last line. Eg: 

$command >> myfile.txt 

Useful to see program output.

---

### Post by Moustacha on 2008-05-15
> **fissionmailed said:**
> $ script file_name

$ blah 
$ blah blah
$ hur hur hur

then either $ exit or ctrl d to stop the script

+1

---

### Post by tat.wright on 2010-08-31
**rlwrap -l output bash**

might do what you want - though this leaves escape characters as they are rather than stripping them.


PS. Not sure if it breaks etiquette rules to post on such an old thread - but I think it's worthwhile having an answer to this question.

---

### Post by lukeiamyourfather on 2010-08-31
All commands are stored by default and can be accessed with the "history" command. The output of the shell is not logged because it can contain sensitive information among other problems. If you need to log a specific event then most terminal emulators have an option to export the current session. Be sure to set the buffer to enough lines to cover what you need (or just set to unlimited).

---

### Post by cariboo on 2010-08-31
> **tat.wright said:**
> **rlwrap -l output bash**

might do what you want - though this leaves escape characters as they are rather than stripping them.


PS. Not sure if it breaks etiquette rules to post on such an old thread - but I think it's worthwhile having an answer to this question.

It does break the rules, next time create a new thread with a link to the oldy moldy thread.

---

### Post by jpeddicord on 2010-08-31
In any case, moving this to a more appropriate forum.

---

