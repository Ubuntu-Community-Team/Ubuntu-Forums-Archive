---
title: "plzz help its urgen"
date: 2008-02-12
forum: General Help
---

### Post by citkatboy on 2008-02-12
hii friends i m new to linux..............
i have installed ubuntu......
but when i typed....sudo-apt get install gdesklets in the terminal it gave me this message.......

shantanu@shantanu-desktop:~$ sudo apt-get install gdesklets
[sudo] password for shantanu:
E: Type 'mdeb' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.

what should i do????
i m able to run the update manger also???
what shold i do????
it gives me this error when i run update manager


Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'mdeb' is not known on line 1 in source list /etc/apt/sources.list, E:The list of sources could not be read.'



plzzz help me guys plzz help....if u want me to access linux and to know what is linux than plzzz help me.....

---

### Post by apetresc on 2008-02-12
You've accidentally typed an 'm' in the first line of your /etc/apt/sources.list file.

Simply do ```
gksudo gedit /etc/apt/sources.list
``` and remove the "m" on the first line so it says "deb" instead of "mdeb", then save and close, type ```
sudo apt-get update
``` and try again :) It should work this time.

---

### Post by fdrake on 2008-02-12
did u select all the required repositories on synaptic?

---

### Post by Zwack on 2008-02-12
try gksudo gedit /etc/apt/sources.list

It looks like the first line starts mdeb

remove the m, save it and try again...

Z.

---

