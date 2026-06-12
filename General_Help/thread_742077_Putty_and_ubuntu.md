---
title: "Putty and ubuntu"
date: 2008-04-01
forum: General Help
---

### Post by raveash on 2008-04-01
Is there a program like "putty" that i can run on ubuntu? if there is already one can anyone give me the name?

---

### Post by stefangr1 on 2008-04-01
yes, ssh

I believe it's installed by default, otherwise run:

sudo apt-get install openssh-client

---

### Post by raveash on 2008-04-01
ok so i know its ssh. but how do i find this program?

---

### Post by ashvee on 2008-04-01
type ssh @ the terminal , then u will get the option :guitar:

---

### Post by stefangr1 on 2008-04-01
well, it's a commandline program. So when you have opened a terminal, you just connect by typing "ssh ip-address", from there everything works the same as in putty.

---

### Post by Slushdoot on 2008-04-01
As above, the tools implemented in PuTTY and its sister-programs are all already installed on Ubuntu and most other Linux systems.

ssh user@host
is the syntax.  :)

---

### Post by raveash on 2008-04-01
Ok i get it now. I guess i was just confused were to put my user name. I found out that it supposed to be  Username@and thend the adress. :lolflag:

---

### Post by era86 on 2008-04-01
You could use gftp for a GUI.  It has different features including SSH.

---

### Post by Dr Small on 2008-04-01
PuTTY is avaliable for Ubuntu in the repositories (I believe) if you wanted a GUI.
Otherwise, openssh-client works much easier in the command line.
[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

---

