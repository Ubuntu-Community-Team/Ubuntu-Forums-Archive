---
title: "Quick question about displaying commands"
date: 2007-07-18
forum: General Help
---

### Post by jonlemur on 2007-07-18
Hello,

I was wondering if there is a command you can enter in the terminal that will display all of the commands you can enter in the terminal.  For instance, I can hit tab tab to display all of the commands the terminal will recognize (or at least a number of them).  But I can't pipe that off to something else, like grep, to narrow down the search, say to display only commands beginning with "g"  Is there a text command that I can enter to do this?

Thanks

---

### Post by HermanAB on 2007-07-18
ls /bin/g*
ls /sbin/g*
ls /usr/bin/g*

---

### Post by NT4usB on 2007-07-18
If you type the beginning of a command, one or two letters, and Tab twice it will list all the commands that begin with those letters (or warn you there are a bazillion and do you want to see them all?)
So, g Tab Tab will get you all the commands that start with g.

---

### Post by strabes on 2007-07-18
whoops, sorry.

---

### Post by jonlemur on 2007-07-20
Thank you for your suggestions, and they will help in the majority of my searching.  But I'm still looking for something that I can pipe, and tab + tab won't work for that (at least not that I know of).  Is there a way that I could write a script to do that, even if it just issues the command tab + tab.  Then perhaps I could run 

myScript | grep *lab

or something along those lines.

I'm very new to writing scripts though, and I don't know if I could do something like that.

Thanks

---

