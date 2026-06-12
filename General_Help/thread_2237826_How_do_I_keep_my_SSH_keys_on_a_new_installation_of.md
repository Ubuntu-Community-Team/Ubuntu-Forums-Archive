---
title: "How do I keep my SSH keys on a new installation of Host?"
date: 2014-08-04
forum: General Help
---

### Post by npinn001 on 2014-08-04
May seem like a noddy question, but I have my host machine which I connect to my server with passwordless SSH keys.

Now, I need to wipe the Host and do a fresh installation. How do I make sure that the key to connect to this machine gets backed up and then put it back on the new host, to keep passwordless SSH login?

Thanks

---

### Post by Lars Noodén on 2014-08-04
On the target host, check the file ~/.ssh/authorized_keys. If it contains the public keys matching the private keys you are using then backup that file.  Then restore it on the target host after the system is re-installed (if the home directories go wiped).  If your system usage has more or less settled into a stable set up, then you might give consideration to using a separate /home partition.  That would then allow you to reinstall the system while leaving the user data and configurations alone.

---

### Post by npinn001 on 2014-08-04
> **Lars Noodén said:**
> On the target host, check the file ~/.ssh/authorized_keys. If it contains the public keys matching the private keys you are using then backup that file.  Then restore it on the target host after the system is re-installed (if the home directories go wiped).  If your system usage has more or less settled into a stable set up, then you might give consideration to using a separate /home partition.  That would then allow you to reinstall the system while leaving the user data and configurations alone.

Ok thanks. So I dont need to copy the .pub file? I just copy the authorized_keys file and thats it? Great.

I have a dual boot with Windows, whereas I'm wiping that to put just Ubuntu on there and so I will be moving to a seperate /home partition.

Thanks!

---

### Post by Lars Noodén on 2014-08-04
On the source host, the one you are logging in from, you should still keep the .pub files in addition to the private keys.  You might need the public keys again later, so keep them just in case.  

But on the remote host, the one that is the target of your logins, you only need your customized *authorized_keys* file.  That contains copies of the public keys and is what allows key-based login.  You can also use the file to restrict access to specific programs or from specific ip numbers.  See the manual page for sshd for the details on the *authorized_keys* file format.

---

### Post by npinn001 on 2014-08-04
ok great, its only the host I'm changing, so I'll just copy the keys to a USB stick and put them back after.

Thanks

---

