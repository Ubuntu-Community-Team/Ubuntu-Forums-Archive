---
title: "Cannot boot, encrypted partition full."
date: 2014-04-12
forum: General Help
---

### Post by 80toy on 2014-04-12
Hello,

I cannot get my 12.04 partition to boot.  I get a error message that tells me to run in low graphics mode, which I do. Then at the next prompt box my key board and mouse no longer work.

That partition is completely full, as in no free space.

I tried using an ext2/3/4 file system browser from my windows partition, but past the home file directiory all files are encrypted, and I cannot tell what they are.  I'm not sure if I could delete them anyway.

I also tried using the recovery manager, but I am not sure how to operate it.  I couldn't navigate past my user folder to clear out or remove files in the root shell.

Finally I tried to access the file system from a live cd, but I don't have permission to view or delete files.

Can anyone please point me to directions or tell me how to clear up space on the linux partition that i cannot boot?  Thank you.

Edit: If I resized the partition from the live CD, what would happen to data on the two affected partitions?

---

### Post by ian-weisser on 2014-04-14
Is your entire linux partition encrypted?
Or is only your /home directory encrypted?
Or are merely the files within your /home directory encrypted?

Is your /boot directory encrypted?
If not, please post a list of the files in /boot.

---

