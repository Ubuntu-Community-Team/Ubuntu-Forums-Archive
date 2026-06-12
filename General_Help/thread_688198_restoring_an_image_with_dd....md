---
title: "restoring an image with dd..."
date: 2008-02-05
forum: General Help
---

### Post by Mia_tech on 2008-02-05
I just made an image of my computer over the network, using the commands below:

On the destination machine:
nc -l -p 5000 | gunzip | dd of=/dev/sda bs=100K

On the source machine:
dd if=sda bs=100K | gzip --fast| nc 1.2.3.4 5000

the image was compressed, and now I want to restore the image, just I'm kind of confuse, don't know what commands to use, to decompress the image back to the disk.... help appreciated

---

