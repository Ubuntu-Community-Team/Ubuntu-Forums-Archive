---
title: "How to install docker-ce under Kubuntu 18.04 ?"
date: 2019-09-06
forum: General Help
---

### Post by petrogromovo on 2019-09-06
Hello, 
in my Kubuntu 18.04 I tried to install docker-ce :
```
$ sudo apt-get install docker-ce
...
E: Package 'docker-ce' has no installation candidate

```
Searching in next I found a decision for [COLOR=#242729]17.10 [/COLOR], but got next error :
```
deb [arch=amd64] https://download.docker.com/linux/ubuntu artful stable
...
Command 'deb' not found, did you mean:

```

1) I searched in net how to make deb running, but drowned in old versions decisions and still is not sure which 
decision is valid for  Kubuntu 18.04 ?

2) Is deb command for  Kubuntu 18.04 the same as I wrote for [COLOR=#242729]17.10[/COLOR] ?

Thanks!

---

### Post by cruzer001 on 2019-09-06
try
```
apt policy docker
```

---

