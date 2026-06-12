---
title: "Adding home after install?"
date: 2008-04-24
forum: General Help
---

### Post by lszanto on 2008-04-24
Hey there, I have installed hardy which might I say was a very nice experience but I stupidly forgot to add my /home partition to be mounted as /home, how do I go about doing this after I have installed?

thanks in advance, Luke

---

### Post by natrixgli on 2008-04-24
You could boot with the LiveCD and resize your root partition, then create a partition for home and edit /etc/fstab accordingly.

It might be quicker to just reinstall, since the installer is pretty speedy.




-n8

---

### Post by lszanto on 2008-04-24
I guess I could reinstall, I've just got everything setup though so it would be a pain to do that. If I can't find another method I guess I'll just have to.

---

### Post by Patsoe on 2008-04-24
You need to add an entry for /home to /etc/fstab. The format is explained in "man fstab".

edit: that is, if I understand your post well, you do already have the home partition, you just didn't mount it?

---

### Post by natrixgli on 2008-04-24
Hi Again:

How comfortable are you with getting under the hood? If you're not, then I'd recommend reinstalling as it would be much less frustrating. Otherwise the steps would be something like:

1) Boot liveCD

2) Use apt-get or synaptic to install gparted

3) Resize / (the root filesystem, probably /dev/sda1 or /dev/hda1)

4) Create your /home partition

5) Mount / (root filesystem)

6) Edit /etc/fstab to add a mount point for the new partition.



Check this out, it might help:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bodhi.zazen on 2008-04-24
Follow a guide for the settings in /etc/fstab :

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If yo need help with fstab :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by lszanto on 2008-04-24
Ehh, I don't think I could be bothered and it will be just as easy to use the LiveCd, thanks all anyways.

---

### Post by Patsoe on 2008-04-24
Hey, it's not that hard. The worst thing that can happen is that you mess up fstab ... and you can still reinstall then!

---

