---
title: "Enabled root account, box is messed up"
date: 2007-02-14
forum: General Help
---

### Post by digilink on 2007-02-14
I was working on a friend's Ubuntu 6.06 box and I enabled the root account lastnight by doing sudo passwd and setting a password. 

Ever since I have done that, he is now experiencing strange problems such as synaptic not coming up correctly, sudo not working from the cli, etc. 

I have done this on every Ubuntu box in my house, as well as on several others and I have never experienced any of the problems he is having. He want's to format/re-install, but I'm confident this can be fixed without resorting to that. 

Anyone ever seen an issue like this and where should I start? I don't want him to re-install unless absolutely necessary.......

---

### Post by meng on 2007-02-14
He may be entering the root password when he should be entering the user password.

---

### Post by taurus on 2007-02-14
What's the output of this command from a terminal after he logs in to his account?

```
id
```

---

### Post by Crooksey on 2007-02-14
As a temporary solution he can...

```

sudo su
/usr/sbin/synaptic

```

---

### Post by digilink on 2007-02-14
> **taurus said:**
> What's the output of this command from a terminal after he logs in to his account?

```
id
```

Here's what I found out. The ID command was very helpful in pinpointing this problem. For whatever reason, his main account got dumped out of the admin account as well as several others. 

I'm not sure why that happened, could I assume this to be a bug and file it appropriately? I have not experienced this on my own install. I fixed it by adding his main username back to the groups that were missing in /etc/group.

---

