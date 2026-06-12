---
title: "Modify Terminal"
date: 2008-04-09
forum: General Help
---

### Post by matt12345678 on 2008-04-09
If I wanted to modify the terminal every time I opened it to do xyz, where would I go to modify the terminal and how would I do this? For instance, if I wanted to have the terminal ssh @xyz.example.com each time I login or execute some other command how would I go about doing this?? I appreciate any help guys, thanks a bunch.

---

### Post by kellemes on 2008-04-09
> **matt12345678 said:**
> If I wanted to modify the terminal every time I opened it to do xyz, where would I go to modify the terminal and how would I do this? For instance, if I wanted to have the terminal ssh @xyz.example.com each time I login or execute some other command how would I go about doing this?? I appreciate any help guys, thanks a bunch.

You need to play around with your ~/.bashrc

Pretty informative thread.. [http://ubuntuforums.org/showthread.php?t=679762&highlight=bashrc]("http://ubuntuforums.org/showthread.php?t=679762&highlight=bashrc")

Search the net for more info on this, there is a lot.

---

### Post by phidia on 2008-04-09
[This]("http://www.linuxquestions.org/questions/programming-9/c-syntax-for-terminal-584029/?highlight=terminal+modding") and [this]("http://www.linuxquestions.org/questions/programming-9/where-to-start-633655/") may help because unless I don't understand your question-always possible-then you are really asking about programming/scripting.

---

### Post by unutbu on 2008-04-09
Save this in a file (I'll call it 'ss'):
```
#!/bin/bash
gnome-terminal --command="ssh user@xyz.example.com"
```

Make it executable:
```
chmod 755 ss
```

---

### Post by lswest on 2008-04-09
if you edit the profile (right-click anywhere on the terminal and choose "edit current profile") for your terminal i do believe an option is there to add a command at the startup of the terminal (a friend of mine once set it up to do sudo -s at startup so that he'd prevent anyone from using his terminal without his password). 

*edit* tested it on my terminal: Go to the tab "title and command" then check the box "run custom command instead of my shell" type in the command and choose "hold terminal open" and done.  However, with the ssh, you might want to set it up in a second profile and just switch between the two profiles for flexibility.

---

