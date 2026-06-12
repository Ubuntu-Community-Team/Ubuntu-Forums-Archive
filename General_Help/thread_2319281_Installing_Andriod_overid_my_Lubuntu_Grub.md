---
title: "Installing Andriod overid my Lubuntu Grub"
date: 2016-04-02
forum: General Help
---

### Post by joel45 on 2016-04-02
Can't boot into Lubuntu or Android. 
after installing Andriod to Sda4. It would get as far as detecting android and gets stuck on a black screen. Guessing debug could fix this not sure how. 

I accidentally overid my Lubuntu Grub so it only shows Android boot options. Andriod and Debug. And Command prompt. 
Lubuntu is on Sda2. 

Would like to be able to Dual Boot Lubuntu and Android or at least just Lubuntu again. Running Acer TouchScreen Laptop

---

### Post by sammiev on 2016-04-02
Hi,

If you can boot Lubuntu from a USB/DVD and open up a terminal window.

try these two lines from within terminal.

```
sudo grub-install /dev/sda
```

```
sudo update-grub
```

---

### Post by joel45 on 2016-04-02
Is there not a command line I can use to boot Lubuntu from the Android Grub terminal.

grub>

---

