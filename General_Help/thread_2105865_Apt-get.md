---
title: "Apt-get"
date: 2013-01-17
forum: General Help
---

### Post by ravi sharan on 2013-01-17
Hello All,
                  I am using Ubuntu since almost three years. Today absent mindedly instead of typing :

```
sudo apt-get update
```and then
```
sudo apt-get upgrade
```I typed :

```
sudo apt-get install
```and the terminal spit out this :

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.So my question is does apt-get install too check for updates???

Kindly help me out learning what is what... I am looking forward to know about this.

Regards,
Ravi Sharan

---

### Post by ibjsb4 on 2013-01-17
Nope, it don't  :)

[https://help.ubuntu.com/community/AptGet/Howto#Installation_commands](https://help.ubuntu.com/community/AptGet/Howto#Installation_commands)

---

### Post by zombifier25 on 2013-01-17
In short: you installed blanks.

---

### Post by ravi sharan on 2013-01-17
Well what exactly is a blank ??? I am hearing it for the first time :p

---

### Post by Frogs Hair on 2013-01-17
You would insert the package name in lower case after install.

See the link command learning resources in absolute beginner talk. To investigate apt-get in your terminal use the following command. 

```
man apt-get  
```

---

### Post by ravi sharan on 2013-01-17
> **Frogs Hair said:**
> You would insert the package name in lower case after install.

See the link command learning resources in absolute beginner talk. To investigate apt-get in your terminal use the following command. 

```
man apt-get  
```

That I know of. But I was just sarcastically mentioning what a blank package was :p hehee. Anyway I will mark this as solved.

---

