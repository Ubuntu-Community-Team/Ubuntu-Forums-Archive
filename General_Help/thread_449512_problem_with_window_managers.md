---
title: "problem with window managers"
date: 2007-05-20
forum: General Help
---

### Post by Naegling23 on 2007-05-20
I use beryl, but turn it off when I launch games with the command kwin --replace in a script.  Recently, after playing around with my monitor settings (I had to replace my xorg.conf backup file after I messed things around too much) the command stopped working.  I am left with:

naegling23@naegling23-kubuntu:~$ kwin --replace
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kwin: Fatal IO error: client killed

I can still toggle beryl/kwin using the beryl manager, but I cannot use the terminal commands to toggle the two of them anymore....does anyone know what is going on, or how to fix this?

---

### Post by Naegling23 on 2007-05-21
I've tried resetting my xorg.conf file to the old one, but the problem still exists.  Any thoughts?

---

### Post by Naegling23 on 2007-05-21
Ok, so I'm plowing through the forums trying to find a solution, unfortunatly, I am at work and cannot trouble shoot anything.  I stumbled upon this command

kwin --replace --config ~/.kde/share/config/kwinrc

I dont know what that does.  Will this help me?

---

### Post by Naegling23 on 2007-05-21
bump

---

### Post by Naegling23 on 2007-05-21
Nobody even has an idea????

I have tried removing and reinstalling kwin, no luck

I have tried logging in as a different user, but the problem is still there.  This makes me think it must be a system issue rather than a custom setting issue.

Whats driving me nuts is that I replaced my xorg.conf with a much older version...one that previously worked, and now that one doesnt.

So its not any settings that would be in my /home folder, and its not xorg.conf.  What can this even be??

---

