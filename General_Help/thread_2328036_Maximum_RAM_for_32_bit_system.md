---
title: "Maximum RAM for 32 bit system"
date: 2016-06-16
forum: General Help
---

### Post by fbird3 on 2016-06-16
Hello, there.
I am runnning Ubuntu 10.04 32 bit version with an Intel Core Duo and 3 GB of RAM installed.
A while ago, I was advised not to add more memory to it [to make it 4 GB in total], because the O.S. would not be capable of using it [being a 32 bit version of the O.S. -- that's what I was informed then].
But recently I began digging a bit and now I am confused...: it seems that 32 bit systems can handle **up to [and including]** 4 GB of RAM -- but no more -- but that contradicts what I was told then; so I decided to come here to dispel my doubts.
Should I pay for the extra RAM, safe in the knowledge that my O.S. will benefit from it or should I not because, after all, Ubuntu 32 bit version will not 'see' more than 3 GB of RAM?
Thanking you in advance.

---

### Post by QIII on 2016-06-16
Hello!

Before you do anything, you should install a supported release of Ubuntu.  10.04 is long past its end of life.

Please see the [Ubuntu Forums Staff's position]("http://ubuntuforums.org/showthread.php?t=2229730") on EOL releases.

---

### Post by grahammechanical on 2016-06-16
The Intel Core 2 Duo is a 64 bit CPU. So, the CPU is capable of addressing much more than 4GB or memory. A 32 bit OS can address up to 4 GB of memory. A 32 bit CPU with Physical Address Extensions (PAE) and a 32 bit OS with PAE capability can address from 4 GB up to 64 GB of memory. 

[https://en.wikipedia.org/wiki/Physical_Address_Extension](https://en.wikipedia.org/wiki/Physical_Address_Extension)

Even if the 32 bit version of Ubuntu 10.04 that you are using was not PAE capable it should still make use of up to 4 GB of memory. I do think, but I cannot say for certain, that the standard 32 bit Ubuntu 10.04 OS was PAE capable. 

I do agree not only with the advice to use a supported version of Ubuntu but a 64 bit version at that. It is not easy to choose between spending money to upgrade a working but getting old machine or put the money towards more modern hardware. It is a difficult choice, indeed. I speak as someone with a Core 2 Duo and less than 3 GB of RAM.

Regards

---

### Post by Impavidus on 2016-06-16
Before we had PAE (physical address extension) 32 bit systems could access 4 GiB. Some of this was reserved for hardware addresses etc., so in practice this was limited to about 3 GiB. The last release of any Ubuntu flavour to support 32 bit non-pae was Xubuntu 12.04, which went end-of-life a little over one year ago.

With PAE a 32 bit operating system can access more than 4 GiB of memory, but each individual application is still limited to 4 GiB (minus what's reseved for hardware addresses etc., I think). So a 32 bit system can use 4GiB of ram and even more, but usage of that amount of ram is more flexible if you have a 64 bit system. If your CPU and motherboard support 64 bit (if it's not very old, it should), I suggest you install the 64 bit version of a supported Ubuntu flavour and upgrade your ram. But if you wish, you can also install 32 bit and still use 4 GiB ram, but in any case get a supported *buntu release. You can take a fresh install of 16.04 LTS as an opportunity to move to 64 bit. That's what I did when I installed 14.04 and at the same time upgraded my ram from 3 GiB to 8 GiB.

---

### Post by fbird3 on 2016-06-17
Thank you all, for the support.
I was willing to upgrade to 16.04, with a leaning to go all the way for  the 64 bit one [I have already downloaded both 32 and 64 bit  installation files]; alas, I found out that the maximum memory my laptop  can have is 4 GB -- no ifs, no buts...
So, seeing how I like my laptop and have no need for another one [just  to install the newer 16.04 version], and that this admitedly old Ubuntu  version [10.04] could be improved but it is still delivering the goods  for me, I have decided to keep the *status quo* and do nothing  more than, perhaps, installing the alluded version to a virtual machine  [particularly the 32 bit one, since I now know that this laptop will not  be much good as a 64 bit machine].
Once again, I am grateful for your suggestions.

---

### Post by Impavidus on 2016-06-17
There's no need to have more than 3 GiB of ram to install Ubuntu 16.04, 32 bit or 64 bit. With 3 GiB of ram a 64 bit system won't really perform better than a 32 bit system, but that shouldn't stop you from moving from 10.04 to 16.04. And a real install of 16.04 will perform better than 16.04 on a virtual machine on 10.04. For that, you memory is tight. It may be best to install a lighter flavour of Ubuntu though.

Installing 16.04 will give you security updates and newer versions of many applications, supporting many new features. 10.04 has not received updates since 2013 (except for the parts it had in common with server edition, which went end-of-life in 2015). Apart from security issues, I don't think that the old web browser in 10.04 still supports all features you find in modern websites. And your 6 year old version of LibreOffice may have difficulty properly displaying documents coming from more recent office programs.

Once again, there is no need to buy a new laptop to be able to run 16.04.

---

### Post by gordintoronto on 2016-06-17
It is unlikely that you would notice any difference by going from 3 GB of RAM to 4 GB, unless you edit videos or run other programs which use a lot of memory. (30 tabs in Chrome would do it.)

But installing 16.04 would be an important upgrade, perhaps Xubuntu 16.04. (Or Lubuntu or Ubuntu Mate.)

---

