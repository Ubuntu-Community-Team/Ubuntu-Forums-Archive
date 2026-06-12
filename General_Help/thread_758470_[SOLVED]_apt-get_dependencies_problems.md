---
title: "[SOLVED] apt-get dependencies problems"
date: 2008-04-18
forum: General Help
---

### Post by Kissell on 2008-04-18
I've created a big mess, and I need help!

Anytime I attempt to install anything, I'm told I don't meet dependencies...  this is what I get when trying to install postfix.

> root@Server:~# apt-get install postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  scrollkeeper: Depends: libscrollkeeper0 (>= 0.3.8) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@Server:~# 


---

### Post by NightwishFan on 2008-04-18
```
sudo apt-get -f install
```

---

### Post by rakris on 2008-04-18
U may have to do apt-get clean.

Or try installing the previously abrubtly stopped apt-get process//

---

### Post by Kissell on 2008-04-18
hmmm...  that actually worked...  

I never use "sudo" before my commands because I switch ahead of time by typing in "sudo -s" which I thought made typing sudo before every command unnecessary.

i've tried "apt-get -f install" many times...  but it never worked...   "sudo apt-get -f install" seems to work though...  weird. 

Thanks!

---

### Post by NightwishFan on 2008-04-18
I am absurdly pleased I was of service, sir. :)
Welcome to Ubuntu Forums.

---

