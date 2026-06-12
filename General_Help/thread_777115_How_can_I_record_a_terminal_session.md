---
title: "How can I record a terminal session?"
date: 2008-05-01
forum: General Help
---

### Post by jakev383 on 2008-05-01
I provide support for a few things and as a course of paying the bills I will have to remotely log into machines and fix things for clients. I always do this through SSH, and have been increasing the size of my scrollback buffer to 600,000 lines or more and when I'm all done copy-pasting the terminal session in vi to send to the client when I'm all done as a way of accounting and to show them what tasks were performed.
Back before I switched to Linux completely I used PuTTY and it had a feature to log all the terminal output to a text file that was much easier to send to the user.  I've tried PuTTY under Ubuntu and found it lacking in the copy-past portion of the terminal screen so I normally just use gnome-terminal to SSH into machines. I've already whipped up a menu system that works for me using dialog to provide me quick SSH access into machines much like the menu on PuTTY did, but I'm not completely opposed to switching terminals for this task.
Does anyone know of a way to record a terminal session for my task?
Thanks for suggestions!

---

### Post by Monicker on 2008-05-01
You can record your terminal session using the script command.


```
script mysession

<terminal commands>

CTRL+D


cat mysession
```

---

### Post by h4p0 on 2008-05-01
Hi!
I would automatically save the ssh sessions on login...
How can  do that?
Tnk's in advance ^_^

- h4p0 -

---

### Post by jakev383 on 2008-05-01
> **Monicker said:**
> You can record your terminal session using the script command.


```
script mysession

<terminal commands>

CTRL+D


cat mysession
```

I guess the next step would be to write a sed script to strip the line feeds and control characters out of the text. I'll look into that.
Thanks for the suggestion!

---

