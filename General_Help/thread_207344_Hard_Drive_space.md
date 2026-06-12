---
title: "Hard Drive space"
date: 2006-07-01
forum: General Help
---

### Post by Firecub on 2006-07-01
Hi Guys,
My Hard drive looks like this:

Windows: 20 G (50% Free)
Unix /Ubunbu: 7 G (10 % Free)
Swap: 1 G
Windows + Unix combined share area = 12 G (80% Free)

Total = 40 G

NOW.... . This is my first time playing with Unix so I am installing applications like a mad man just to see what they do. Thus now I have almost filled up my 7 Gs of Unix space! Can I and How will I increase the size of my Unix partition? I really don't want to reinstall everything from scratch.
Many thanks

---

### Post by halfvolle melk on 2006-07-01
Hi,
You can adjust your partitions with gParted which is on the live cd.
[http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted](http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted)
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

Note: I don't know how a Windows partition likes to be shrunk, you may bork it. Maybe defragging it first is a good idea but I wouldn't know.

1GB [edit]swap[/edit] is a bit much I think. Maybe you can shave some of of that.

---

### Post by greenbmw530i on 2006-07-01
I have resized (more specifically, shrunk) my Windows partition several times to make room for my ever-growing Ubuntu partition with no problems with Windows or Ubuntu whatsoever.

Happy resizing!

---

