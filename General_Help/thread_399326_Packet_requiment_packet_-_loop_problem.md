---
title: "Packet requiment packet - loop problem"
date: 2007-04-02
forum: General Help
---

### Post by rvny on 2007-04-02
Hello!
I get packet's from pc, which connected to inetrnet. I give a *.pkg files from /var/apt/cashe
and save to disk
In my pc I copy this packets to similar folder.
I get a console, write
sudo su
password:)
dpkg -i name-of-packet1.pkg

My computer write name-of-packet1.pkg requiment name-of-packet2.pkg

I write
dpkg -i name-of-packet2.pkg
But this packet write:
name-of-packet2.pkg requiment name-of-packet1.pkg

How resolve this problem?
I can't install this 2 packet's, becouse they link's to each other. (Loop link's)

My computer not have internet and I need you help :) Thank you very much!!!

Renat

---

### Post by diepruis on 2007-04-02
Please try

```

dpkg -i package_1 package_2

```

---

