---
title: "install ubuntu on an old hp presario 2100"
date: 2013-03-19
forum: General Help
---

### Post by anant12 on 2013-03-19
I want to install ubuntu on an old hp presario 2100. I want to use it as an alternative device to browse internet and some other minor apps with nice look and moreover windows does not work nice on it. So please reply fast guys.
Thanks.

---

### Post by sudodus on 2013-03-19
Welcome to the Ubuntu Forums :-)

It is an old computer, so I would advice that you install the light-weight flavour ***Xubuntu 12.04 LTS*** instead of standard Ubuntu. Furthermore, if you have less than 768 MB of RAM, you should download the ***alternate iso file***, otherwise you can use the standard live desktop Xubuntu iso file. In both cases, use the 32-bit version.

---

### Post by anant12 on 2013-03-19
From what I know ram is 20 gb but physical memory is low and I have already downloaded Ubuntu. As the wifi connection is not working properly and I need to do some work urgently. Can I just use ubuntu or will it work worse than win xp on the low powered laptop. If Ubuntu will not work properly I can install archpup on this one.

---

### Post by mörgæs on 2013-03-19
Something in the Puppy family would be great, but stay away from Ubuntu. 

If you want the Buntu family, Xubuntu (or Lubuntu) is a good option as mentioned above.

Best is to install with wired access and focus on wirefree later.

---

### Post by anant12 on 2013-03-19
Will it not work at all or will still run with little delay.

---

### Post by sudodus on 2013-03-19
> **anant12 said:**
> Will it not work at all or will still run with little delay.
The current versions Ubuntu 12.04 LTS and 12.10 need much more 'horsepower', according to what I found in an internet link about your computer. So Ubuntu will not work at all.

---

### Post by mörgæs on 2013-03-19
According to this
[http://www.cnet.com/laptops/hp-compaq-presario-2100/4507-3121_7-21271063.html](http://www.cnet.com/laptops/hp-compaq-presario-2100/4507-3121_7-21271063.html)
we have a Pentium 4 M and not a Pentium M, so PAE is not a problem.

Anyway, Ubuntu is out of the question due to its (other) hardware requirements. The alternatives mentioned above are worth trying.

---

### Post by anant12 on 2013-03-19
Wat about ubuntu 8 - 10

---

### Post by sudodus on 2013-03-19
> **anant12 said:**
> Wat about ubuntu 8 - 10

These versions are too old. 8 is way past its end of life, and 10.04LTS end of life is next month.

In the Ubuntu family (flavours), you should try Xubuntu 12.04 LTS or Lubuntu 12.10. Xubuntu 12.04 end of live is April 2015 (3 years of support), while Lubuntu 12.10 end of life is April 2014 (18 months of support). After end of life there are no security updates and no bug fixes at all.

---

### Post by anant12 on 2013-03-19
I just want to use the presario as an alternative laptop when my dell inspiron is not available. So, I do not need any security updates. I just want the laptop to be functional for little urgent work.

---

### Post by sudodus on 2013-03-19
Please let us know the size of RAM in your computer! This helps us suggest a suitable flavour of Ubuntu and some other linux distros.

If you want to find out more about tiny linux distros, that work in old computers and/or with small RAM, browse the internet for** tiny linux distros**

---

### Post by anant12 on 2013-03-19
It is 512 mb, upgradable to 1gb.
I have already downloaded archpup but I am really looking forward to use ubuntu on it.

---

### Post by sudodus on 2013-03-19
***Knoppix*** will do fine with 512 MB. ***Lubuntu and Xubuntu*** will also work with this amount of RAM. There will not be so much space for a lot of  applications or web pages or documents at the same time, but if you open one at a time, it will work reasonably well.

Use the ***alternate iso file*** to install Lubuntu and Xubuntu when you have less than 768 MB of RAM.

You will have more memory for applications if you run one of the really tiny linux distros (for example Puppy linux), but the environment might feel less convenient. Try them and decide what is best for you :-)

---

### Post by anant12 on 2013-03-20
what if i upgrade it to 1gb.

---

### Post by sudodus on 2013-03-20
> **anant12 said:**
> what if i upgrade it to 1gb.

Then I suggest that you ***try Lubuntu and Xubuntu***, and select the one you like the best for installation. Or you can do what I do with this old IBM Thinkpad T42 with 1.25 GB ram: Lubuntu 12.04 plus Xubuntu desktop (selectable at the log in screen).
```
sudo apt-get install xubuntu-desktop
```

---

### Post by excollier on 2013-03-20
Try Linux Lite, if it will boot from a dvd. I ended up installing Linux Mint 13 Mate from a cd sized iso because my old Presario 2138EA refused to boot from dvd or usb.
Other options would be Bhodi Linux, PCLinuxOS LXDE (all Ubuntu based) or some other lightweight distro try here for more info:

[URL="http://distrowatch.com/"]http://distrowatch.com/
[/URL]

---

