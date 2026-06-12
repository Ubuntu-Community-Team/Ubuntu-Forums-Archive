---
title: "Two Questions. Using Ubuntu Fourteen.Ten."
date: 2015-05-30
forum: General Help
---

### Post by michael290 on 2015-05-30
One. I have this problem. :/ 

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/vivid/universe/i18n/Translation-en  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.



```

Two. How do you check how many procesors Ubuntu is using?

---

### Post by monkeybrain20122 on 2015-05-30
1.That happened to me too, but the problem disappeared after I rebooted. If it doesn't fix itself after a reboot
```
sudo rm /var/lib/apt/lists/* 
sudo apt-get update
```

2.open the terminal, type 
```
top
```
and then type 
```
1
```
you can see usage of the cpu's on the top of the terminal window.


Edited: you said Ubuntu 14.10 but the output you posted indicated that you are using 15.04

---

### Post by michael290 on 2015-05-30
```
michael@michael-Aspire-5335:~$ sudo rm /var/lib/apt/lists/*[sudo] password for michael: 
rm: cannot remove &#8216;/var/lib/apt/lists/partial&#8217;: Is a directory

```
I am trying to upgrade

---

### Post by monkeybrain20122 on 2015-05-30
Oops

should be 
sudo rm -r /var/lib/apt/lists/*

---

### Post by michael290 on 2015-06-01
```
michael@michael-Aspire-5335:~$ sudo rm -r /var/lib/apt/lists/*[sudo] password for michael: 
michael@michael-Aspire-5335:~$ sudo rm -r /var/lib/apt/lists/*
rm: cannot remove &#8216;/var/lib/apt/lists/*&#8217;: No such file or directory
michael@michael-Aspire-5335:~$ 

```

---

### Post by gordintoronto on 2015-06-02
In my experience, archive.ubuntu.com is frequently down. Wait 12 hours and try again.

---

### Post by michael290 on 2015-06-03
still nothing

---

### Post by michael290 on 2015-06-05
Hello?

---

### Post by michael290 on 2015-06-19
Can I get some help?

---

### Post by Bucky Ball on 2015-06-19
Little off-topic, but be aware that 14.10 has just over a month of support remaining before you are going to need to upgrade your release to 15.04. If you've got nothing to lose or have everything backed up, maybe a clean install now would be worth considering.

The problematic repo that is showing in your error in post #1. I presume you didn't install that PPA manually?

---

