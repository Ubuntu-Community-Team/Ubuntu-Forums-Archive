---
title: "More and more problems"
date: 2013-02-13
forum: General Help
---

### Post by yeikel on 2013-02-13
Hi guys , it seems that my experience with Ubuntu is going bad every day that pass , now I am into a new weird problem . All I did was to install and run a few commands like install java , chmod and things like that , I did not install any weird software or so . So that is why I cant understand this problem now :confused: 

The fact is that for an unknow reason I cant login using SSH (it opens , ask me for password and then putty closes :confused::confused: , same thing happen with SFTP , at filezilla I get "Connection closed by server with exitcode 127" . And for be more cool , some programs do not open (LIKE KONSOLE!!!!!)

The true is that I cant understand this , very very weird for me.Right now and with no konsole I cant imagine any fix for this (re-install is the last option)

Thanks for any kind of help :KS 

problem live : [http://i.imgur.com/Nx8PAAT.gif](http://i.imgur.com/Nx8PAAT.gif)

---

### Post by ali abry on 2013-02-13
try connecting with terminal and ssh command by passing two or three `v` to it . 
it give you more verbs output  to find out whats the problem.

```
ssh -vv USER@ADDRESS
```

---

### Post by hawthornso23 on 2013-02-13
Where were you chmod'ing. Wrong permissions on things like config files can cause all sorts of weird stuff to happen.

---

