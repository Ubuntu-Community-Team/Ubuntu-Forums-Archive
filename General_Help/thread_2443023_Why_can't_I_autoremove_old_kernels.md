---
title: "Why can't I autoremove old kernels"
date: 2020-05-10
forum: General Help
---

### Post by Vtwin on 2020-05-10
Kubuntu 20.04 
Ryzen 3200G using onboard graphics
240GB SSD
16GB ddr4 2666

Hi
I've recently started using Kubuntu 20.04 in a dual boot with Linux Mint 19.3. I decided to remove my oldest kernel as I had three installed. Mint has a very easy GUI for doing this but with Kubuntu I tried to use autoremove as described at [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels). No kernels showed up as being auto installed. I followed the instructions to remove the oldest kernel. My question is why the 3 kernels show up as manually installed when they were all done using the normal updates available procedure. The removal was easy enough but I've searched and haven't been able to come up with an answer.

---

### Post by xxteraxx on 2020-05-12
Most linux distributions only autoremove after you have 4 kernels installed.  then it will only remove the oldest of the 4. So you will still have the other 3.  You could just purge the kernel and the headers like you would with any other app if you want

---

### Post by Impavidus on 2020-05-13
Ubuntu only keeps two. I don't know how the mechanism works exactly, but I think it takes a short while before it's offered for autoremoval. At least you have to reboot using the new kernel. I don't know about Mint, but Kubuntu must do this in the same way as every other Ubuntu flavour.

---

### Post by Vtwin on 2020-05-13
I know how to remove old kernels but I was curious as to why they show up as manually installed when I didn't use apt-get to update them. Maybe it is just a matter of waiting longer. Thanks for your replies.

---

### Post by ActionParsnip on 2020-05-13
Never seen this but then again I manually remove kernels to save space......

---

### Post by mastablasta on 2020-05-14
can you post the output you get when trying to auto remove and also what kernels you currently have installed?

```
sudo apt autoremove
```

[i moved to apt instead of apt-get]

old kernels don't take that much space and may come in handy when something goes wrong. still one or two old ones max should be enough.

---

### Post by Vtwin on 2020-05-15
mastablasta I'm showing output for kernels that show as manually installed as well. The ou[FONT=arial][/FONT]tput for sudo apt autoremove showed nothing. I used 
sudo apt-mark auto '^linux-.*-5\.4\.0-26(-generic)?$'

to remove the old kernel with the correct kernel version of course which I can't remember.
scott@Kub-3200G:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
scott@Kub-3200G:~$ apt-mark showauto 'linux-image-.*'
scott@Kub-3200G:~$ apt-mark showmanual 'linux-image-.*'
linux-image-5.4.0-28-generic
linux-image-5.4.0-29-generic
linux-image-generic

---

### Post by ActionParsnip on 2020-05-15
what is the output of:

```

uname -a; echo; dpkg -l | grep linux-image

```

Thanks

---

### Post by Vtwin on 2020-05-15
Hi this is the output you asked for

scott@Kub-3200G:~$ uname -a; echo; dpkg -l | grep linux-image
Linux Kub-3200G 5.4.0-29-generic #33-Ubuntu SMP Wed Apr 29 14:32:27 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

ii  linux-image-5.4.0-28-generic                  5.4.0-28.32                                 amd64        Signed kernel image generic
ii  linux-image-5.4.0-29-generic                  5.4.0-29.33                                 amd64        Signed kernel image generic
ii  linux-image-generic                           5.4.0.29.34                                 amd64        Generic Linux kernel image

---

