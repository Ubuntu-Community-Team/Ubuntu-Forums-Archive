---
title: "Issue with php5-curl installation"
date: 2013-06-08
forum: General Help
---

### Post by realestateworld on 2013-06-08
[COLOR=#000000][FONT=Arial]I currently have PHP 5.4.14-1~quantal+1 (cli) installed on my Ubuntu 13.04 and I tried to install php5-curl but I have a dependency issue[/FONT][/COLOR]

$ sudo apt-[COLOR=#00008B]get[/COLOR] update$ sudo apt-[COLOR=#00008B]get[/COLOR] upgrade$ sudo apt-[COLOR=#00008B]get[/COLOR] install php5-curl[COLOR=#000000][FONT=Arial]"php5-curl : Depend: php5-common (= 5.4.9-4ubuntu2) but 5.4.14-1~quantal+1 should be installed"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Do someone has any idea how to fix this problem?[/FONT][/COLOR]

---

### Post by realestateworld on 2013-06-08
Is anyone know this?

---

### Post by oldos2er on 2013-06-08
Please wait 24 hours between bumps.

---

### Post by sandyd on 2013-06-08
> **realestateworld said:**
> [COLOR=#000000][FONT=Arial]I currently have PHP 5.4.14-1~quantal+1 (cli) installed on my Ubuntu 13.04 and I tried to install php5-curl but I have a dependency issue[/FONT][/COLOR]

$ sudo apt-[COLOR=#00008B]get[/COLOR] update$ sudo apt-[COLOR=#00008B]get[/COLOR] upgrade$ sudo apt-[COLOR=#00008B]get[/COLOR] install php5-curl[COLOR=#000000][FONT=Arial]"php5-curl : Depend: php5-common (= 5.4.9-4ubuntu2) but 5.4.14-1~quantal+1 should be installed"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Do someone has any idea how to fix this problem?[/FONT][/COLOR]
For some reason, apt-get is trying to download a quantal version of php.

Can you post the output of
```

cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

Thanks.

---

