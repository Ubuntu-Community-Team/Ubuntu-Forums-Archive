---
title: "Strange Synaptic errors"
date: 2007-07-27
forum: General Help
---

### Post by jrtpaul on 2007-07-27
HI, i just had to re-install Ubuntu 7.04, and now when i try to download and install programs via Synaptic, i get an error telling me that the prgram cannot be installed on my computer type (i386). This is the first time i have ever seen had this error, and it has only happened since i re-installed. My processor is an x86-64 but i have the 32-bit version of Ubuntu. 

Any suggestions or help will be greatly appreciated!

---

### Post by garionw on 2007-07-27
I'm getting the same problem and I only just installed Feisty today (about 20 minutes ago)

I have a 32bit processor and using the 32bit version

---

### Post by Espreon on 2007-07-27
Maybe the programs you are trying to install only work on 32-bit processors.

---

### Post by jrtpaul on 2007-07-27
Also whenevr i try to reload the application list i get an error about the repo's not being available (either because there is something wrong with them)

Edit :   It cant be that because i have used them before. BTW it is every application there not just some of them.

---

### Post by bikeboy on 2007-07-27
Can you show us what's in your /etc/apt/sources.list by doing the following please?

Applications > Accessories > Terminal ```
cat /etc/apt/sources.list
```

I think I know the problem, but this should help confirm it.

---

### Post by garionw on 2007-07-27
> **Espreon said:**
> Maybe the programs you are trying to install only work on 32-bit processors.

Thats the thing, I've got a 32bit processor, downloaded the i386 edition, had it work in the past, but not now

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe


---

### Post by bikeboy on 2007-07-27
Also, what ISP are you with?

---

### Post by jrtpaul on 2007-07-27
Sure, here it is:


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse




Didnt put commented stuff. Thanks for everyones help .

ISP: Bigpond (Telstra)

---

### Post by garionw on 2007-07-27
I'm from Internode (also Tasmania, Australia)

---

### Post by jrtpaul on 2007-07-27
> **garionw said:**
> I'm from Internode (also Tasmania, Australia)



Wow, small world. Where abouts are you in Tassie????

---

### Post by garionw on 2007-07-27
Burnie - Mine works now, I just needed to update ubuntu

Thanks for the help

---

### Post by bikeboy on 2007-07-27
Hmmm I expected to see some au.archive.ubuntu.com, but none of you have that. Just so you know, au.archive.ubuntu.com (hosted on Optus's network) went down a few days ago and probably isn't fixed yet.

Anyway, it's unlikely but you can try another Aussie mirror to see if that works. Internode have one that will be free traffic for their customers, but I'm not sure of the address.

There's also [ftp://mirror.pacific.net.au/linux/ubuntu](ftp://mirror.pacific.net.au/linux/ubuntu) which is free traffic to anyone on PIPE. To try out an alternative mirror, backup the file ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.original
```
Then replace the current address with another mirror using gedit
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by garionw on 2007-07-27
Yeah, I just found it now - It was commented out

To change to the mirror you suggested, do I just replace the address with the one you provided?

---

### Post by bikeboy on 2007-07-27
Yes, just the replace the [http://archive.ubuntu.com](http://archive.ubuntu.com) [ftp://mirror.pacific.net.au/linux/ubuntu](ftp://mirror.pacific.net.au/linux/ubuntu), the rest stays the same.

---

### Post by jrtpaul on 2007-07-27
For anyone who is iterested, updating  Ubuntu fixed my problem.

---

