---
title: "Apache 2 Problem"
date: 2007-06-01
forum: General Help
---

### Post by mazki516 on 2007-06-01
Hi all! 

look on the error i get when i /etc/init.d/apache2 start
```

root@server1home:~# /etc/init.d/apache2 start
 * Starting web server (apache2)...
Syntax error on line 141 of /etc/apache2/apache2.conf:
Invalid command 'Order', 
perhaps misspelled or defined by a module not included in the server configuration
[fail]


```

plz, anyone can help me to fix this problem?

Thanks from advance....
Mazki

---

### Post by tronica on 2007-06-01
well i kinda of gives you your answer in a round about way. Basicly line 141 of that config file is the problem post that line or the file and lets see what the problem is.  Open it in gedit and turn the line numbers by clicking Edit the preferences and then turn line numbers and post that line.

---

### Post by mazki516 on 2007-06-01
well, this is the code,
```

<Files ~ "^\.ht">
    Order Deny
    Deny from all
</Files>

```

anyway, I don't think it connected to the problem. because if i delete those few lines i get the same errors from the other  lines in the page, and if i delete them to...happens again...

---

