---
title: "How to make a short cut or launcher"
date: 2008-01-14
forum: General Help
---

### Post by src2206 on 2008-01-14
Hello

I am on a PPPOE Dial up connection which has limitation on data transfer. So I have to repeatedly use the following two commends in the terminal window which hinders  my normal work flow a lot. These commands are:

**pon dsl-provider** and [B]poff -a

[/B]Is there any way to make a Launcher (or something like it, not sure honestly) to automate this process? Or may a GUI front end for these two commands?

Please suggest. :confused:

Thank you.

---

### Post by b0rka7a on 2008-01-14
Yes :) Go to the terminal and type:
```
gedit connect
```
Type in it the following lines:
```
#!/bin/bash
pon dsl-provider && poff -a
```
Save the file and go back to the terminal and type:
```
chmod +x connect
```
That's it ;) Just run the launcher (it should be in your home dir).

---

### Post by src2206 on 2008-01-15
> **b0rka7a said:**
> Yes :) Go to the terminal and type:
```
gedit connect
```Type in it the following lines:
```
#!/bin/bash
pon dsl-provider && poff -a
```Save the file and go back to the terminal and type:
```
chmod +x connect
```That's it ;) Just run the launcher (it should be in your home dir).


Hello b0rka7a

Thanks very much for your reply.

Well, I did everything as you said. But as I double click on this "connect", it gives me 4 different options. As I choose to run, it can not connect to the net but while running the connection if I run this appliction, the connection closes. So in a nutshell, **this application can stop but can not start the connection**. 

Any idea? :?:

---

### Post by src2206 on 2008-01-20
Could some one help me out please?

:(

---

### Post by src2206 on 2008-01-29
Any more help please? it is still not resolved...:(

---

### Post by Spitz on 2008-06-10
just open a terminal and type:
```
./connect
```

Otherwise you could probably also make a launcher by right clicking on you desktop, choose create launcher, and set the command as ./connect

---

