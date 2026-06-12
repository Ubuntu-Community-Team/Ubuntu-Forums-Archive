---
title: "Problems with Ubuntu partition and maybe HDD"
date: 2017-02-06
forum: General Help
---

### Post by hernandeza on 2017-02-06
Hello to everyone,

I have an ASUS laptop. It is exactly this one: [https://www.cnet.com/products/asus-k55vm-sx090v-15-6-core-i7-3610qm-8-gb-ram-500-gb-hdd/specs/](https://www.cnet.com/products/asus-k55vm-sx090v-15-6-core-i7-3610qm-8-gb-ram-500-gb-hdd/specs/) (ASUS K55 VM). Since a couple of years, I have had Ubuntu 14.04 and Windows 7 in the same HDD and it all worked really well and fast. A couple of weeks ago, the laptop started to work really slow and, after that, Ubuntu (where all my personal information is stored) would not login anymore. However, Windows still runs perfect. I think I the HDD is damaged (below I say why). All the information I have gathered is the following:

I have an aprox 300GB partition with Ubuntu installed and another one with Windows 7 (aprox 80GB). GRUB works as it allows me choose the desired SO. However, if I choose Windows, everything works but, if I choose Ubuntu, apart from loading the SO really slow, when I get to the login screen, I write my username and password and then nothing happens. If I press CTRL+ALT+F1 to run the terminal, this shows up:

[IMG]http://imgur.com/6DGQwtP.jpg[/IMG]

It clearly says that there are some error in some sectors of the HDD and it does not allow me to execute commands. If I boot my computer and go into advanced options for Ubuntu and choose recovery mode, the following screen appears:

[IMG]http://imgur.com/i9E5vNp.jpg[/IMG]

I have both executed dpkg and fsck. Dpkg ends up with:

[IMG]http://imgur.com/G4eFbl2.jpg[/IMG]

So, in the end, no packages are installed, right?

On the other hand, executing fsck ends up in:

[IMG]http://imgur.com/IY1jT6s.jpg[/IMG]

I have also tried to use an Ubuntu LiveCD to try to rescue files from the Ubuntu system, and also use the Windows (with ext2 readers) to try to rescue files. 

The case regarding the live CD gives me this error:

[IMG]http://imgur.com/cBLDwjM.jpg[/IMG]

Which is the same error as trying to carry out the extraction graphically:

[IMG]http://i.imgur.com/SOC29rP.jpg[/IMG]

From windows, with Ext2/4 readers... some files can be retrieved but not all of them (I supossed the damaged ones). The question is, I need to retrieve as much information from Ubuntu as possible, does anyone know how?

Sorry for my English, I have tried to describe the situation as accurate as possible, but if you need anything else to know about to help me, just say it.

Thank you very much

---

