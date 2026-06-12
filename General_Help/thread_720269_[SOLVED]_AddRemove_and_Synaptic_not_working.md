---
title: "[SOLVED] Add/Remove and Synaptic not working"
date: 2008-03-10
forum: General Help
---

### Post by marxman47 on 2008-03-10
Hi everyone - I've been happily using Gutsy since December and everything has gone so well that I've almost forgotten that I'm using a system other than Windows - which is quite an achievement for me, having been a MS thrall for so long.

However - an update went haywire last night - I was try to get the MS Core Fonts - and the Add/Remove and Synaptic are no longer working.

I have a message saying that I must manually run 'dpkg --configure -a' but when I try to do this in 'Run', nothing happens and the message reappears when I open Add/Remove or Synaptic.

Can anyone help out a Windows dummy who is a wee bit wary of the command line?

Thanks in anticipation. marxman47.

---

### Post by kesman on 2008-03-10
open terminal and run
```

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by marxman47 on 2008-03-10
Thank you very much, Kesman, for coming to my aid!  I ran the lines you gave me and the MS fonts installed properly AND the Add/Remove is working again.

Again, many thanks - this is a great place for people like me :) !

marxman47

---

