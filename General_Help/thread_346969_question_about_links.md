---
title: "question about links"
date: 2007-01-26
forum: General Help
---

### Post by Mateo on 2007-01-26
I want to make the command 'dvd' run 'mplayer dvd:///dev/hdb'.  But:

Aliases won't work because they have to be run through the terminal.  I want to run it in 'Run Application'

Desktop shortcut won't work for the same reason.

Link doesn't work because it doesn't work with command lines.  Same for Ln -s (i think).

any other suggestions?

---

### Post by encompass on 2007-01-26
Bash....

create this...
```
#/bin/bash
your command goes here.
```
then you can place it somehwere nice....
then make it executable with....
```
chmod +x dvd
```
then you create a link to the file inside the /usr/bin/ derectory....
let me think..... how do I make a link again?

---

### Post by encompass on 2007-01-26
sudo ln -s dvd /usr/bin/dvd
that should get you running...
I did this with my lowend system.

---

### Post by citizenofnowhere on 2007-01-26
This isn't quite what you're looking for, but you want something to be in "run application" -> by this I take to mean "open with..." because once you do that a couple of times it gets added... 

Your ~/.local/share/applications is where all the options that appear in the "open with..." section live. They're in the form of desktop files. I copied one, right-clicked properties, changed the name, changed the launcher description etc. and now I have an entry named dvd that does what you want.

So perhaps use a combination? an alias for command line and the above method for right click?

---

### Post by Mateo on 2007-01-26
citizenofnowhere:  sorry, I didn't mean open with.  I meant Run Application from alt+f2.  I'll try  encompass' suggestion.

---

### Post by encompass on 2007-01-29
Did it work for you?  It is important to post if you go it or not.

---

### Post by Mateo on 2007-01-30
actually I gave up, and just made a launcher instead.

---

