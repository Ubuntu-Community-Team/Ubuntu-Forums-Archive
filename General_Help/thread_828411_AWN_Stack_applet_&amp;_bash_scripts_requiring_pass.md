---
title: "AWN Stack applet &amp; bash scripts requiring password"
date: 2008-06-13
forum: General Help
---

### Post by vtechstu on 2008-06-13
Hi,

I've added some bash scripts to one of my stacks in awn.  When I click them, nothing happens.  I ran awn from the terminal, and when I clicked them I noticed it's actually waiting for the root password, but since i'm g these from the stack, no terminal shows initially, and therefore no way to type it in.

Does anyone have a fix for this?

To be clear, I have some bash scripts in my Stacks applet in AWN that I want to click, and have run in the terminal, so that I can see whats actually happening and to also put in the password.

Thanks in advance

---

### Post by Lostincyberspace on 2008-06-13
Add run as root gksu before the the path to the file
ie. gksu sh ubuntu.sh

TO run through terminal you need to pipe it to gnome-terminal or some other terminal.

I can't figure it out though.

---

### Post by Happy_Man on 2008-06-13
There is a terminal applet for AWN, you can use that to run the scripts.

---

### Post by vtechstu on 2008-06-16
Lostincyberspace:
   I have sudo before it already in the call.  I feel like we're experiencing the same issue or at least trying to accomplish the same goal.

Happy_Man:
   Yeah I have the applet for the terminal, but it doesn't help with what I'm trying to accomplish here. But thanks anyway.

Anyone else get this to work?

BUMP

---

### Post by Happy_Man on 2008-06-16
> **vtechstu said:**
> Lostincyberspace:
   I have sudo before it already in the call.  I feel like we're experiencing the same issue or at least trying to accomplish the same goal.

Happy_Man:
   Yeah I have the applet for the terminal, but it doesn't help with what I'm trying to accomplish here. But thanks anyway.

Anyone else get this to work?

BUMP
Hm, instead of putting the scripts themselves directly in the stack, try making a folder that contains a set of shortcuts that open a terminal that in turn starts the script. A sample one: ```
#!/bin/bash

gnome-terminal "/path/to/script.sh"
```

And then stick all these in another folder and make them runnable. So when you click it, it should open up a terminal with the script started. A bit convoluted, but definitely doable.

---

### Post by vtechstu on 2008-06-16
> **Happy_Man said:**
> Hm, instead of putting the scripts themselves directly in the stack, try making a folder that contains a set of shortcuts that open a terminal that in turn starts the script. A sample one: ```
#!/bin/bash

gnome-terminal "/path/to/script.sh"
```

And then stick all these in another folder and make them runnable. So when you click it, it should open up a terminal with the script started. A bit convoluted, but definitely doable.

Thanks Happy_Man,

That's a great idea, and it would be suitable for me, but I gave it a try and it didn't work.  It opens up the gnome-terminal correctly, but not the script in quotes in the driver script.

Anything else I need to do to make this work?

---

### Post by Happy_Man on 2008-06-16
> **vtechstu said:**
> Thanks Happy_Man,

That's a great idea, and it would be suitable for me, but I gave it a try and it didn't work.  It opens up the gnome-terminal correctly, but not the script in quotes in the driver script.

Anything else I need to do to make this work?
Ah, I had forgotten one thing: See if this works...

```
#!/bin/bash

/usr/bin/gnome-terminal -e "/path/to/script.sh"
```

---

### Post by vtechstu on 2008-06-16
Hah yeah it does, I figured it out after reading the man page, but got carried away implementing this that I forgot to update my response.  thanks for the help.

---

