---
title: "install *.bin"
date: 2008-07-06
forum: General Help
---

### Post by damiloveu on 2008-07-06
I tried to install *.bin to /usr/share. But I found I didn't have the permission to do it.

I found that Ubuntu looks very safe, however, it is not good for a rooki like me.

I had installed the software package as *.deb, it was very simple as *.exe in Windows.

Could you tell me a way to install software, convert *.bin to *.deb or upgrade my account to root or some way else?

Thank you~

---

### Post by iaculallad on 2008-07-06
Insert the command **sudo** before the command to get a "root" privilege.

i.e:

```
sudo fdisk -l
gksudo gedit /etc/fstab

```

---

### Post by scragar on 2008-07-06
the best method is to run it from a terminal, go to applications>accessories>terminal, then type **sudo** followed by a space, drag the file into the terminal, then press enter to run it with admin rights(after confirming your password)

---

