---
title: "Grub boot menu, error 22. will not boot."
date: 2007-09-23
forum: General Help
---

### Post by tribeca26 on 2007-09-23
I recently deleted my linux partition from within windows using partition magic because it had become corrupt. When i rebooted my computer, i thought that grub would have also been deleted, but it appears it has not, even though the partition it was on is gone, and is now part of my windows free space. When Grub loads now it says error 22 and will not let me do anything, hence, i cannot even get on windows now. It says "error 22". Any ideas on how I can get past this?

---

### Post by Arwen on 2007-09-23
Boot into the recovery console using your windows disk.. and in the prompt type "fixmbr" or "fixboot".It has helped out many times,I hope it'll help you too.:-)

---

### Post by Shazaam on 2007-09-23
What arwen said, If you have a Windows disk. A little info on the error here...
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by tribeca26 on 2007-09-23
whew, thank you! worked perfectly :]

---

