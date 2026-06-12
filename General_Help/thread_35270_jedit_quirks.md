---
title: "jedit quirks"
date: 2005-05-18
forum: General Help
---

### Post by vegetto on 2005-05-18
I am using jedit for java editing but a minor issue is that the console plugin cannot execute javac and java without entering the full path. java is already added to path and everything works. i can get jcompiler to compile the file with a single shortcut key but is there way to execute the program using a single shorcut key.

---

### Post by dave9191 on 2005-05-18
Are you sure that javac and java are in your PATH ? If they are, then maybe it has to be set for the jedit console seperatly? 

Dave

---

### Post by vegetto on 2005-05-18
Yes, java is in my path. it is in bashrc and java and javac works from terminal.

---

### Post by dave9191 on 2005-05-18
Try typing bash into the jedit console. And then see if they work. 

Dave

---

### Post by vegetto on 2005-05-18
I figured it out! simple really just edit the jedit startup script and set the correct java directory. i wonder how jedit was working with an incorrect java_home directory in the first place but anyways now i am really happy :) , here i come bruce eckel. ](*,)

---

### Post by dave9191 on 2005-05-18
I thought that it might have been to do something with the settings in jedit somewhere. Now get back to work :p

---

