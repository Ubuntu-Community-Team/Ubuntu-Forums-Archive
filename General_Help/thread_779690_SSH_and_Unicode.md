---
title: "SSH and Unicode"
date: 2008-05-02
forum: General Help
---

### Post by julzKB on 2008-05-02
Hello,

I have got a little unicode issue here, I hope someone will be able to help .

I've got an external drive formated in FAT 32 mounted with those options in fstab :

```

defaults,utf8,umask=0000 0 1

```

All is fine, interactively in Nautilus I can see my "é" characters, in the Terminal, same thing all the characters with accents are fine .

Now, the problem appears when I login remotely via ssh on my mac.The terminal on the OSX machine is fine, it can read accents without a problem so I basically think that the problem lies on the Ubuntu box not translating Unicode correctly via SSH ..

Any idea ??


I hope it all makes sense ..

---

