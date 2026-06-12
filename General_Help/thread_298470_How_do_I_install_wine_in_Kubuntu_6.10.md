---
title: "How do I install wine in Kubuntu 6.10?"
date: 2006-11-12
forum: General Help
---

### Post by yurtfg89327tfg0o on 2006-11-12
My sources list is

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse restricted 
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe 

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted 

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe 

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 

I dont see wine in adept

'sudo aptitude install wine' does not work either.
Please help

Matt

---

### Post by pdub on 2006-11-12
I followed this guide when installing Edgy and wine installed for me using their sources.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

I did add this to my sources.list though

# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by yurtfg89327tfg0o on 2006-11-12
Thanks.
Unfortunately I get this

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

I guess maybe a deb for AMD64 doesn't exist yet.

---

### Post by pdub on 2006-11-12
Probably not.

I ran 64 bit for a while and then gave up. It was no faster and finding repo's was a pain.

---

### Post by yurtfg89327tfg0o on 2006-11-14
Well while trying once again somehow I lost my home dir. Very bad.
I'll play safe and go with edgy i386 (or safer yet and 6.06 i386).
It's so frustrating to have 64-bit CPU's 'forced' upon us ahead of their time. I doubt 99.99% of users need 64-bit software.

---

### Post by klokwyze on 2006-11-15
Yeah,](*,)  I cant install Wine in Kubuntu 6.10 either... I am getting the feeling I should have installed 6.06 instead, but noone really told me that. 

Why release 6.10 as a full release, but not support it like 6.06? Why is a newer release seemingly more unstable? not very logical....

Why is this such a challenge to just install a program? If its just a few lines of code that need to be input, why can't I find these lines?

If anyone can help me figure out how to install Wine or any other windows compatibility layer, I would really appreciate it.](*,)

---

### Post by klokwyze on 2006-11-16
Does anyone know?

I have done searches everywhere and posted @ multiple forums... 

any help is appreciated.... :neutral:

---

### Post by ser1alsn1per on 2006-11-16
hi its easy install automatix it has wine as an option to install very easy

---

### Post by yurtfg89327tfg0o on 2006-11-16
FWIW I ditched 6.10 and went back to 6.06 i386.
How many really need 64-bit anyway? Maybe there's a difference on some very niche tasks, but for the 'average' user its not worth it.
As for 6.10 being a 'full release' I think that's debatable. Theres a thread somewhere on these forums about it. 6.06 is the stable version with long-term support. Edgy seems too much like a release to keep the 'bleeding edge' crowd happy. Some say it works fine, but there are well know problems.
Mind you, even dapper on 64-bit has its share of troubles with things like codecs.
Don't forget that wine doesn't have an official 64-bit version yet.

---

### Post by ferochera on 2006-11-16
Try 

[I]#Wine
deb [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) edgy main[/I]

in your sources.list ;) .

But, does anybody know how to configure the serial ports? All I've read is about *wine.conf* but there's no one in my installation:-k .

Thanks.

---

### Post by Nameless_one on 2006-11-16
Have you tried this?

[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

---

