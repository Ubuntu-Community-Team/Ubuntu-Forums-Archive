---
title: "How do you open up a new tab in terminal??"
date: 2007-03-16
forum: General Help
---

### Post by falcon22 on 2007-03-16
Okay, I am pretty new to Ubuntu and Linux as a whole, so I don't mean to sound stupid by asking this question.  Anyways, I wanted to do some bash scripting and I need to know if there is a command which opens up a new tab in an already open terminal.  Thx.

---

### Post by useResa on 2007-03-16
Don't worry about asking questions. It is better to ask the question than to remain ignorant :)

To open a new tab: From the menu select: File --> Open Tab 
or press Shift+Ctrl+T

---

### Post by 23meg on 2007-03-16
The OP is asking how to do it with a command in a script, not manually. ```
gnome-terminal --tab-with-profile=PROFILENAME
```should work.

---

### Post by falcon22 on 2007-03-16
thanks for the fast responses.  Would the PROFILENAME be something like person@person-desktop?

---

### Post by steve101101 on 2007-03-16
i think its your username not sure though

---

### Post by 23meg on 2007-03-16
No, you should substitute it with an existing gnome-terminal profile name.

---

### Post by Cynik on 2008-06-18
Hi

I was trying 
gnome-terminal --tab &
gnome-terminal --tab-with-profile=DEFAULT
(the only profile set)
in 8.04 and for some reason a new **window** is opened instead of a tab.

Can you give me any suggestions to correct this?
(I wanted to write a bash script to open a set of files in different tabs.)

Thanks.

---

### Post by inigo48 on 2008-07-08
I want the same thing: new tab in an existing terminal window. It is pretty vital if you use a dock and for example want to open a new terminal from pcman.
any idea? maybe it isn't possible at all?

---

