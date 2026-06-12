---
title: "how to filter tree on ubuntu?"
date: 2014-12-29
forum: General Help
---

### Post by random512 on 2014-12-29
Hello, I used WinSCP to create the following directory on Ubuntu: /home/ubuntu/MyJsScripts

I uploaded HelloWorld.js to this directory.  Now I'm trying to execute HelloWorld.js.  I installed tree to see the directory structure but a basic tree command returns 1520 directories.  How can I filter this directory structure to find the directory "MyJsScripts" and then navigate to this directory through ubuntu?  

In windows I would simply execute cd c:\home\ubuntu\MyJsScripts\ which would take me to the command prompt.

---

### Post by schragge on 2014-12-29
cd works in Ubuntu just like in Windows:
```
cd /home/ubuntu/MyJsScripts
``` You can pass to *tree* the directory to start from, too:
```
tree /home/ubuntu/MyJsScripts
```
To filter results of tree, try
```
tree -P \*.js --prune
```
The first option (-P) tells tree to only show files that satisfy the pattern (end in .js), the second (--prune) -- not to show directories that do not contain files to be shown.

---

### Post by random512 on 2014-12-29
@schragge - perfect thanks for your help :)

---

