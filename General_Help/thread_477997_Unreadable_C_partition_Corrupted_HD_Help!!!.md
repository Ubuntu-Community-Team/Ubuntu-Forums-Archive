---
title: "Unreadable C partition? Corrupted HD? Help!!!"
date: 2007-06-18
forum: General Help
---

### Post by Fireblend on 2007-06-18
So, my brother has been playing with this computer lately (dual boots Windows and Ubuntu with Wubi) and it seems there's something weird going on. It was going all fine and now it won't boot. Well, it gets to the grub menu and it doesn't matter what you choose, it restarts the computer and the cycle starts again.

Now, there's been a virus going on that was starting to bother me, I can't remember exactly its name, but it was something along the lines of Rotorok or something like that and whenever the antivirus detected it, it was a boot.exe file, so my first thought was that it was related to this issue. If you ask why I hadn't killed the virus before, it's because I found out about me having it this afternoon when I connected it to a computer of a friend of mine and it got detected.

Now, I'm using the ubuntu live cd and mounted the partition, but whenever I click on it, I get a "Can't show contents" message and right clicking -> properties show me it's "unreadable". Is the HD corrupted? What are my options here? It was just fine a few minutes ago. I'd really appreciate any help. I'm backuping all my other data into my ubuntu-only computer as a backup plan but it would still be nice to save this computer.

Thanks.

---

### Post by Fireblend on 2007-06-18
Bump, I _*really*_ need help.

---

### Post by joe.turion64x2 on 2007-06-18
When you mount something using the liveCD only the root user can access it. Try typing ***sudo nautilus*** and browse to your partition.

Joe.

---

### Post by Fireblend on 2007-06-18
Yup that's exactly what I did.

---

### Post by joe.turion64x2 on 2007-06-18
Did it work then?

Last week I backed up 40GB of data in a Windows box, the problem was that since my external USB drive is ext3 I needed to boot from a Ubuntu Live CD to perform the task. I mounted the partition and when I 'normally' opened Nautilus and tried to access the files got the same messages as you did (only with sudo nautilus I could access them). I think that if the partition were corrupted, it shouldn't have been mounted in the first place.

Joe.

---

### Post by Fireblend on 2007-06-19
No, it didn't. I meant I'm aware that I have to browse it with Nautilus. The error message wasn't about not having permission but about not being able to show the contents.

---

### Post by merlinus on 2007-06-19
You might try systemrescue cd:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

-merlin

---

### Post by joe.turion64x2 on 2007-06-19
Ok, I asume you are doing **sudo nautilus** (as superuser), have in mind that when you don't have permissions to access some files they cannot be displayed (I mean, I have seen those 'error messages' in the same context).

---

### Post by Fireblend on 2007-06-19
> **merlinus said:**
> You might try systemrescue cd:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

-merlin

Yeah, I'm gonna definitely try that out...

> **joe.turion64x2 said:**
> Ok, I asume you are doing **sudo nautilus**.

Yes, as I said, it's not a permissions issue.

---

### Post by joe.turion64x2 on 2007-06-19
> **Fireblend said:**
> Yeah, I'm gonna definitely try that out...



Yes, as I said, it's not a permissions issue.
Very well then. In that case I can not imagine what is happening there, provided you did not get error messages while mounting the partition, did you?

What does Gnome Partition Editor say about the partition? Does it appear mounted there?

Joe.

---

### Post by Fireblend on 2007-06-19
I didn't receive any error message, and GParted is showing the partition just fine, seems to have all the data intact.

---

### Post by joe.turion64x2 on 2007-06-19
Ok, so keep trying, at least you know your data is not lost.

Joe.

---

