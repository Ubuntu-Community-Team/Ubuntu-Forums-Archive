---
title: "admin authentication asks for xubuntu's password, not mine"
date: 2014-03-16
forum: General Help
---

### Post by Nick_Dyer on 2014-03-16
Hi,

I make a new account on a persistent live cd of xubuntu with admin permissions, but when I download something it asks for xubuntu's password, which is nothing so anyone could download anything on my xubuntu. Any help would be appreciated.

---

### Post by tfrue on 2014-03-17
Have you tried typing in your password? 

While it's extremely not recommended to change roots password, it is possible. You will have to use "sudo" to get the privileges, then change the roots password from there.

Remember, **THIS IS NOT RECOMMENDED AND SHOULD NOT BE USED!** Just keep in mind that your system is now "that" much more vulnerable.

Type:
```

sudo su
(Enter your password when prompted)
passwd
(Enter the new password)
(Enter the new password, again)

```
That should do it, and you have now assigned a password to root. **BE CAREFUL!**

---

### Post by Nick_Dyer on 2014-03-17
I tried typing in mine, but it only asks for xubuntu's password. It doesn't let me select my user or anything. I set myself as an admin

---

### Post by efflandt on 2014-03-17
A persistent live iso is just intended to try or install whichever Ubuntu. As you found out it is not secure, since it could allow most anyone with a little knowledge to do most anything on the computer. Another issue it that you cannot easily install things that happen during boot, like video drivers or kernel updates, without remaking your own iso file, since initial boot is from a fixed squashfs file system. Although, you can add programs that run after boot.

So if you want it to be secure and be able to do all updates, you should do a regular install, which likely requires at least 8 GB of space, but would likely boot and run quicker.

---

