---
title: "How do I give a user Sudo ing ablitities???"
date: 2006-09-25
forum: General Help
---

### Post by cobbweb on 2006-09-25
Hi, 
   right now im logged into my computer as root in the terminal and would like to know what the command for letting my account be a sudoer. I had problems with it and somehow it broke my sudoing ablities. Thanks 

 Cobbweb

---

### Post by aysiu on 2006-09-25
```
adduser cobbweb admin
```

Full details here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by lamego on 2006-09-25
If you dont want to give admin group privileges you can specify users with or the commands that can be used with:
```
sudo visudo
```

---

