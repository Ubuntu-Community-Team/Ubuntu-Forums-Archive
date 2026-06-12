---
title: "Dual boot share help?"
date: 2007-05-21
forum: General Help
---

### Post by Maniac Matt on 2007-05-21
How do you share files (like music) between OS's in a dual boot?

I have a Fat32 Partition. if that means anything.

I have windows xp installed and am planning on putting on Dapper of Feisty.

-matthew

---

### Post by bobplano on 2007-05-21
if you want to use that partition it makes things easier. you just put whatever you want to share on it and both Oses can read it. you could also install drivers so windows could read from ubuntu or vice versa but that is slightly more complex

---

### Post by greenstar on 2007-05-21
In your case, probably nothing more than mount the Fat32 partition RW. If it were *my* system, I'd have at least 5 partitions spread over my hard disk(s).

1. Windows OS
2. Ubuntu OS
3. Swap
4. Ubuntu's /home
5 Shared Fat32 partition


Mount the Fat32 RW in both OS's to have a "pass-thru" partition for sharing.

Greenstar

---

### Post by Maniac Matt on 2007-05-21
Im not sure exactly what you mean, because i am horrible with computers :).. but this is my mine looks like.


1. Windows OS
2.Kubuntu OS
3. Linux-swap
4.Fat32

is this good or bad?

---

### Post by greenstar on 2007-05-21
> **Maniac Matt said:**
> Im not sure exactly what you mean, because i am horrible with computers :).. but this is my mine looks like.


1. Windows OS
2.Kubuntu OS
3. Linux-swap
4.Fat32

is this good or bad?

That will do just fine. The question of good or bad is irrelevant; it's functional and that's what we're really after. Good luck.

Greenstar

---

