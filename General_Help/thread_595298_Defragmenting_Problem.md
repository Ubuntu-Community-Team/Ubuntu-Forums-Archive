---
title: "Defragmenting Problem"
date: 2007-10-28
forum: General Help
---

### Post by SGorilla on 2007-10-28
I've decided to try linux again, with the new release of Ubuntu and AMD releasing ATI drivers ect. I decided to start defragmenting my Vista partition to make way for the Ubuntu one, but in my attempts there is one part that just won't budge, right at the end of my windows partition (the only partition on the drive). I've defragged everything that PerfectDisk will, which includes system files and everything usually said to be undefragmentable. I was wondering if anyone knew what these files may be, or suggest another program for me to use.

And I won't remove vista. :)

---

### Post by ed-koala on 2007-10-28
I don't think *where* the files are is any problem.  When you repartition for Linux, it should take care of that for you.  You won't lose any files (unless something truly horrid happens).

I'm not sure how it works, but it does.

---

### Post by SGorilla on 2007-10-28
I'm trying to repartition with the built in vista tool, and when I try to shrink it it only allows me to shrink it by 566mb or something like that, and I'm guessing it's because of the files at the end of the disk.

---

### Post by louieb on 2007-10-28
If it were XP I'd say it was you swap file. In XP you right click on My Computer > Properties > Advanced tab > Virtual memory. You can disable it temporally before you shrink the partition.  

Wonder if Vista is similar.

---

### Post by SGorilla on 2007-10-29
> **louieb said:**
> If it were XP I'd say it was you swap file. In XP you right click on My Computer > Properties > Advanced tab > Virtual memory. You can disable it temporally before you shrink the partition.  

Wonder if Vista is similar.

I did that but the files are still there.
I found that PerfectDisk tells me what the files are and that they are mainly in the folders C:\System Volume Information C:\Windows or some randoms with a $ infront of them.
I'm gonna try another Offline Defragmentation which starts on reboot supposedly before these files are loaded.

Thanks for helping so far. :)

---

### Post by maybeway36 on 2007-10-29
If you can get the list of those files, you might want to post it here.

---

### Post by SGorilla on 2007-10-29
Woo!
I turned of virtual memory like louieb said and did an offline defrag. It worked! Now I just have to download Ubuntu.
Thanks for your help!

---

