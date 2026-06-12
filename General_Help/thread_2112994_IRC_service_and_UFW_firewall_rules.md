---
title: "IRC service and UFW firewall rules"
date: 2013-02-06
forum: General Help
---

### Post by desesperado on 2013-02-06
Hello all.

I am securing my computer following the [superbeb Dangertux thread]("http://ubuntuforums.org/showthread.php?t=1876124") and have created same rules by utilizing UFW at CLI.

My question is this, in order to allow IRC services with XChat 2.8.8, and because IRC service uses ports 6667 through 7000 (according to Dangertux's thread) do I have to write a rule for each port, like:
```
sudo ufw allow out 6667/tcp
sudo ufw allow out 6668/tcp
sudo ufw allow out 6669/tcp
....
sudo ufw allow out 7000/tcp
```
Or can I do something this way:
```
sudo ufw allow out 6667:7000/tcp
```

On the same subject let me ask you another question, does IRC just uses TCP protocol or do I also have to write equal rules for the UDP protocol?

---

### Post by desesperado on 2013-02-06
Pretty please :(

---

### Post by desesperado on 2013-02-06
No one??? :o:confused::(

---

### Post by slickymaster on 2013-02-06
> **desesperado said:**
> ```
sudo ufw allow out 6667:7000/tcp
```

Yes, there's nothing wrong with your syntax. 6667:7000 matches all ports from 6667 up to and including 7000.
The only thing though, is that IRC protocol TCP, on Ubuntu Servers defaults to 8001.

---

### Post by desesperado on 2013-02-07
Ok, thanks a lot.
```
sudo ufw allow out 8001/tcp
```

---

