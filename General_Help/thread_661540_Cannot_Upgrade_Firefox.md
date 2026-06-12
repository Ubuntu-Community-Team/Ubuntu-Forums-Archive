---
title: "Cannot Upgrade Firefox"
date: 2008-01-08
forum: General Help
---

### Post by richfaraone on 2008-01-08
Hi Everyone,

I'll start off my very first post here :) by saying that I have tinkered with Linux in some form or another for about 2 years now, never really seriously, until last week when I pulled out an old Ubuntu CD I got off eBay for about $2 last year and decided to install it on an old server I had laying around collecting dust. After only a week, I have it up and running (really in 10 minutes), installed Apache, perl, mySQL, FTP server, etc., and actually transfered my first website to it and got my first php forum up and running on the Internet! I'm hooked to say the least!

Well, I have really done a lot of research to get all these things installed and organized, especially since I have limited to no knowledge of what I'm doing! :) So this question really make me feel stupid asking it, but here goes anyway.

I am trying to upgrade Firefox to the latest v2, and I have gone there, downloaded it, and the instructions really have me confused. So after a little research, I found the great little "Add and remove Progs" In the system and figured, DUH! But no, when I choose update from there, the latest version I can get is 1.5.0.15pre.

Can anyone explain in plain English how I can get the v2 Firefox? Or is Firefox even the best browser for Linux? I guess I use it because I have used it for so long and I'm used to it..

Any advise would be greatly appreciated!
*Sorry for being so long winded! I type as if I were talking!*

Best regards, and thank you in advance!

-Rich

---

### Post by p_quarles on 2008-01-08
It sounds like you have an older version of Ubuntu installed. You can get the exact version name and number by running the following command in a terminal:
```
lsb_release -a
```
Post the output here if you need any help interpeting it.

---

### Post by nowshining on 2008-01-08
have u tried the ubuntuzilla script?

---

### Post by richfaraone on 2008-01-08
Wow, that was fast!

Okay, here's what I get:
Ubuntu 6.06.1 LTS
Release 6.06
Codename: dapper


Thanks,

-Rich

---

### Post by richfaraone on 2008-01-08
ubuntuzilla? I'm really new to this. I have no idea what this means. Is this an upgrade?

Thanks,

-Rich

---

### Post by richfaraone on 2008-01-08
Okay I just looked it up, and the download page has versions for i386 and amd64. My termal says I have i686?

---

### Post by richfaraone on 2008-01-08
I tried to download it and I get the error:
error: Dependency is not satisfiable: libnotify-bin

---

### Post by p_quarles on 2008-01-08
> **richfaraone said:**
> Okay I just looked it up, and the download page has versions for i386 and amd64. My termal says I have i686?
Post the output of the following command; that'll tell me which version you need to install:
```
uname -a
```

---

### Post by richfaraone on 2008-01-08
Linux rich-desktop 2.6.15-29-386 #1 PREEMPT Mon Sep 24 17:18:25 UTC 2007 i686 GNU/Linux

I tried downloading the libnotify-bin with the dependancy error, so I downloaded the libc6 dependancy, yet another error, and downloaded the next dependancy locals-bin with a final error!

I think I might blow this thing up before long :)

Thanks!

---

### Post by richfaraone on 2008-01-08
Hey All, Thanks for all the quick replies... but I have to up for work in 3 hours, so I'll check back here again tomorrow.


Thanks again!

-Rich

---

### Post by zvacet on 2008-01-08
Do you have all repositories open?Look [this](https://help.ubuntu.com/community/Repositories/Ubuntu) and you will know what to do.After that install libnotify-bin in synaptic or 

```
sudo apt-get install libnotify-bin
```

---

### Post by nowshining on 2008-01-08
6.06 is still updated and has an available repo, u can order DVDs of all the software :) i forgot where, canonical store I think - ubuntu.com, but it's supported with sercurity updates and bug fixes for the desktop until June 2009 of which is TWO whole months after Gutsy Gibbon (the on I use) becomes unsupported. hehe

:D

after which date(s) the repos for Gutsy and Dapper will disappear into oblivion :P

---

### Post by richfaraone on 2008-01-09
Okay guys, here's the trick that did it for me. I went to the Ubuntu website, downloaded the iso for v7, burned it to disk, restarted my computer and 45 minutes later... **viola!** Problem solved.

I have my old Firefox back with the custom theme as well as the newer O/S, and I'm good to go!

Thanks to all you good folks for the help...

Now it's off to read some good articles for beginners, and I'm kissin' *Winblows* goodbye forever! I love this O/S!

Thanks again!


-Rich

---

### Post by nowshining on 2008-01-09
lolz ur welcome, :)

I switched to swiftfox by the way,

getswiftfox.com

:)

---

### Post by misfitpierce on 2008-01-09
Firefox is not just the best browser for linux... Its the best browser on any OS... ever! lol :)

---

### Post by nowshining on 2008-01-09
> **misfitpierce said:**
> Firefox is not just the best browser for linux... Its the best browser on any OS... ever! lol :)
hehe :P

---

