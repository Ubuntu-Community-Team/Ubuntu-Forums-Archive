---
title: "Updates fail on Ubuntu 13.10"
date: 2013-12-13
forum: General Help
---

### Post by paul1945 on 2013-12-13
I am having a problem. Updates are flagged, download, but the updating program stops halfway through and hangs.
This seems to be an ongoing problem.
Is there a way to clear the obstacle and get this to function properly?
I am a beginner.
Thanks. Paul.

---

### Post by QIII on 2013-12-13
Hello!

Have you had any experience with using the terminal?  It is often much easier to see what is going on if you can paste the results of commands issued in the terminal.

---

### Post by grahammechanical on 2013-12-14
In a terminal run 

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Note any error messages, especially with the second command. Do, you get an icon in the top panel informing you of a failure to update? It sometimes offers a solution as does the apt-get upgrade command.

Regards.

---

### Post by paul1945 on 2013-12-16
Thanks for that, I have gone into the terminal and done as suggested above.
I have attached a text file with a listing which also shows a number of error messages.
I am sorry about the size of this, but that's what came up.
Regards, Paul.

---

### Post by plucky on 2013-12-17
> sudo apt-get update
[sudo] password for paul: 
0% [Working]Ignoring unknown parameter "server role"
Ignoring unknown parameter "server role"
Ignoring unknown parameter "server role"
Ignoring unknown parameter "server role"
Ignoring unknown parameter "server role"

What does your sources.list show you?

From a terminal,copy and paste the outputs for the following commands.

```
cat /etc/apt/sources.list
```
and
```
cat /etc/apt/sources.list.d/*.list
```

---

### Post by paul1945 on 2013-12-18
Here are the listings. Regards, Paul.

---

### Post by claracc on 2013-12-18
In your sources.list file you have to lines ( 51 and 52) corresponding to precise release:

```
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

```

Comment them writing # at the bebinning of the lines, save sources.list and try again to update.

---

