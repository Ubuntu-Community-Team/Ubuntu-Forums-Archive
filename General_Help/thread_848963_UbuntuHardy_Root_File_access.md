---
title: "Ubuntu/Hardy Root File access"
date: 2008-07-04
forum: General Help
---

### Post by metallica1973 on 2008-07-04
I am using Ubuntu/Hardy and have been trying to modify certain files with root access and "su -". When ever I even try to create a file I get this message

[PHP]root@Zithius:~# touch test
touch: cannot touch `test': Read-only file system  [/PHP]

I am assuming this is selinux or appamour security. How in the heck can I disable this so that I can modify what I need?

---

### Post by iaculallad on 2008-07-04
Check your /var/log/messages file and see if smartd daemon reported anything.

---

### Post by metallica1973 on 2008-07-04
I checked /var/log/messages and all it has is iptables dropped packets.

What application is causing this?

---

### Post by iaculallad on 2008-07-04
> **metallica1973 said:**
> I checked /var/log/messages and all it has is iptables dropped packets.

What application is causing this?

With no messages from smardt daemon would mean that your filesystem may been corrupted.

Try checking your filesystem partition with the fsck terminal utility:

```
fsck -nf /dev/fsystem_partition
```

---

### Post by metallica1973 on 2008-07-04
this is a brand new installation. It is this way on all of my system from the a default install.

---

### Post by metallica1973 on 2008-07-04
I figured it out. UBUNTU and other Distros like Mandriva are using the SUDO type of security and not the traditional root access. Check out this link:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

thanks for the help!

---

