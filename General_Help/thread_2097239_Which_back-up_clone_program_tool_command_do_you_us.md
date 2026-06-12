---
title: "Which back-up clone program/ tool/ command do you use?"
date: 2012-12-22
forum: General Help
---

### Post by listerdl on 2012-12-22
Just wondering - 

I guess clonezilla is the obvious winner but is there another tool that you use and pefer?

I am looking for a solution to make a complete image backup of my machine so in case of any drama I can revert back to working time.

Thanks

---

### Post by sudodus on 2012-12-22
***Clonezilla*** is good for making images. I use it too.

But for my multimedia data partition, I use ***Unison*** (front-end to rsync), because it is not a good idea to compress what is already compressed, and it saves a lot of time to work incrementally with the large data amount.

---

### Post by blackbird34 on 2012-12-22
Never used Clonezilla myself, at the moment I do backups with Back In Time (another front-end to rsync) and I have an .iso of my system made with Remastersys. But I don't experiment much now anyway.

---

### Post by listerdl on 2012-12-22
> **blackbird34 said:**
> Never used Clonezilla myself, at the moment I do backups with Back In Time (another front-end to rsync) and I have an .iso of my system made with Remastersys. But I don't experiment much now anyway.

Whats the difference between those two? I get the impression that remasterys is a classic backup too and the .iso sounds really good.

Is it quite simple to use remasterys? Of course i can take a look but your feedback would be helpful.

What i am trying to achieve here is just a simple back-up of the entire system including a virtual machine which I have. Remasterys would do the job right?

Thanks

---

### Post by sudodus on 2012-12-22
I think remastersys will make an install iso file to make another system of your 'exact' flavour but without your personal files.

So you need to backup at least your home directory in some other way.

---

### Post by listerdl on 2012-12-22
> **sudodus said:**
> I think remastersys will make an install iso file to make another system of your 'exact' flavour but without your personal files.

So you need to backup at least your home directory in some other way.

Right. Thanks.

I think that clonezilla is my friend if I want to have a complete exact byte by byte copy? (I think!)

---

### Post by sudodus on 2012-12-22
Yes!

You can do it with several other tools, the simplest one is dd, nicknamed disk destroyer because it does what you tell it to do, not what you intend to do but fail to tell. And it does not ask.

Clonezilla is much friendlier, it skips empty parts of the partitions, and with the partclone tool it is very fast and works well also for ext4 file systems.

---

