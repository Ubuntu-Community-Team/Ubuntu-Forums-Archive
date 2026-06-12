---
title: "Azureus and limewire command line based?"
date: 2005-04-23
forum: General Help
---

### Post by cloudz14 on 2005-04-23
Hi

I know we can invoke gaim from xterm, what I would like to do is to add the command azureus and limewire to /usr/bin/ directory so that I can invoke the program from command line interface. So how should I do this? I can't just copy across the azureus command from /opt/azureus/ ?

thanks A bunch.

Johan

---

### Post by doclivingston on 2005-04-24
What you want to do is create a symlink to it in /usr/bin.

```
ls -s /path/to/azureus /usr/bin
```

---

### Post by cloudz14 on 2005-04-24
did u mean ln instead of ls?
 
create symlink using ls?

I dun quite get that... could you explain a bit more?

Thanks !! 

 O:)

---

### Post by telmo on 2005-04-24
If you search this forum for that particular problem, you'll find your answer... ;)

---

### Post by doclivingston on 2005-04-24
Oops. ln -s was what I meant.

---

