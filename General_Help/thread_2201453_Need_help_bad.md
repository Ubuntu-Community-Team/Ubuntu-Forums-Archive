---
title: "Need help bad"
date: 2014-01-24
forum: General Help
---

### Post by Kyle_Tyner_ on 2014-01-24
I successfully installed ubuntu with lots if trial and error and once I did te first boot I had many problems the wifi connected for a short while and the. Would go right off then the screen glichs bad everywhere I move te mouse the screen make lines an such and I cannot fix any of the problems without internet please could I have some help.

---

### Post by Rick1971 on 2014-01-24
you have to give more info than that...was it on a separate HDD or did you try to partition, was it 64 bit ot 32?

---

### Post by Kyle_Tyner_ on 2014-01-24
I installed as the main os it was 64bit

---

### Post by Rick1971 on 2014-01-24
did you partition or over-right the current O/S?

---

### Post by 9k0aefbmMtuJ on 2014-01-24
Please tell us 
- what version of Ubuntu you are installing
- where you download it from
- what medium (CD/DVD/USB drive, Flash drive, etc)  you are booting from to do the install
- if Ubuntu running off the live medium runs successfully
- what device you are installing Ubuntu on
- the hardware specification of that device (RAM size, Storage size, CPU speed, etc)

---

### Post by Kyle_Tyner_ on 2014-01-24
I over righted the current os 
My specs are 8 gb ram 
750 hard drive space 
I inisralled from a usb 
It barley runs 
The version was the latest that I received from the ubuntu website
I cannot currently get the rest of my specs to to tech problems

---

### Post by Rick1971 on 2014-01-24
is this your only comp?

---

### Post by Kyle_Tyner_ on 2014-01-24
The only one I have admin rights on

---

### Post by Rick1971 on 2014-01-24
well my suggestion is to try again, only burn a DVD of the ISO and boot from that, then install from there, it has never failed me before, and I have done this a dozen times with dozen different distros...

---

### Post by Kyle_Tyner_ on 2014-01-24
I am going to try Linux mint it looks more stable for a beginer

---

### Post by Rick1971 on 2014-01-24
like I said would burn a DVD

---

### Post by Bucky Ball on 2014-01-24
If it is the latest, 13.10, try 12.04 LTS, available below 13.10 from the same webpage. Sometimes makes a difference.

---

### Post by varunendra on 2014-01-24
> **Kyle_Tyner_ said:**
> I successfully installed ubuntu with lots if trial and error and once I did te first boot I had many problems the wifi connected for a short while and the. Would go right off .... I cannot fix any of the problems without internet please could I have some help.

May I assume fixing wifi is your first goal then? If it is a driver problem, it would be same on all flavours of Linux since they more or less use the same kernel, hence same driver.

My we see details of your wireless card and the driver in use? The quickest way - Please open a terminal (Ctrl-Alt-T) and run the following command in it -
```
lspci -nnk | grep -iA2 net
```
Note down the complete output (as it is, formatting is not important but line breaks are), and post it back here.

Is a wired connection or any other means to connect (like a usb modem) an available option? It will make things much easier should we need to install some packages.

**PS:**
I second the suggestion to try out the LTS (12.04). Usually (although not always) it is more stable.

---

### Post by GrouchyGaijin on 2014-01-24
> **Kyle_Tyner_ said:**
> I am going to try Linux mint it looks more stable for a beginer

I don't think the problem is Ubuntu versus Mint.  The problem is more likely the USB install method.
I've had trouble installing from a USB stick in the past.  I've never had trouble installing from DVD.

---

### Post by Rick1971 on 2014-01-24
I always install from DVD and have never had problems with that...

---

