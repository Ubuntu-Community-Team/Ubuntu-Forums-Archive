---
title: "Hard-linked directories! How is it possible and how do I fix it?"
date: 2017-09-06
forum: General Help
---

### Post by bilkay on 2017-09-06
Never mind! The directories aren't hard-linked, /dev/sda1 was mounted on /mnt as well as /. Sorry for being stupid.

p.s. According to some websites I checked, hard-linking directories is sometimes possible by root. I couldn't find anything about unlinking them

I just discovered that my /mnt directory is the same as my root directory and they're not duplicates. The commands `$ ls -ild /` and `$ ls -ild /mnt` yield the same inode number. I have no idea how this is possible or how this happened because trying to hard-link directories always results in an error. I haven't tried `$ rmdir /mnt` because if ln can't hard-link directories, I don't see rmdir unlinking them. Any thoughts appreciated!

---

### Post by The Cog on 2017-09-06
I wonder if the root partition is also mounted at /mnt, rather than being hard linked. The command **mount** should list all mount points. Try **mount | grep /dev/sd** to pick out just disk mounts. Or just **sudo umount /mnt** and see if it complains.

---

### Post by bilkay on 2017-09-06
> **The Cog said:**
> I wonder if the root partition is also mounted at /mnt, rather than being hard linked. The command **mount** should list all mount points. Try **mount | grep /dev/sd** to pick out just disk mounts. Or just **sudo umount /mnt** and see if it complains.

Stupid me! I should have checked /etc/mtab first. What threw me was both having the same inode number. After unmounting /mnt, `ls -ild /mnt` gave a much different inode number.

Thanks for responding.

---

### Post by bilkay on 2017-09-06
What makes this really stupid is that I mounted /mnt myself - and forgot I'd done it. Getting old is a bitch. I've been told that memory is the second thing to go and I'll be damned if I remember what the first was.

---

### Post by The Cog on 2017-09-06
Great. It feels good when a guess turns out right like that.

---

