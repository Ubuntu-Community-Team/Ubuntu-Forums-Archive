---
title: "Machine boots to BusyBox after running updates"
date: 2008-05-03
forum: General Help
---

### Post by ed3120 on 2008-05-03
I ran update manager on my Mythbuntu install and now I'm getting the following message on boot:

BusyBox v.1.1.3 (Debian 1:1:1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


I can still boot a previous version via Grub, but the default/most recent version is dropping me to this prompt.  How do I fix this?

---

### Post by chrisccoulson on 2008-05-03
Please boot using the working kernel and post the contents of your /boot/grub/menu.lst, and also the output of:
```
ls -la /boot
```

---

