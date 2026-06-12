---
title: "Jedit, multiple open docs, save dialog frozen"
date: 2018-05-08
forum: General Help
---

### Post by dgosborn on 2018-05-08
I'm using Jedit and I have 21 unsaved "untitled" documents. (please don't kill me)
I went to save one and the save dialog is frozen for the last half hour or so.

Is there any way to recover from this situation?

What about a memory dump?
Swap dump?
Application memory dump?

I don't want to sacrifice a chicken but about anything short of that . . .

Is it safe to say <2gb used ram will produce <2gb memory dump? I have about 20GB free on disk.

If I do a memory dump(s) any tips on digging the text out of those, or doing the dump in a way that will make that easier? Maybe one dump per pid then something to delete data that is duplicated across the pids?

---

### Post by QIII on 2018-05-08
Please use a meaningful title.  Your previous one was more likely to drive people away than attract them.

---

### Post by westie457 on 2018-05-08
I have never seen this situation before.
This will probably no help at all so is just an idea.

Use 'htop' to identify the frozen process and kill it.
Then retry to save the documents.

This might save at least half a chicken.....

As for your other ideas, again I do not know however someone who knows more than me will be able to help more.

As for us killing you, we will let you do that yourself.

---

