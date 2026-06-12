---
title: "Which version am I running?"
date: 2007-02-03
forum: General Help
---

### Post by gjtoth on 2007-02-03
I *think* I just upgraded to Feisty but am not sure it "took".  Is there a way to see what version I'm running from the console? :confused:

---

### Post by danielph on 2007-02-03
System, About Ubuntu

see below you said console doh

---

### Post by 23meg on 2007-02-03
```
lsb_release -a
```

---

### Post by jimbob on 2007-02-03
If you do a uname -a from the terminal it will show you the kernel anyway.

Do a cat /etc/apt/menu.lst and see if all the debs point to feisty.

Don't really know how to get it to show version 7.0x or whatever Feisty is now.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by gjtoth on 2007-02-03
> **23meg said:**
> ```
lsb_release -a
```

As I suspected... it didn't take.  Drat!

Thanks!

---

### Post by 23meg on 2007-02-03
You're welcome. Remember to do a forum search before asking questions in the future.

---

