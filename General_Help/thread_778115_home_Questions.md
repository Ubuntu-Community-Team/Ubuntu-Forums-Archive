---
title: "/home Questions"
date: 2008-05-01
forum: General Help
---

### Post by arseniy on 2008-05-01
1. Should I (or is it a good idea to) put /home on a different partition on my internal hard drive? I'm thinking yes, because it allows me to reinstall anything without losing my /home data. But that benefit is easily canceled because I have backups lol... Your ideas?

2. If I do that, can I encrypt that second partition, so that it's private, but still access it just as fast (like for listening to music, I'd have to open Amarok and read from that partition)? Does encryption slow it down?

3. When I first installed Ubuntu, I had lots and lots of free space. Then I copied around 30GB of music into my home folder from another drive, and all of a sudden I had used up 50 more GB than was free before I moved the music. 30 != 50 lol! Why did this happen? Could updates have taken so much space? Could I have accidentally copied it elsewhere too, so two copies of my music exist on my drive? And if that's the case, can I find that second copy somehow?

4. Does the Live CD have gparted? :)

Thanks!

---

### Post by RATM_Owns on 2008-05-01
1. Yes. If that gives you more space.

2. I think you could encrypt it. But I think it would slow /home/ down.

3. Updates shouldn't take that much space. Do a
sudo apt-get clean
and see if that helps. Also search for the music in your harddrive. 

4. The Ubuntu one? Yes. A lot better than the Gparted Live CD.

---

### Post by arseniy on 2008-05-01
So say I don't encrypt it. Will it still be slower than having /home on one main partition?

How can I have more space if I do that? Won't it just be the same amount of space?

---

