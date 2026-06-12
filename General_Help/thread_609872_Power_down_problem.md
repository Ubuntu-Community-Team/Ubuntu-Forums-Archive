---
title: "Power down problem"
date: 2007-11-11
forum: General Help
---

### Post by Sardog on 2007-11-11
Since the last update, my computer will not finish powering down, hard drive stops then system just sits there at the ubuntu screen. If there is no solution how do I roll back to previous build of the kernel, I can see it there in the boot folder backed up but I don't know how to roll back to it.

---

### Post by matrooswolf on 2007-11-11
I have the same problem.

Have a look a this thread:
[http://ubuntuforums.org/showthread.php?t=591229](http://ubuntuforums.org/showthread.php?t=591229)

But I have to admit, I tried a lot of stuff, but the problem remains.  Ubuntu says system will now halt, but it doesn't.

Maybe you have more luck.

---

### Post by Sardog on 2007-11-11
Thanks for replying. I am using 7.10 and only installed it 3 weeks ago. At first it worked fine and it was only after an update about a week ago that this problem came up. I can't believe that just an update would do this. I am just going to wipe the partition and reinstall from the live cd since I have not had it long enough to grow attached to it, but if the problem reappears I will try another distribution.

---

### Post by matrooswolf on 2007-11-12
Problem seems fixed for me (at least for the last three shutdowns)

Try this:
add reboot=b in grub, after the kernel line, as explained in:

[http://ubuntuforums.org/showthread.php?t=591229&page=3](http://ubuntuforums.org/showthread.php?t=591229&page=3) post #23

seems to work for me.

I'm not so happy with upgrading to Gutsy Gibbon myself.  Feisty worked flawlessly. Gutsy Gibbon looks like a step back.  Hope Hardy Herron will rock!

---

