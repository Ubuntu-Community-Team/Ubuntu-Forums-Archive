---
title: "Terminal can't handle directory names with spaces in them e.g. Ubuntu One"
date: 2013-11-28
forum: General Help
---

### Post by rdh61 on 2013-11-28
Hi,

I've found out that terminal commands cannot handle directory names with spaces in them. One might think the answer is simple - avoid putting spaces in directory names. But the Ubuntu One directory is called Ubuntu One by default, and a good guess is that Ubuntu One will not work if I delete the space. But if I want to cd into that directory, I get: 

```
robert@robert-desktop:~$ cd /home/robert/Ubuntu One
bash: cd: /home/robert/Ubuntu: No such file or directory
robert@robert-desktop:~$ 
```

Why do I want to do that? Because I want to create an encrypted directory in Ubuntu One using encfs. Example:

```
robert@robert-desktop:~$ encfs ~/.safe ~/Ubuntu One/Safe
The directory "/home/robert/.safe/" does not exist. Should it be created? (y,n) y
The directory "/home/robert/Ubuntu" does not exist. Should it be created? (y,n) 
```

Again, the terminal does not recognise the directory name "Ubuntu One".

How can I get around this?

Many thanks.

---

### Post by Old_Grey_Wolf on 2013-11-28
Try using the "\" i.e.
```
cd /home/robert/Ubuntu\ One
```

---

### Post by steeldriver on 2013-11-28
^^^ this - note as well that if you use tab completion, bash will fill in the \ escape for you. Or quote the whole name 

```

cd "/home/robert/Ubuntu One"

cd '/home/robert/Ubuntu One'

```

---

### Post by rdh61 on 2013-11-29
Thanks to both!

---

