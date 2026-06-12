---
title: "String replacemet with bash script"
date: 2007-10-10
forum: General Help
---

### Post by theolster on 2007-10-10
Hi, I want to replace some text within a file.  I'm trying to use sed, but I think I'm missing something because it doesn't seem to work!
```
sed '/<#net/ipv4/ip_forward=1>/<net/ipv4/ip_forward=1>/g' "/etc/sysctl.conf"
```Basically I'm trying to remove the # from the line: #net/ipv4/ip_forward=1
within the file /etc/sysctl.conf

Any ideas?

---

### Post by Old *ix Geek on 2007-10-10
You have several problems with your code as it stands now:```
sed '/<#net/ipv4/ip_forward=1>/<net/ipv4/ip_forward=1>/g' "/etc/sysctl.conf"
```For one thing, you need to escape the slashes in the string you're changing, otherwise sed thinks they're part of the command.  Anyway, try this:```
sed 's/#net\/ipv4\/ip_forward=1/net\/ipv4\/ip_forward=1/g' /etc/sysctl.conf
```

---

### Post by theolster on 2007-10-10
Thanks,

It works, but how do I get it to save the file?

Cheers...

---

### Post by bashologist on 2007-10-10
When using paths in sed statements like that it's a good idea to choose a different delimiter like this.
```
sed '\@^#net/ipv4/ip_forward=1$@ s/^#//'
```

---

### Post by Old *ix Geek on 2007-10-10
> **theolster said:**
> It works, but how do I get it to save the file? Sorry, I assumed you knew!  Just redirect its output to a file, like this:```
sed 's/#net\/ipv4\/ip_forward=1/net\/ipv4\/ip_forward=1/g' /etc/sysctl.conf **> your_new_file**
```

In case you don't know, it's ALWAYS a good idea to save the original file...just in case. So in your example, redirect the revised text to something else, such as **/etc/sysctl.conf.revised**.  Then save **/etc/sysctl.conf** as **/etc/sysctl.conf.orig**, THEN overwrite the original one: **mv /etc/sysctl.conf.revised /etc/sysctl.conf**.

---

### Post by theolster on 2007-10-10
Thanks, worked a treat.

---

### Post by bodhi.zazen on 2007-10-10
> **bashologist said:**
> When using paths in sed statements like that it's a good idea to choose a different delimiter like this.
```
sed '\@^#net/ipv4/ip_forward=1$@ s/^#//'
```

+10

You can use underscores as they are easy to read.

---

