---
title: "ecryptfs Private folder is not locked (it is mounted) by default when I log in"
date: 2012-12-25
forum: General Help
---

### Post by nerdinator on 2012-12-25
I installed ecryptfs-utils.
 ```
sudo apt-get install ecryptfs-utils 

```Did :
```
 ecryptfs-setup-private 
```I chose a password and I am able to mount and unmount my Private folder (~/Private).
Mount :
```
ecryptfs-mount-private
```Unmount :
```
ecryptfs-umount-private
```But what I notice is, when I log out and log back in, the Private folder can be opened and viewed.
Only when I do :
```
ecryptfs-umount-private
```does it get locked. 
I wish I didn't have to do it everytime I logged in.

I would want it to stay locked (unmounted) when I log in. 

How can I do that?

---

