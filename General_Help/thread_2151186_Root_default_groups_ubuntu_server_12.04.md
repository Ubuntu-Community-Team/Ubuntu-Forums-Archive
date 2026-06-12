---
title: "Root default groups? ubuntu server 12.04"
date: 2013-06-03
forum: General Help
---

### Post by kevinxsalerno on 2013-06-03
I goofed up. 

usermod -G MYGROUP root

was suppose to be usermod -a -G MYGROUP root

Anyway, can somebody with ubuntu 12.04 type in 'groups root' and tell me what they are?

Thanks.

---

### Post by Hekabe on 2013-06-03
Er....just 'root' as far as I know, but I can't verify.

---

### Post by redmk2 on 2013-06-03
> **kevinxsalerno said:**
> I goofed up. 

usermod -G MYGROUP root

was suppose to be usermod -a -G MYGROUP root

Anyway, can somebody with ubuntu 12.04 type in 'groups root' and tell me what they are?

Thanks.

No users are in the group *root* by default.
```
sudo getent group root
[...
root:x:0:

```
If there were they would be after the last colon.

As is here```
users:x:100:bruce,bill,joe,jane,wendy,grace,eloisa,samantha,luke,john,guido

```

---

