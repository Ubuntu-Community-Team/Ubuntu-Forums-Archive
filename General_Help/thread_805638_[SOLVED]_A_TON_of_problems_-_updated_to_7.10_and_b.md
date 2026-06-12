---
title: "[SOLVED] A TON of problems - updated to 7.10 and broke my Nvidia + Netowrk drivers -"
date: 2008-05-24
forum: General Help
---

### Post by Beatbreaker on 2008-05-24
Hi, I recently updated from Fiesty Faun to 7.10

it busted my Nvidia drivers, so i've been stuck in the terminal since. Now when i've tried to fix the drives i've found that my wired internet connection is busted in the terminal too.

i was told to do  
```

ping google.com
```

and i couldn't get any responses from a server

i was then told to edit /etc/network/interfaces and add...

```
audo eth0 
iface eth0 iten dhcp
```

then to type the command

```
sudo ifup eth0
```

but i got the following error message

```
/etc/network/interfaces:20:duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

any help would be most appreciated!!!

---

### Post by Beatbreaker on 2008-05-26
Resolved - I decided not bother trying to fix the broken update and installed Hardy over the top instead. I gotta say i'm VERY impressed. I was worried but i tested the hardest things and they all work now, my web cam - Perfect. My printer, worked after plugging it in. It was TOO easy!!!

Great work guys!

---

