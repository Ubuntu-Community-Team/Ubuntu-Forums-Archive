---
title: "Ubuntu is getting slow"
date: 2008-06-14
forum: General Help
---

### Post by dodskaper on 2008-06-14
Hello everyone,

After running ubuntu for two weeks I noticed that Ubuntu was getting slow. After I installed virtual box ubuntu started to act strange. When I start Firefox my whole system becomes slow. Slow in like it takes 2 seconds before the letter you type appears on the screen. After I close Firefox the system stays slow. 

I decided to de-install Virtualbox in the hope that that would be the answer but alas...

I tried a reboot but nothing helps. Does anyone know a solution or some tips?

Thank you in advance

greetz

Dod

---

### Post by dacorr on 2008-06-14
install gpsprocessmonitor and see which process is hogging the CPU

is it a duel cores system?

Dac

---

### Post by dodskaper on 2008-06-14
> **dacorr said:**
> install gpsprocessmonitor and see which process is hogging the CPU

is it a duel cores system?

Dac

No its not a dual core based.

The proces that is the biggest is called Xorg. It used 360MB(of the 512 I have) of RAM memory and takes about 9% of my CPU...

---

### Post by dacorr on 2008-06-14
do you use desktop effects, high screen res, high quality desktop image etc?

the xorg process is the same, for mine. 

How big is the swap partition?

from terminal

sudo fdisk -l

Dac

---

### Post by dodskaper on 2008-06-14
> **dacorr said:**
> do you use desktop effects, high screen res, high quality desktop image etc?

the xorg process is the same, for mine. 

How big is the swap partition?

from terminal

sudo fdisk -l

Dac

Yes I use Compiz and Emerald but use that for the past two weeks now without any problems. But I don't use any high rez because my videocard (basic intel onboard chipset) just can't handle that

the swap partition is 1gb big.

---

### Post by yoman82 on 2008-06-14
I would increase the swap file to 1.5 GB, and try to tone down some of the Compiz and Emerald effects. If you must, buy 1 GB more RAM. It should only be $25-35, not that bad.

---

### Post by HermanAB on 2008-06-14
Before changing things, run 'top' and 'ps -e' to see what is going on and kill offending processes with 'kill -9 PID'.  Google the process names if you don't know what they are.

Cheers,

Herman

---

### Post by dodskaper on 2008-06-15
No idea what happend..

I downgraded Compiz restarted my laptop but nothing changed. I was fed up with it so I called it a night. I just started my laptop again and everything is fast again...:confused:

Thanks for the help guys. You tought me a lot about Linux

---

