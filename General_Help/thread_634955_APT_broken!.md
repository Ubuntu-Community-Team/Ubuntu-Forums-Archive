---
title: "APT broken!"
date: 2007-12-08
forum: General Help
---

### Post by x-demon on 2007-12-08
Damn... Looks like i broke APT...
root@X-demon:~# apt-get install compiz
Reading database... done
Building dependency tree 
try*`apt-get -f install':
Unresolved dependencies:
  compiz: depend: compiz-fusion-plugins-main (>= 0.5.2+git20070917) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
          depend:: compiz-fusion-plugins-extra (>= 0.5.2+git20070917) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
E: Unresolved dependencies&#1080;. try 'apt-get -f install'

It happened in EVERY apt-get install/remove command...
remove --purge not working
What i must do?

---

### Post by PmDematagoda on 2007-12-08
Try:-
```

sudo apt-get install -f
```

---

### Post by x-demon on 2007-12-08
> **PmDematagoda said:**
> Try:-
```

sudo apt-get install -f
```

 /var/cache/apt/archives/compiz-fusion-plugins-main_0.5.2+git20070928-0ubuntu2_i386.deb
 /var/cache/apt/archives/compiz-fusion-plugins-extra_0.6.0+git20071121-0ubuntu1~gutsy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by x-demon on 2007-12-08
This happened when i performing full system upgrade... To gibbon... Updater unexpectly closed when downloading files... Please help, i configure this system for me, build custom kernel, and now i doesnt want lose it.

---

### Post by PmDematagoda on 2007-12-08
Hmm, I think I may have got it, post the result of:-
```

cat /etc/apt/sources.list
```

---

### Post by x-demon on 2007-12-08
> **PmDematagoda said:**
> Hmm, I think I may have got it, post the result of:-
```

cat /etc/apt/sources.list
```
I already fix it! Just
dpkg -r desktop-effects
then
dpkg -r compiz
That's all! I am noob =(

---

### Post by PmDematagoda on 2007-12-08
Good for you:lolflag:.

---

### Post by x-demon on 2007-12-08
> **PmDematagoda said:**
> Good for you:lolflag:.
Damn, i can configure and compile kernel, but i can't fix small errors... hahahah....

---

