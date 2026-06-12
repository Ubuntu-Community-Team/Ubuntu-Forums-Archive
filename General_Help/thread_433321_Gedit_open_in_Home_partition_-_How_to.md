---
title: "Gedit open in Home partition - How to"
date: 2007-05-04
forum: General Help
---

### Post by JimS on 2007-05-04
...
I want Gedit to open in my Home partition at a certain directory.
How do I fix it?
...
JimS
...

---

### Post by m.musashi on 2007-05-04
I'm not sure I understand but you can open a terminal and type
```
gedit ~/name_of_dir/name_of_file
```
For example
```
gedit ~/foo/boo
```
That will open a file called boo located in /home/foo/.

If you want to open gedit from the menu and have it defalut to /home/foo then I'm not sure but I bet there is a config file somewhere that will set that up.

---

### Post by JimS on 2007-05-05
...
Domo arigato Miyamoto Musashi san.
Mo ichido shite kudosai.

That is not the answer.  
When I open Gedit, I want Gedit to be opened  in my home partition, XXX directory.

JimS
...

---

### Post by m.musashi on 2007-05-06
Gomen kudasai. Sore shika wakarimasen.

And for the rest of you, I'm afarid I don't don't know how to do that. It's probably in a config file but I wouldn't know where to begin.

---

### Post by fragos on 2007-05-06
Check out the configuration editor apps->gedit-2.  That's the most likely place I can think off.  Gedit cosiders specifying only a directory when opening it an error.

---

