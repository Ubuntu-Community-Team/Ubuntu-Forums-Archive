---
title: "How do I get nautilus SSH file system to see local files?"
date: 2007-11-28
forum: General Help
---

### Post by MR.UNOWEN on 2007-11-28
Hello

I use ssh -XC nautilus to connect to my school account. For the most part it works, but there's one issue. I can't copy/ paste from from school account to my home computer or the other way around. Is there a solution to this problem?

---

### Post by sirgogo on 2007-11-28
You mean in the terminal or using the GUI?

(I'm sorry if I'm being stupid right now, and I totally missed your point. I'm still pretty nub.)

If its the terminal:
1. You can't transfer using the ssh protocol, you have to use sftp. So make sure the server supports it, a good way to check is by trying to type in the terminal:

```
sftp useraccount@server.edu
```
Then it will prompt you for the password.

You browse your local files by adding "l" in front of all the commands. For example, to list (ls) local files you have to type:

```
lls
```

and to enter a local directory ```
lcd
``` (instead of cd).

To upload things to the server, navigate to the local folder using the "l" commands, and then go:

```
put filename
```

and to download, navigate remotely, using *regular* commands and type:

```
get filename
```.

If you're using a GUI:
1. I really don't know what to say, I suggest you use the terminal, its easier and more fun.

Again, sorry if I'm being stupid and totally missed your question, just trying to help.

Take it easy ;)

---

### Post by MR.UNOWEN on 2007-11-29
The issue is nautilus. For some reason what ever I copy from one system does not apply to the other file system.

---

### Post by fjgaude on 2007-11-29
> **MR.UNOWEN said:**
> Hello

I use ssh -XC nautilus to connect to my school account. For the most part it works, but there's one issue. I can't copy/ paste from from school account to my home computer or the other way around. Is there a solution to this problem?

You are using clipboard? copy and paste and not drag and drop?

---

### Post by geirha on 2007-11-29
You are running nautilus remotely. It will have no access to your local system. You should connect the other way around, using nautilus locally to connect to your school.

Places -> Connect to server, choose ssh, and other necessary data, then doubleclick the entry it creates in the left-margin of local nautilus windows.

---

### Post by MR.UNOWEN on 2007-11-29
thanks

---

