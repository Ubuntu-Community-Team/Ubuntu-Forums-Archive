---
title: "When I shut Ubuntu down, does it save my files?"
date: 2007-05-28
forum: General Help
---

### Post by tszanon on 2007-05-28
Let me create a scenario and then ask the question.

In windows, suppose I am running eMule. When I shut Windows down, eMule saves its files then everything closes. In Ubuntu, when I shut it down, everything seems to go through a forced-close, it seems that aMule does not save its files if I shut the system down while it's still running.

The same happens with any Office suite: in Windows, it asks me if i want to save the changes, then it shuts down. In Ubuntu, it just shuts down (if I recall correctly).

My question is: files that surely should be saved (like aMule's), are they saved? And what about those files that should/shouldn't be saved, that need user confirmation (like the documents in OpenOffice)?

Maybe the answer is "it depends on how the program was written"...

---

### Post by raul_ on 2007-05-28
I don't know my portuguese-talking friend. I think that when Linux shuts down it sends the "kill" signal to all processes, causing them to quit abruptly, not saving your work. 

Try editing some garbage in open office and then shutting down..then see if they're still there.

---

### Post by tszanon on 2007-05-28
> **raul_ said:**
> I don't know my portuguese-talking friend. I think that when Linux shuts down it sends the "kill" signal to all processes, causing them to quit abruptly, not saving your work. 

Try editing some garbage in open office and then shutting down..then see if they're still there.
It makes sense...something like, "hey, if you wanted to save something before shutting down, WHY did you tell it to shut down????" ;)

When I get home I'll try to find it out. Thanks, raul_!

---

### Post by tszanon on 2007-05-28
Actually, the system really acts in a user-friendly way: I tested with OpenOffice and the Text Editor and both asked me if I wanted to save my files. They could even stop the system from rebooting.

That's it, thanks again. :D

---

### Post by raul_ on 2007-05-28
Yes. Some editors also keep temporary save files of your work. For example, if your programming, you'll see that in the folder you're in, a lot of ~* files are created: these are "safe-copies" in case something goes wrong

---

