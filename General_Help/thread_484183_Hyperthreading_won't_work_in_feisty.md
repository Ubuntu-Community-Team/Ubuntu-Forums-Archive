---
title: "Hyperthreading won't work in feisty"
date: 2007-06-25
forum: General Help
---

### Post by JPDVM2014 on 2007-06-25
Hi,

    I have been trying to figure this out for days. For some reason i can't get hyperthreading to work in Feisty. I have tried everything. I found a post on the forums that said to add ht=on to a line in the grub menu. That didn't work. I made sure ht was enabled in my bios. I even reinstalled to see if that would fix it. It was working then one day when i started Ubuntu i noticed it running a little slower, and when i checked the system monitor it only showed one CPU. I also know it isn't a problem with my CPU because i dual boot with XP and ht works fine in windows. The only thing i haven't tried is completely wiping the disk and then reinstalling. I don't really want to have to do that if at all possible. So does anyone have any ideas? Thanks.

---

### Post by atlfalcons866 on 2007-06-25
[http://ubuntuforums.org/showthread.php?t=469391&highlight=hyperthreading](http://ubuntuforums.org/showthread.php?t=469391&highlight=hyperthreading)

---

### Post by atlfalcons866 on 2007-06-25
After reading that article i dont really think hyperthreading speeds up applications that much. I used to have a pentium 4 with hyperthreading and i really didnt see any diffrence

---

### Post by JPDVM2014 on 2007-06-25
Alright. I figured out the problem. When i used the liveCD i had to use the boot options irqpoll nolapic and acpi=off. I didn't realize that after the install they were set as default boot options for the kernel. I removed them and ht works perfectly.

---

### Post by atlfalcons866 on 2007-06-25
is there a speed diffrence? i had a pentium 4 at 3Ghz with HT and i didnt see any diffrence

---

