---
title: "scripting help"
date: 2008-05-08
forum: General Help
---

### Post by alphaniner on 2008-05-08
Is there a way to store your user password in a script, such that any command in the script which requires sudo will run without prompting?  Obviously security is not a concern here.

---

### Post by drs305 on 2008-05-08
Here is one way to run a user script which requires a root password. 

Open the sudoers file vis visudo. Note - to edit the sudoers file the system uses vi. It can be confusing to new users. When it opens, select Edit. To insert a line, press I. Then type what you want. After you finish typing, hit the ESC key to get out of the editing mode. Then type :w to write/save your input. To exit, type :q

```
sudo visudo
```
Enter the following text (example is for username dave and script /home/dave/Desktop/testscript.sh)

```
dave ALL= (root) NOPASSWD: /home/dave/Desktop/testscript.sh
```

This script will now run without having to input the root password.

---

### Post by alphaniner on 2008-05-09
I tried that, but it is not actually the script that requires sudo, rather one of the lines in the script.  The entire script is

```
#! /bin/sh
sudo /usr/bin/vmware
```

After editing sudoers for the script name, I tried it with and without sudo before the command.  With sudo I get prompted for the p/w.  Without I get the  error I would expect to get if I ran it without sudo.  I tried adding /usr/bin/vmware to the sudoers file instead, but I got the same error without sudo, and a different one with.

Thanks though.

BTW, when I ran the 'sudo visudo' command, it opened nano, not vi.

---

### Post by bodhi.zazen on 2008-05-09
You can look at expect :

Expect : Automate interactions (will pass passwords):
    
    [http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

    [http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

Or you can pipe the output of an echo command.

---

