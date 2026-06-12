---
title: "Accessing windows files on same hard drive (8.04)"
date: 2008-04-29
forum: General Help
---

### Post by mistersam on 2008-04-29
I just installed 8.04 (which I believe is a great improvement over 7.04 as many many more things work right out of the box) using Wubi (same hard drive, no partition). Now I would like to access my Windows folders but I don't know where to begin.

On 7.04 (partitioned), all I had to do was \dev\hda and there it was. But not anymore. Any ideas?

---

### Post by Monicker on 2008-04-29
The Windows partition should be listed under Places

---

### Post by mistersam on 2008-04-29
Thanks for the prompt reply. I do not see it there. I have:

Home Folder
Desktop
Documents
Music 
Pictures
Videos
--
Computer
CD/DVD Creator
--
Network
Connect to Server
--
Serch for Files
Recent Documents

---

### Post by azizzle on 2008-04-29
I'm having the exact same issue. Are we supposed to mount the windows drive or something? With gutsy it was already there?:confused:

---

### Post by azizzle on 2008-04-29
I think I've found the problem. Since we installed with wubi, and inside the windows partition, windows isn't going to be called windows or separate drive. The windows files should be accessible under /host.

---

### Post by mistersam on 2008-04-29
Yep, that's where they are. Thanks!

---

### Post by mistersam on 2008-06-14
I've since made my Ubuntu virtual disk bigger and I cannot find the host folder anymore. any ideas?

---

