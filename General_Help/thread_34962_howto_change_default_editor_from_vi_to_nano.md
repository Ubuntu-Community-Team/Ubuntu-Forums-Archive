---
title: "howto change default editor from vi to nano?"
date: 2005-05-17
forum: General Help
---

### Post by bpilgrim1979 on 2005-05-17
Hello, how do I change the default console editor from vi to nano?  for my desktop user? root?  

Commands like cvs commit default to vi and I want to switch it.

Thanks.

---

### Post by BackslashN on 2005-05-17
There's an EDITOR variable on your system as well as the CLASSPATH variable. simply change and export it.

EDITOR=nano
export EDITOR

---

### Post by JonahRowley on 2005-05-17
Sometimes I like to use different editors for different things.  To launch a command (for example, crontab) with a different edtior, you don't have to export the variable, you can just say:
```
$ EDITOR=vim crontab -e
```
Another useful environment variable is PAGER.  You can also do some strange things with these, give this a try:
```
$ PAGER="tr A-Za-z N-ZA-Mn-za-m | less" man apt-get
```
You can be sure that no one will be reading over your shoulder!

---

