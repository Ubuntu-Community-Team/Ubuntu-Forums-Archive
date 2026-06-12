---
title: "Accidentally set root password and want to undo it"
date: 2017-12-16
forum: General Help
---

### Post by monkeybrain20122 on 2017-12-16
I tried to change my user password but in my stupor instead of ```
passwd my-user-name
``` 
I did 

```
sudo passwd
```, my understanding is that it has set a password for the root account, which is locked by default.

I then tried to undo it by
```
sudo passwd -dl root
```

I checked with
```
su 
```
and the root password I set no longer works (so it is good)

Are things now back to the way they were before? Is there anything more I need to do?

Thanks.

---

### Post by sisco311 on 2017-12-16
You should be fine. To make sure that the root account password is properly locked check out the content of the shadow file:
```
sudo grep ^root /etc/shadow
```
You should see something like:
```
root:**!**:17516:0:99999:7:::
```
The exclamation mark in the second field means that the password is locked. 

On a vanilla installation you will see an asterisk on the second field:
```
root:*:17516:0:99999:7:::
```

The difference between ! and * is that ! can be followed by the password the account had before it was locked. 

HTH

---

