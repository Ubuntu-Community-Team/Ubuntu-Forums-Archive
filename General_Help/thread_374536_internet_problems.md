---
title: "internet problems"
date: 2007-03-02
forum: General Help
---

### Post by corytoneill on 2007-03-02
I just installed version 6.10 and i cannot connect to the internet with an Ethernet cord. I went into the system->admin->networking and activated the wired connection but when i try connecting to it the only connection available is called "lo" can anyone help?

---

### Post by invalid on 2007-03-02
What do you get from```
ifconfig
```and```
sudo ifup eth0
```

---

### Post by zvacet on 2007-03-02
After system->admin->networking and activated the wired connection press properties buttton.Thar will open window and you can select type of connection you want(dhcp,static),and chek the upper left box (make this connsction available or something like that).Close.go programs>accessories>terminal
```
sudo pppoeconf
```
If you after all still have problems with your net try this
[http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe]("http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe")

---

