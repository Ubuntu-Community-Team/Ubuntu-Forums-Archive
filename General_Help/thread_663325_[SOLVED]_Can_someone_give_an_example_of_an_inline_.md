---
title: "[SOLVED] Can someone give an example of an inline &amp;quot;at&amp;quot; (without the &amp;quot;-f&amp;quot; option)?"
date: 2008-01-10
forum: General Help
---

### Post by brownbat on 2008-01-10
Can someone give me an example of an inline "at" command?

The manual suggests it can read the command from a file or from stdin, but I'm not sure how to get it to do the latter. I tried 
```
echo echo hello > at 11:30
at echo hello 11:30
at `echo hello` 11:30
at "echo hello" 11:30

```
all to no avail.

I know I could have just written a file in the time it takes me to post this, but I'm hoping this will help me to understand std in and using commands inside commands.

(I should also point out that searching for help on "at" is pretty difficult. Here's to search-friendly program names!)

---

### Post by dagnabit dang doohickey on 2008-01-10
Run the at command with desired time (and options):
```
at *now + 2 minutes*
```
You will now see the at prompt:
```
at>
```
Enter the command you want to run:
```
at> *touch ~/at-test-file*
```
Hit Enter then press Ctrl+D to save the job. You will see:
```
at> <EOT>
*job number and runtime info*
```

---

### Post by brownbat on 2008-01-10
Wow, that seems so obvious in hindsight, thanks so much!

---

