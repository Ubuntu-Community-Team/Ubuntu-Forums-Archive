---
title: "Help with permissions"
date: 2006-11-18
forum: General Help
---

### Post by kingofkings on 2006-11-18
I need help. I'm a little frustrated with this. How do you change the permission. I am trying to download some plugins for aMSN. I can't do them:sad:. Could someone help me? I'm new. I've had ubuntu for a 1 week and 5 days

---

### Post by Choad on 2006-11-18
to change the owner of a file, use chmod (from a terminal)

$ man chmod

for more info

to temporarily give yourself super privilages, and become the unix god, use "sudo" before any command. 

$ sudo mv ~/myfile.txt /myfile.txt

would move a file to the root directory even tho you are not root and dont own the root directory

not sure what the amsn plugin thing is about. you probably have a ~/.amsn/ directory, which probably has some kind of plugins directory

(oh and ~ is the shortcut to "home", and a "." before a filename makes it hidden, so ~/.amsn is a hidden folder in the home directory.... probably. cant guarantee its there because i dont use it)

---

### Post by kingofkings on 2006-11-19
How do you change the permissions on man chmod?

---

### Post by Sohum on 2006-11-19
you don't. man chmod is the manual page of chmod; you're supposed to read it and then use chmod.
These are terminal commands: type them in Menu>Accessories>Terminal.

---

### Post by kingofkings on 2006-11-19
Ok. now I get it.

---

