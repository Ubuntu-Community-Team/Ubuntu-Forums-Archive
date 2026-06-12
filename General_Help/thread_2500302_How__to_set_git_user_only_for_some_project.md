---
title: "How  to set git user only for some project ?"
date: 2024-08-29
forum: General Help
---

### Post by nilovsergey on 2024-08-29
When under ubuntu 22.04 I init git system I use command like
```

git config --global user.email "myname@site.com" 
git config --global user.name "myname@site.com"

```
To set my user's account for all git projects.
But how in some project to set different user only for this project ?

---

### Post by currentshaft on 2024-08-29
0

---

### Post by nilovsergey on 2024-08-30
1) The same format of the command, but without "[COLOR=#000000][FONT=&quot]--global[/FONT][/COLOR]" ?
2) Which lines have I to add to /.git/config ?

---

### Post by currentshaft on 2024-08-31
```
cd $(mktemp -d)
git init
git config user.name "myname@site.com"
git config user.email "myname@site.com"
cat .git/config
[user]
name = [email]myname@site.com[/email]
email = [email]myname@site.com[/email]
```

---

