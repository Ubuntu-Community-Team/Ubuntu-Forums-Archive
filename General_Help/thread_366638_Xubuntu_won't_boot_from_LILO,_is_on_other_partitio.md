---
title: "Xubuntu won't boot from LILO, is on other partition"
date: 2007-02-21
forum: General Help
---

### Post by pix2iii on 2007-02-21
Hi, I just registered right now.

My computer is Pentium III / 500 Mhz, my main operating system is Windows XP but even if I practically know nothing about computers except just everyday stuff, I wanted to try Linux a bit.

I have a fairly messy harddrive(s). Two harddrives which both are partitioned. This is perhaps part of my problem.

My computer boots using LILO, which was installed together with another Linux (Feather Linux). My computer is messy, and the LILO is the only way to boot Windows; without LILO I get an error (NTLOADER IS MISSING), so I wish to keep the LILO.

Before I installed Feather Linux to get LILO (back), I had installed Xubuntu, so Xubuntu is already installed. Grub, which got installed together with my Xubuntu installation allowed me to boot Xubuntu, but unlike LILO it turned out it didn't let me get into Windows -- which is why I installed Feather again (Feather had been there before I installed Xubuntu.) The Feather install is a re-install, just replacing an earlier Feather install that was (probably) messed up (I mess up my Feather on a regular basis, unfortunately).

To get to the point, Xubuntu is not on the root partition, and my problem is managing to configure LILO and set things up so I can boot into my Xubuntu install.

I did try and look for information on how to do this, but it's not easy it seems -- especially for someone who knows practically nothing about "all this". I copied some file from the Xubuntu partition, and pointed to that file from the LILO configuration file, this was supposed to let LILO boot Xubuntu according to the article I read, but I haven't been able to get it to work. Right now I have Xubuntu on my LILO menu, after Feather and Windows XP, but selecting Xubuntu doesn't boot Xubuntu (I get some error, perhaps "not a system disk").

I do not know what I am talking about, basically, but if anyone has some vague idea what I am trying to explain and can give me some clue, I would be very thankful since I liked using Xubuntu while it still was booting. I will try to give more information if it could be of use.

---> The only thing I want to change at this point is getting LILO to boot my Xubuntu install. This is not an urgent matter at all, just something I would like to get in order at some point.

Thank you very much for reading this.

I have attached my lilo.conf file (in pdf format).

Thanks in advance for any pointers or clues.

pix2iii

---

### Post by paparucino on 2007-02-21
> **pix2iii said:**
> 

Thanks in advance for any pointers or clues.

Are you sure your windows partition in on hbd1? usually XP is on C: which is hda1

---

### Post by pix2iii on 2007-02-21
paparucino,

Thank you for replying. Yes, my Windows is not where it usually would be, my computer has let's say a "long and complicated history". LILO does boot both Feather and Windows.

pix2iii

---

