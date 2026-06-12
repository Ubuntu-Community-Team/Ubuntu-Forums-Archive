---
title: "help using the dd command"
date: 2006-11-15
forum: General Help
---

### Post by elj4176 on 2006-11-15
I have been using g4u to backup my main drive for awhile now. I also use a dd command to shrink the image.

#
sudo dd if=/dev/zero of=/0bits bs=20971520   
sudo rm /0bits
#

My problem is that I now have added a second and much larger drive with several paritions on it. The image file is too large.
How do I remove the 0bits using the dd command on this drive? Do I simply cd to a dir on each partition and run the same command? 

Or will running the command on any partition on the second drive do the trick?

Thanks!

---

