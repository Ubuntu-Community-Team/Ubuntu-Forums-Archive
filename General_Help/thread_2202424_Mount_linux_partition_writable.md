---
title: "Mount linux partition writable"
date: 2014-01-29
forum: General Help
---

### Post by Macamba on 2014-01-29
I thought I knew how, but I clearly do not. I mount partitions automatically by entering the following lines in /etc/fstab
```

# Working
UUID=56e96ed1-4787-4081-afbc-3f4e77f6b2d2 /home/me/Stuff2  ext3	
defaults        0       2

# Also working
UUID=57825d60-616a-480e-bae7-4e044ac31183 /home/me/Stuff3  ext3	
defaults,user,exec,dev,suid        0       2

# Not working 
UUID=697eb1e8-bc75-45e1-a5d5-ca27f8be9e6c /home/me/Vrij ext3	
defaults  

```

The last line I added today after reformatting the partition, and copying the UUID to fstab. After a 'sudo mount -a' however the partition is not writeable. What am I doing wrong?

Caveat: I know these are not the place one should mount partitions. Humour me.

---

### Post by Morbius1 on 2014-01-29
A newly created or reformatted linux partition will have permissions of 755 and be owned by root. If you want to write to it then either change permissions to 777:
```
sudo chmod 777 /home/me/Vrij
```
Or change ownership to you:
```
sudo chown morbius:morbius /home/me/Vrij
```
Using your own user name.

---

### Post by Macamba on 2014-01-29
Thanks. That solved it.

---

