---
title: "Is this possible?"
date: 2008-03-03
forum: General Help
---

### Post by Kris001 on 2008-03-03
Hi everyone,
I wondered if this is possible and how:

I have 2 computers at home. I have installed Kubuntu at one pc on my external hard drive. Everything works fine there. But now, my brother always is on that pc. Now, I want to plug in my external hard drive on the other pc and use that installed Linux on the other pc. Is that possible? It's difficult to install everything again(I live in Belgium, and we have data limit here:( )

Thanks in advance, Kris

---

### Post by jken146 on 2008-03-03
How easy it is depends on how you currently boot to your external hard drive, i.e. where GRUB is on the 
drives.  It should be possible though.

---

### Post by Kris001 on 2008-03-04
Grub is on the hard drive of that computer ;)
My root and home partitions are on the external hard drive.

---

### Post by Kris001 on 2008-03-04
So if I install Grub on the other pc, Kubuntu will work?

---

### Post by Kris001 on 2008-03-04
Anyone?

---

### Post by Whiffle on 2008-03-04
It could work.  I assume it has windows on it?  I think what you could do is setup the windows bootloader to boot the external hard drive, similar to this:

[http://ubuntuforums.org/showpost.php?p=2240168&postcount=2](http://ubuntuforums.org/showpost.php?p=2240168&postcount=2)


You'll have to get grub on your external hard drive though.

---

### Post by Kris001 on 2008-03-04
Thanks :)
I had some problems when I started linux, it couldn't boot, because the external hard drive wasn't mounted yet. I had to install the /boot partition on the computer's drive. 

Does this matter?

---

### Post by Kris001 on 2008-03-04
I just found out about **Smart Boot Manager**, maybe this will work too? :)

---

### Post by Kris001 on 2008-03-07
Anyone, please?:)

---

