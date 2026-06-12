---
title: "Formatting USB Drive..."
date: 2007-07-23
forum: General Help
---

### Post by Lster on 2007-07-23
Hi

I'm sorry to ask what I imagine is a trivial question, I could not find my problem when searching.

Basically I have a USB flash drive that I want to backup some of my stuff on. It was formatted to be Fat32 so I wanted to reformat it as Ext2 or 3. I managed this successfully, but now I can;t write to the drive. The permissions appear to all be root (I was root when I formatted it, if that makes any difference?).

So how do I get it formatted so I can read and write to it?

Thanks in advance,
Lster

---

### Post by apjone on 2007-07-23
mount it and chown it.
```

sudo mount device path
sudo chown -R username path

```
That is what i did

---

### Post by Lster on 2007-07-23
Thanks for the hint.

All is working; but I have a small question. So I can rely less on the forum, what does chown do? Is that the command that changes privileges...?

Thanks again,
Lster

---

### Post by Bablefish on 2007-07-23
I took the cowards way out I format mine on my windows pc.

---

### Post by Lster on 2007-07-23
Lol. :)

---

### Post by stchman on 2007-07-23
> **Lster said:**
> Hi

I'm sorry to ask what I imagine is a trivial question, I could not find my problem when searching.

Basically I have a USB flash drive that I want to backup some of my stuff on. It was formatted to be Fat32 so I wanted to reformat it as Ext2 or 3. I managed this successfully, but now I can;t write to the drive. The permissions appear to all be root (I was root when I formatted it, if that makes any difference?).

So how do I get it formatted so I can read and write to it?

Thanks in advance,
Lster

I would leave the flash drive as FAT32 as pretty much any PC out there can read it.

---

### Post by benx009 on 2007-07-23
> **stchman said:**
> I would leave the flash drive as FAT32 as pretty much any PC out there can read it.

yeah, i formatted one of my flash drives as ext3 once, and it caused nothing but problems

---

### Post by apjone on 2007-07-24
> **Lster said:**
> Thanks for the hint.

All is working; but I have a small question. So I can rely less on the forum, what does chown do? Is that the command that changes privileges...?

Thanks again,
Lster

Yes, these guys are a good bunch of people who helped me allot when I first started. If your not sure what a command does then in a terminal run

man command

eg

man chown

and this will give you the manual for that command.

---

