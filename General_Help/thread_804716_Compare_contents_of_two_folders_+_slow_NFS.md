---
title: "Compare contents of two folders? + slow NFS"
date: 2008-05-23
forum: General Help
---

### Post by christianxxx on 2008-05-23
Hi,

I was copying files from a backup folder to the newly formatted drive.
My ever so creative 10 months old son poured water in my router so the copying was aborted, though nearly finished. 

Is there an easy way to compare the contents of the two folders?
The copy operation took far too long to repeat, so I only want to copy the missing files.

Also, I should probably check the files incase the last file was corrupted?

Last but not least, I was copying from an Ubuntu client to an Ubuntu server, both in a Wireless 54Mbit network. The folder on the server is an NFS-export. 
The problem is that the copying was EXTREMELY slow. I did it by command line, so I don't know the transfer rate, but 6 Gb took something like 24 hours to complete (nearly, as it was aborted by water.. ). I could have just burnt a DVD and copied directly, but I never expected it to be so slow... 

I could do the DVD part now, but I want to find a Linux solution to it.. :)

---

### Post by christianxxx on 2008-05-26
*bump*

---

### Post by prshah on 2008-05-26
> **christianxxx said:**
> Is there an easy way to compare the contents of the two folders?
The copy operation took far too long to repeat, so I only want to copy the missing files.
Also, I should probably check the files incase the last file was corrupted?


```
rsync  -c -a -r -u -z --progress [src] [dest]
```

This will copy only missing files and corrupted files (identified by checksumming so will take time) from [src] to [dest]. Since you feel that the network transfer rate is slow, the above command will compress and xfer files, so I hope you have a fast processor both sides. "man rsync" contains a lot more useful options, incase you'd like to know what the above options are.

---

### Post by christianxxx on 2008-05-26
Thanks! I'll sure give it a try!

---

