---
title: "partioning and /home"
date: 2008-01-03
forum: General Help
---

### Post by zach12 on 2008-01-03
Hello,
I will be going to try out some new linux distributions. 
And would like to have my /home in it's own partion but i haven't had a lot experience with
partioning. and need to resize my windows partion.


thanks

---

### Post by p_quarles on 2008-01-03
This link is a good guide to setting that up:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Also, make sure that you defrag and backup data before resizing your Windows partition.

---

### Post by stburman on 2008-01-03
My favorite tool for disk partitioning is the [GPartEd live CD]("http://gparted-livecd.tuxfamily.org/").  It's very easy to use.  The solution is basically a matter of clicking on the resize button after selecting the windows partition, then creating an ext3 partition in the empty space.  

If you're installing a new distribution, you can usually tell the installer to mount your home partition at /home.  If you're keeping a root partition, you'll probably want to edit /etc/fstab.  ```
$sudo gedit /etc/fstab
```
Then add a line for your home partition.  Mine looks like:```
/dev/hda6    /home    ext3   defaults    0    0
```  You'll want to change the path to your partition, and any other options you need to customize.
I hope this helps.  If this is wrong please correct me since I am a bit new to this myself.

---

