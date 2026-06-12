---
title: "Infinitely deep non-empty directory, how to delete"
date: 2014-02-27
forum: General Help
---

### Post by david_ericmartin on 2014-02-27
I'm having problems on deleting a directory in an HFS+ HDD. I tried the following but it did not work.

1. rm -rf /path/to/directory (returned Permission denied)
2. sudo chmod 777 /path/to/directory
3. sudo rm -rf /path/to/directory (returned Directory not empty)

I also tried ls in the parent folder and permissions are dwrxwrxwrx. Using "ls /path/to/directory" returns "ls: reading directory .: Input/output error"

need to delete this folder

---

### Post by Habitual on 2014-02-27
What is the exact path and directory name please?

---

### Post by david_ericmartin on 2014-02-27
I usually name the drive F: so F:\transferAW

---

### Post by oldos2er on 2014-02-27
That looks like a Windows drive letter designation, which Linux doesn't use. If this partition is mounted in Ubuntu, can you please post the output from ```
mount
``` ?

---

