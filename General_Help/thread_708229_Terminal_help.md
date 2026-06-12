---
title: "Terminal help"
date: 2008-02-26
forum: General Help
---

### Post by Sisophon2001 on 2008-02-26
Hi

I accidentally typed the ' (single quote) character as part of a command in gnome terminal, and the prompt changed and became >. After this what ever I type does nothing, until I use Ctrl-C

Example
```
~$ ls' 
> ls
> cd /
> 
~$ 
```

What is the purpose of the single quote in this usage, and what does the > prompt mean?

Thanks

Garvan

---

### Post by plucky on 2008-02-26
> What is the purpose of the single quote in this usage, and what does the > prompt mean?

See [here](http://www.linuxcommand.org/wss0060.php#quotes) for explanation.The > is waiting for another ' to close the text quote.


Hope this helps.

---

### Post by mali2297 on 2008-02-26
It enables you to input several lines, for example
```

$ echo 'Hello
> World.'

```
End it with another single-quote.

---

### Post by Sisophon2001 on 2008-02-26
Thanks to all.

Garvan

---

