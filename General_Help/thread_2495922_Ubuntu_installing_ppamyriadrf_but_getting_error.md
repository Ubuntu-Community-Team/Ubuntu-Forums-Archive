---
title: "Ubuntu installing ppa:myriadrf but getting error"
date: 2024-03-07
forum: General Help
---

### Post by sairfan1 on 2024-03-07
I'm trying to install software for HackRF one on my freshly setup Ubuntu machaine, after installing OS i updated it.


Then I installed python3 and followied the instruction at QSepctrum Analyzer git page as below

[QSpectrum Analyzer Github page]("https://github.com/xmikos/qspectrumanalyzer")


At above page if you see instruction for Unbunto OS first command to run is


```
sudo add-apt-repository -y ppa:myriadrf/drivers

```



But I get error message


> ERROR: ppa 'myraidrf/drivers' not found


I'm not well experienced in linux (Ubuntu) looking for help

---

### Post by ajgreeny on 2024-03-08
It looks as if activity of that ppa has mainly ended; the only recent package is **limesuite**, but I know nothing about that or what it is for.
Python3 is a default in all currently supported Ubuntu family versions so wonder why you installed it; what version of Ubuntu are you running?

---

### Post by sairfan1 on 2024-03-08
I'm running Ubuntu 22.04.4 LTS (I did not know phython comes builtin that's why i installed it)

> It looks as if activity of that ppa has mainly ended;
Do you mean ppa:myriadrf/drivers is not a valid package anymore?

---

### Post by deadflowr on 2024-03-08
What's up with the discrepancy between the the command to add the PPA  and the error.
one is myriadrf and the other is myraidrf

---

### Post by coffeecat on 2024-03-09
Support, not chat. *Thread moved to **General Help**.*

---

