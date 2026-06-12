---
title: "Installing XP over Ubuntu"
date: 2008-03-31
forum: General Help
---

### Post by waterskill on 2008-03-31
Is there a way to install XP over Ubuntu when I used ALL my partitions for Ubuntu?

---

### Post by nickoli_02 on 2008-03-31
What do you mean, used ALL partitions? If you have multiple partitions (ie. one for Ubuntu OS, another for media files) you can install XP on another partition. You will then need to reinstall the GRUB boot loader to the MBR since XP will put its own boot loader there that doesn't care about other OS's. 

If you only have one partition then you should be able to resize your Ubuntu partition and create a new one for XP. Or, you can buy another hard drive for XP. In any case, yes it is possible but a little more work because you need to reinstall and configure GRUB from XP.

---

### Post by NightwishFan on 2008-03-31
Blasphemy!
Well I say the best option is to resize partition for XP, assuming you wish to keep Ubuntu.

---

### Post by waterskill on 2008-03-31
> **nickoli_02 said:**
> What do you mean, used ALL partitions? If you have multiple partitions (ie. one for Ubuntu OS, another for media files) you can install XP on another partition. You will then need to reinstall the GRUB boot loader to the MBR since XP will put its own boot loader there that doesn't care about other OS's. 

If you only have one partition then you should be able to resize your Ubuntu partition and create a new one for XP. Or, you can buy another hard drive for XP. In any case, yes it is possible but a little more work because you need to reinstall and configure GRUB from XP.
> Blasphemy!
Well I say the best option is to resize partition for XP, assuming you wish to keep Ubuntu.

So how do I resize my partition? I'm a noob at stuff like that, I mean I don't have much experience with it. :/
And by all the partitions a I mean that when I entered the setup for Ubuntu it asked me if I wanted to use all the partitions or only 2 and I chose all.(Coulda been 4 or 2 but I'm not sure x.x)

---

### Post by NightwishFan on 2008-03-31
Put the Ubuntu live cd in and use the partition editor its all gravy from there on.

---

