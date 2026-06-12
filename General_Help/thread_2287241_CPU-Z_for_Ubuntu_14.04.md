---
title: "CPU-Z for Ubuntu 14.04"
date: 2015-07-17
forum: General Help
---

### Post by meetdilip on 2015-07-17
I tried to use I-Nex using 

```

sudo   add-apt-repository ppa:gambas-team/gambas3
sudo add-apt-repository ppa:i-nex-development-team/stable
  sudo apt-get update
  sudo apt-get install i-nex


```

but I couldn't add gambas ppa as it says open key ( or may be public key) missing. Any way out will be great. Thanks.

---

### Post by v3.xx on 2015-07-18
Did it say no pubkey?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gpg+error+no_pubkey&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gpg+error+no_pubkey&sa=Search&cof=FORID:9)

---

### Post by sudodus on 2015-07-18
If you want to install ***cpu-z*** because you want to know the hardware, you can also use the following linux tools

***lshw***

The following commands create the file **lshw.txt** with a list describing the hardware.

```
sudo -s
lshw -sanitize > lshw.txt
exit  # exit from the elevated permissions
```

I think lshw is already installed in Ubuntu and the Ubuntu family flavours.

***hardinfo***

This GUI program is installed in Lubuntu, but maybe not in all Ubuntu family flavours. You can install it from the repositories

```
sudo apt-get install hardinfo
```

or with the Ubuntu ***Software Center***.

---

