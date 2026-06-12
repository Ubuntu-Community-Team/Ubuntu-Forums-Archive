---
title: "Updating Intel Micro code - which file do I choose from this site?"
date: 2017-05-17
forum: General Help
---

### Post by dendrite2 on 2017-05-17
Hi all,

Enjoying Ubuntu 16.04.2 Mate (five year support 4.xx kernel, not 4.8 etc) after being on Mint for years. I love the look of 16.04 Mate and ease of use. 

This is the help site to install a later version of my intel microcode:

 [https://sites.google.com/site/easylinuxtipsproject/microcode](https://sites.google.com/site/easylinuxtipsproject/microcode)

This is the link from that site to get a newer microcode file than the current November 2015 one listed in Synaptic Package Manager. 

[http://ftp.us.debian.org/debian/pool/non-free/i/intel-microcode/](http://ftp.us.debian.org/debian/pool/non-free/i/intel-microcode/)

Question: I installed 16.04.1 so I can stay with the 4.xx kernel but just want to update my intel microcode to the latest version. Its pretty straight forward but I am unsure what file to select for my 64 bit Intel machine, a Core i5 6500 Skylake machine with 64 bit Ubuntu installed. 

So, which file for my machine? Pretty sure its this one: [intel-microcode_3.20170511.1_amd64.deb]("http://ftp.us.debian.org/debian/pool/non-free/i/intel-microcode/intel-microcode_3.20170511.1_amd64.deb")

[COLOR=#000000][/COLOR]Thanks for your help. :)

---

### Post by Xian on 2017-05-17
So you have 4 options:

intel-microcode_3.20170511.1.dsc
intel-microcode_3.20170511.1.tar.xz    
intel-microcode_3.20170511.1_amd64.deb     
intel-microcode_3.20170511.1_i386.deb

The first 2 deal (for the most part) with source files.
The last option is for 32bit architecture.

So yes -- intel-microcode_3.20170511.1_amd64.deb is your correct choice.

---

### Post by dendrite2 on 2017-05-18
Thank you. :)

---

