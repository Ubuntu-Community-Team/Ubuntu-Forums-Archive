---
title: "installing software using *.tar.gz file"
date: 2008-06-07
forum: General Help
---

### Post by jyesj on 2008-06-07
i have downloaded a sip phone software. myfile.tar.gz file and successfully created a folder in my /home/tom/x-hight say for example expanded file with "tar -zxvf myfile.tar.gz" it has created a folder,  inside it has one  file and  say softphone and readme.  that says for permisstion run "chomd +x softphone" but it says no chomd command then i try to run the file like this "./softphone" but it is also not executing or working what to do. kindly help

---

### Post by LoneWolfJack on 2008-06-07
chomd = chmod

probably a typo that kills all efforts made by newbies. 
no need to be embarrassed though, we've all been there.

---

### Post by rune0077 on 2008-06-07
It's a typo. The correct command is:

```
chmod +x softphone
```

EDIT: beaten to the punch :)

---

### Post by drs305 on 2008-06-07
Here are a couple of links that can answer most installation questions:
How to install ANYTHING in Ubuntu!:  [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Ubuntu Guide: Hardy: [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

---

