---
title: "Editing system path problem"
date: 2019-03-28
forum: General Help
---

### Post by gamma1memo on 2019-03-28
I am trying to edit the path that is seen by all programs on my Ubuntu 12.04 computer.  I can change the path by editing the .profile file in my home directory.  However I have a program that complains that it can't find the path to qmake even though I put the path in .profile and even though qmake runs from any directory.  I added the path in /etc/environment but that didn't work.  When I type $path I see a different entry than is in the environment file.

---

### Post by ajgreeny on 2019-03-28
**Firstly, you really should stop using 12.04 as it has had no support now for two years and will be a security risk.**
I suggest a clean install of 18.04 which has another 4 years support.

In general terms that command you used, **$path**, will show nothing at all; it should be **$PATH**.

It is easy to add a folder to the $PATH variable in order that the qmake you are having problems with work as expected.
Which application complains that it can not find qmake.

---

### Post by gamma1memo on 2019-03-29
I should have written $PATH in my message.  I did type it with caps in the terminal.  I was trying to install openCV and got messages that it couldn't find qmake.  I came across a web page this morning that says that when I use sudo the command no longer sees the environmental variables.  Maybe that's the problem.

---

