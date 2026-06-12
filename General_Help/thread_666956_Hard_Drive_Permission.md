---
title: "Hard Drive Permission"
date: 2008-01-13
forum: General Help
---

### Post by jimartin8219 on 2008-01-13
Hello all,

I just formated 3 hard drives on my system but I can't create folders (grayed out). I'm new to Ubuntu so go easy on me.

Thanks.

---

### Post by taurus on 2008-01-13
What filesystem is that new partition and where did you mount it to?

---

### Post by dcstar on 2008-01-13
> **jimartin8219 said:**
> Hello all,

I just formated 3 hard drives on my system but I can't create folders (grayed out). I'm new to Ubuntu so go easy on me.

Thanks.

You probably need to mount them in the correct way, install the **pysdm** package and then use System-Administration-Storage Device Manager to set up auto-mounting, once this is done (and you reboot) you should be able to use them with your user credentials.

---

### Post by jimartin8219 on 2008-01-13
I used ext3 using qtparted, then I rebooted.  I can see them, I just can't create folders in them.

---

### Post by taurus on 2008-01-13
You just have to change the ownership of the mount point for that partition from root to your login name so you can write to it without root privilege.  _Assuming_ you mount it to /media/storage and your login name is **jim**, do

```
sudo chown -R **jim**:**jim** /media/storage
ls -la /media
```

---

### Post by articpenguin on 2008-01-13
if he is new he most likely choose ext3

---

### Post by jimartin8219 on 2008-01-15
> **taurus said:**
> You just have to change the ownership of the mount point for that partition from root to your login name so you can write to it without root privilege.  _Assuming_ you mount it to /media/storage and your login name is **jim**, do

```
sudo chown -R **jim**:**jim** /media/storage
ls -la /media
```
That did the trick.  Thanks very much!  I am learning something new.

Should I always use ext3 for all hard drives?  I have a eSATA external drive and I want to make sure I have the most stable format using Ubuntu.

Thanks.

---

