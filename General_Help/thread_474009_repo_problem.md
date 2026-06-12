---
title: "repo problem"
date: 2007-06-14
forum: General Help
---

### Post by Irti on 2007-06-14
ok whenever i try to do  
/etc/apt/sources.list 
it always says 
 bash: /etc/apt/sources.list: Permission denied
even wen i do
sudo -i
and get to the root....its the same....can anyone please help me sort this out

---

### Post by jasonlfunk on 2007-06-14
If you are trying to edit it try:
```

gksudo gedit /etc/apt/sources.list
```

---

### Post by Irti on 2007-06-14
o crap.....ya right....thanx a lot

---

