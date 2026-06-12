---
title: "Opening Programs With Sudo Command In GUI"
date: 2015-04-17
forum: General Help
---

### Post by Tadpole Jackson on 2015-04-17
I'm fairly new to Linux and I can't figure out how to do this. I've searched the internet and the forums with no luck. I have a program, specifically Dwarf Fortress on my desktop but when I double click it, nothing happens. However, if I go into the terminal and open it via a sudo command it runs fine. How do I perform a sudo command on the application via a double-click? I don't want to have to go into the terminal just to run a program. It just seems needlessly difficult. I am running version 14.04.

---

### Post by ian-weisser on 2015-04-17
Might be a simple permissions issue.
You shouldn't need to run *any* common application with sudo, unless you are modifying data owned by a different user. And often not even then.

How, exactly, did you install Dwarf Fortress? If you followed online instructions, a link would be helpful.

---

### Post by Tadpole Jackson on 2015-04-17
I just downloaded the Linux pack from [http://lazynewbpack.com/](http://lazynewbpack.com/) and extracted the files from the zip.

---

### Post by Tadpole Jackson on 2015-04-17
If I use the terminal to run the command without sudo I get the following errors:

No value set for `/desktop/gnome/applications/terminal/exec'
No value set for `/desktop/gnome/applications/terminal/exec_arg'
xdg-terminal: configured terminal program '' not found or not executable

---

### Post by sotiris2 on 2015-04-17
Can you actually run programs from the terminal? Like firefox for example?

---

### Post by mc4man on 2015-04-17
What occurs if you cd to extracted folder & run - 
```
./startlnp
```
It's a one time setup... then run as before, no sudo needed

Otherwise read/muddle thru - [http://www.bay12forums.com/smf/index.php?topic=140966.0](http://www.bay12forums.com/smf/index.php?topic=140966.0)

---

### Post by Tadpole Jackson on 2015-04-17
I tried reinstalling it and now it won't work even if I use the sudo command. I get this error:

> If I use the terminal to run the command without sudo I get the following errors:

No value set for `/desktop/gnome/applications/terminal/exec'
No value set for `/desktop/gnome/applications/terminal/exec_arg'
xdg-terminal: configured terminal program '' not found or not executable

---

