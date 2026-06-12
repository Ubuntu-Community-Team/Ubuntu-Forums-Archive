---
title: "cd command syntax"
date: 2007-02-10
forum: General Help
---

### Post by ukeitaro on 2007-02-10
Hi everyone,

On the terminal, I'm trying to change the directory to "/home/michael/Desktop/my documents" but the space in "my documents" creates an error when i use the cd command.  How do I appropriately type it using cd?  Thanks

Michael

---

### Post by pizzutz on 2007-02-10
The space has to be "escaped" (preceded with a \)  or quoted.


try one of these two.

cd "/home/michael/Desktop/my documents"

or

cd /home/michael/Desktop/my\ documents

and it will know the space is part of the path.

Alternatively, you can use tab completion. type as far as

cd /home/michael/Desktop/my

and push tab.  As long as the my is unique to that directory, the shell will fill in the rest for you, escaped whitespace and all.

---

### Post by Maestro23 on 2007-02-10
> **ukeitaro said:**
> Hi everyone,

On the terminal, I'm trying to change the directory to "/home/michael/Desktop/my documents" but the space in "my documents" creates an error when i use the cd command.  How do I appropriately type it using cd?  Thanks

Michael

One way:

#mkdir my_documents

Then when you cd to it, 

#cd my_documents

I think there is another way with / or \, (not sure), but I have always done mine this way from my old Slackware days.:)

*Edit.. Guy above beat me to the other way...

---

