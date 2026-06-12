---
title: "Help with WINE"
date: 2008-01-09
forum: General Help
---

### Post by pedrom169 on 2008-01-09
i dont know if this is the proper place to put this.

im new to ubuntu
i was wonder if someone could help or give me a easy to understand website for downloading and installing WINE (or a program like it that is better)

my computer is not on internet

thanks in advance

Peter

---

### Post by wieman01 on 2008-01-09
It is in the repositories, so when you open Synaptic, you should be able to install it from CD. I don't think there is a need to download it.

---

### Post by pedrom169 on 2008-01-09
sorry for the stupid questions

Synaptic << whats that?

---

### Post by wieman01 on 2008-01-09
Sorry... right... it't the package manager? Can you find it? I think it is under "Administration" or similar...

---

### Post by pedrom169 on 2008-01-09
sorry. i cant access my ubuntu computer atm. im at work.

i was just looking for a guide of some sort for when i get home.

sorry for inconvience

Peter

---

### Post by wieman01 on 2008-01-09
> **pedrom169 said:**
> sorry. i cant access my ubuntu computer atm. im at work.

i was just looking for a guide of some sort for when i get home.

sorry for inconvience

Peter
No problem, Peter. You'll figure it out. It is very simple. Post here if you have issues, we will help you out.

---

### Post by pedrom169 on 2008-01-09
one more question.

how would i go updating it without internet

or is it not possible?

Peter

---

### Post by wieman01 on 2008-01-09
> **pedrom169 said:**
> one more question.

how would i go updating it without internet

or is it not possible?

Peter
Install it from CD, but you need to have internet connection to update it. Or get the .DEB installer file for WINE. You find more information here:

[http://winehq.org/site/download-deb]("http://winehq.org/site/download-deb")

Really the easiest way is by downloading the stuff. Is there no Internet available where you are at home?

---

### Post by pedrom169 on 2008-01-09
yes on the pc in the family room.

the ubutu pc is in my room

Peter

---

### Post by wieman01 on 2008-01-09
> **pedrom169 said:**
> yes on the pc in the family room.

the ubutu pc is in my room

Peter
Then you could connect your PC to the Internet connection once in a while and update your system. That's the easiest route.

---

### Post by pedrom169 on 2008-01-09
what do i need to do to update?

Peter

---

### Post by wieman01 on 2008-01-09
Ok, to install it while you are connected to the Internet, open a terminal window (command line window) and type:
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```
```
sudo apt-get update
```
```
sudo apt-get install wine
```
Enter your user password when prompted. 

To update to the latest version, simply do:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
The last 2 commands will update all software packages including WINE provided that the Internet connection is working. I assume your are on **Gutsy**...

---

