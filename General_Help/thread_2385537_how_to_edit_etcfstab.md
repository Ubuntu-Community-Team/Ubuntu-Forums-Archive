---
title: "how to edit /etc/fstab"
date: 2018-02-21
forum: General Help
---

### Post by christon74 on 2018-02-21
Good evening fellow UbuntersO:)
What I am trying to do is just create a swap partition after the OS install. Or rather create a Swapfile. And where I am stuck is how to make this swapfile permanent.  I understand I have to edit the /etc/fstab file using a terminal. Can someone please give me step by step instructions how to do this so that I do not completely muddle things up ? (something at which I usually excel :oops:)
Thanks in advance. 

Chris.

---

### Post by deadflowr on 2018-02-21
Following this guide:
[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F]("https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F")
Change the name to whatever yours is.
(from the /mnt/1GiB.swap to whatever your is)

---

### Post by oldos2er on 2018-02-21
Good idea to make a backup copy before editing: ```
sudo cp /etc/fstab /etc/fstab.backup
```

---

### Post by HermanAB on 2018-02-22
It is not obvious at all, but a most excellent swap user guide is in the swapon man page:
$ man swapon

It is a good guide and will tell you everything you need to know about swap.

---

### Post by christon74 on 2018-02-22
Many thanks to all of you, Oldos, Deadflowr, Herman. I have read the guide (link posted by Deadflowr) and it worked. Swapfile successfully created. :D

---

