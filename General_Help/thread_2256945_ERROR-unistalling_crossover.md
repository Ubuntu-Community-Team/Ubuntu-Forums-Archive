---
title: "ERROR-unistalling crossover"
date: 2014-12-15
forum: General Help
---

### Post by kccv42 on 2014-12-15
I tired to unistall the demo version of crossover in synaptic package mangaer but i am getting an error.

---

### Post by ajgreeny on 2014-12-16
So what is the error?

---

### Post by kccv42 on 2014-12-16
To un install it. I am trying to delete it.

---

### Post by slickymaster on 2014-12-16
> **ajgreeny said:**
> So what is the error?
@kccv42: this ^^^
Can you please post back in this thread exactly what is/are the error/s you're getting.

Generally, all it takes is to remove it:```
sudo rm -fr /opt/cxoffice
rm -fr ~/.cxoffice 
```

---

### Post by kccv42 on 2014-12-16
It did not work. It asked me for a password but then did nothing. I tried synaptic packages software to remove it and here is the error. E: crossover: subprocess installed pre-removal script returned error exit status 127

---

### Post by slickymaster on 2014-12-17
Can you please post back in the thread the output you get running the following command in a terminal window```
dpkg --get-selections | grep crossover
```

---

### Post by kccv42 on 2014-12-18
```

dpkg --get-selections | grep crossover
crossover                    purge

```

---

### Post by slickymaster on 2014-12-19
Can you please try, in a terminal window, the following commands, one at a time:```
sudo -i
cd /opt/cxoffice/bin
./cxuninstall

```

---

### Post by kccv42 on 2014-12-20
```

root@computer4:~# cd /opt/cxoffice/bin
-bash: cd: /opt/cxoffice/bin: No such file or directory
root@computer4:~# ./cxuninstall
-bash: ./cxuninstall: No such file or directory

```

---

### Post by slickymaster on 2014-12-22
I would advise you to prompt CodeWeavers to investigate this by submitting a [support ticket]("https://www.codeweavers.com/support/tickets/enter/")

---

### Post by kccv42 on 2014-12-23
ok thanks

---

