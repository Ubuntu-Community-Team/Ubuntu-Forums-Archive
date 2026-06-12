---
title: "Access to /usr in places"
date: 2008-06-03
forum: General Help
---

### Post by hAvAAck on 2008-06-03
I must fail at search, but I tried several key words and came up with nothing, and I'm sorry for such a ridiculous question (as I'm sure it is), but how do I gain access to /usr?
I wanted to create a script that called for it to be in /usr/local/bin but was unable to create a file there, using places and navigating there with the mouse. Instead I created it somewhere else and used terminal to sudo cp it to the location. Is this the normal way I should expect to do these sorts of things? I don't want to change any permissions (ie I want to be able to do this graphically but still have password restrictions). Am I just gravitating towards my windows base and not understanding the functionality of things like this? Thanks.

---

### Post by kbuel on 2008-06-03
An easy way to create a file in /usr/local/bin is with the following command:

gksudo gedit /usr/local/bin/yourScript.sh

when you hit save, the file will be written to the /usr/local/bin directory with the name 'yourScript.sh'


Edit:
This will give you a graphical way of creating the file in the location, but you will need to initially use the command line.  This may be a good thing though, as it is a step you need to do when editing/creating files in "root" owned areas (as in a layer of protection so you don't mess anything up un-intentionally).

---

