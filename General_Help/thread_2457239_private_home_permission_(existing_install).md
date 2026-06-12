---
title: "private home permission (existing install)"
date: 2021-01-28
forum: General Help
---

### Post by yaminb on 2021-01-28
Hi all,

I was reading this post for 21.04 which makes user home directories private.
[https://discourse.ubuntu.com/t/private-home-directories-for-ubuntu-21-04-onwards/19533](https://discourse.ubuntu.com/t/private-home-directories-for-ubuntu-21-04-onwards/19533)

I wasn't aware they were not.

So I decided to make the change on my system:

```

# ensure future users homes are safe
sudo sed -i s/DIR_MODE=0755/DIR_MODE=0750/ /etc/adduser.conf

# then get your own house in order
chmod 750 $HOME
setfacl -m u:libvirt-qemu:rx $HOME

```

This did change /home/me to 750. Yet, all the files inside /home/me still have their old permission, which in some cases in 755.
Is this an issue? Like hypothetically speaking if someone knows the name of a file in my home, can they read it? I suspect they can.

Would it be safer to do a recursive chmod for every entry that is 755 to 750? I don't know. Anyone have experience here that might have gone through such a migration?

---

### Post by Impavidus on 2021-01-28
> **yaminb said:**
> 
Is this an issue? Like hypothetically speaking if someone knows the name of a file in my home, can they read it? I suspect they can.

You can experiment with this yourself. It helps to understand permissions. But the answer is no. To read a file, you need read permission on the file and read and execute permission on all directories in the path.

---

