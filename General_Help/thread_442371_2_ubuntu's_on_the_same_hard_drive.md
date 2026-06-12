---
title: "2 ubuntu's on the same hard drive?"
date: 2007-05-13
forum: General Help
---

### Post by mills on 2007-05-13
is it possible to have 2 ubuntu installations on the same hard drive?

if it is possible then how would grub distinguish the 2?

yours ubuntuly
                            mills

EDIT: oh yeah and what about swap, would i need 2

---

### Post by tgm4883 on 2007-05-13
Yea its possible, you would just need different partitions for each.  And grub points to the correct partition for each entry.  You would have to manually rename each in grub to avoid having both just say Ubuntu

---

### Post by mills on 2007-05-13
just what i wanted to hear :)

but what about swap, iam guessing they will each have their own swap but just want to make sure

---

### Post by pekko on 2007-05-13
One swap is enough.

---

### Post by aldenhg on 2007-05-13
One swap will definitely be enough, just so long as you don't want to hibernate one of your Ubuntus and use the other one. IIRC, Linux uses the swap space to store all of the hibernation info, much like Windows' hiberfil.sys. It might be worth trying it out, but it also might do some damage.

---

### Post by floke on 2007-05-13
I can verify that having more than one ubuntu on a hard drive is fine. Grub will point to them by their partition (eg hda0,0; hda 0,1) so you haven't got to rename them. The newer install will also detect and use the swap file already on the drive, so they will share the swap space. Don't know about hibernation issues though, since it doesn't work for me anyway :)

---

### Post by tgm4883 on 2007-05-13
> **Steve.K said:**
> I can verify that having more than one ubuntu on a hard drive is fine. Grub will point to them by their partition (eg hda0,0; hda 0,1) so you haven't got to rename them. The newer install will also detect and use the swap file already on the drive, so they will share the swap space. Don't know about hibernation issues though, since it doesn't work for me anyway :)

Agreed, my comment about renaming it was for human use, not functionality.  The computer knows which is which, but it is only going to show Ubuntu (or something to that effect) in both grub entries.  So if you want to choose which one you want, it may help to make the human description more descriptive

---

### Post by floke on 2007-05-13
Ok, fair enough :popcorn:

---

