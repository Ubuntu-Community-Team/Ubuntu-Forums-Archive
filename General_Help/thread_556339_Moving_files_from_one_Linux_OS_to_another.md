---
title: "Moving files from one Linux OS to another?"
date: 2007-09-21
forum: General Help
---

### Post by Ederico on 2007-09-21
*Hello,*

On my laptop I a multi-boot scenario with three OS, Windows XP Professional and two different Ubuntu OS. What I would like to do is eliminate one of the Ubuntu OSs, without losing my documents and multimedia files stored there. I'm assuming that to do this all I need to do is merely to move the files in question or not?

Both partitions involved are ext3, and the OSs are both based on Feisty Fawn (one is Ubuntu Christian Edition and the other is Ubuntu Ultimate Gamers Edition).

I hope someone can tell me if what I am presuming is correct, and what and if potential data loss risks are involved.

[I]Best Regards,
Ederico.[/I]

---

### Post by chuckyp on 2007-09-21
All you need to do is copy the files from your /home directory.

This is why users should set up a seperate /home partition then you could have used the same /home partition for Christian Edition and Ultimate Games.  I have a seperate /home on my drive makes switching distros very easy.  All of my settings and documents are saved.  For directions on creating a seperate /hom after you get rid of one of the ubuntus follow this guide:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Ederico on 2007-09-21
Thanks a lot, really helpful, and you gave me an idea to setup a more efficient system. :)

---

### Post by tgalati4 on 2007-09-21
Of course, if you get rid of the Christian edition, you will have to answer to a higher source!

---

### Post by Judgegeo on 2007-09-21
I couldn't stop laughing @ Ubuntu Christian Edition. No disrespect to Christains, but you just don't seem to understand what Christianity is about..

---

### Post by Lord Illidan on 2007-09-21
These two posts above me have no relation to the problem at hand. Either keep your opinions about Ubuntu CE to yourself or else addess them in the backyard.

---

### Post by Ederico on 2007-10-18
> **chuckyp said:**
> All you need to do is copy the files from your /home directory.

This is why users should set up a seperate /home partition then you could have used the same /home partition for Christian Edition and Ultimate Games.  I have a seperate /home on my drive makes switching distros very easy.  All of my settings and documents are saved.  For directions on creating a seperate /hom after you get rid of one of the ubuntus follow this guide:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I'm having a problem, my Linux partitions are not in /dev/. I ran GParted to check where they are, and they are found in GParted, however when I boot into Ubuntu the partitions aren't there. I cannot proceed further with the instructions given in the link as when I type the commands with the partition locations as provided by GParted I get a notice saying that the partition/location doesn't exist.

---

### Post by Ederico on 2007-10-18
> **Ederico said:**
> I'm having a problem, my Linux partitions are not in /dev/. I ran GParted to check where they are, and they are found in GParted, however when I boot into Ubuntu the partitions aren't there. I cannot proceed further with the instructions given in the link as when I type the commands with the partition locations as provided by GParted I get a notice saying that the partition/location doesn't exist.

Sorry about this, I had mistyped the locations from GParted, oops. :D

Still, the devices are not shown in /dev/ anyways.

---

