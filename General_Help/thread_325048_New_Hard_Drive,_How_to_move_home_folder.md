---
title: "New Hard Drive, How to move home folder?"
date: 2006-12-24
forum: General Help
---

### Post by themikeflynn on 2006-12-24
Tomorrow I'm going to install a second SATA hard drive in my parent's computer. They use Ubuntu primarily now, and their 40gb hard drive is getting filled up from their home folder. So I'm giving them a 250gb one, but I'm not sure how to make use of it with Ubuntu.

What I want to do is format that hard drive so Ubuntu recognizes it, and then move the /home/ contents into that hard drive. Is this a painless process? I'm pretty sure it has something to do with dd, but I'm not sure how to do it, and I don't want to mess it up.

Is there a guide for this, or can anyone give me some advice?

---

### Post by meng on 2006-12-24
Perhaps this will help.
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by taurus on 2006-12-24
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by meng on 2006-12-24
Your situation might be a little more complicated than in the guide, but hopefully not too difficult.

---

### Post by themikeflynn on 2006-12-24
I'll post again tomorrow or the 26th if I need further help. Thanks for the link and the speedy replies! :D

---

### Post by bodhi.zazen on 2006-12-25
You do not need to move /home to use the drive.

You can use the drive as a data partition.

Example: format it as ext3

Assuming the drive is sdb1:

```
sudo mkdir /mnt/data
sudo mount /dev/sdb1 /mnt/data
sudo chown root:users /mnt/data
sudo chmod 770 /mnt/users
```

Fstab (/etc/fstab):> /dev/sdb1 /mnt/data ext3 defaults 0 0

Now, for you father:
```
mkdir /mnt/data/father
ln -s /mnt/data/father /home/father/data
```

Etc.

Use what names you will ....

---

### Post by themikeflynn on 2006-12-25
I had a little trouble with the method from that psychocats guide. I'm glad I backed everything up. :mrgreen: 

So I went with the data folder method. I had some paths and links for the programs they use, but it all works out now. Thanks for that method, bodhi.zazen. :cool:

---

### Post by andyp11 on 2006-12-26
Is there any reason why one can't just copy the HOME dir. to anywhere, update GRUB accordingly, then delete the old HOME when/if everything's working fine?

---

