---
title: "Black screen upon startup"
date: 2022-01-10
forum: General Help
---

### Post by mjnolan on 2022-01-10
I just recently installed Ubuntu and had to restart but when it did, this black screen popped up. The computer logo shows up fine, but then nothing except for a terminal like text enter line (not able to type anything though).

I had run two commands from terminal to try and enable function mode:

echo options hid_apple fnmode=1 | sudo tee
sudo update-initramfs -u -k all

What methods can I try to fix this.

---

### Post by mjnolan on 2022-01-10
Edit: fixed.

It turns out that the gui was uninstalled at some point. I was able to access the command line by pressing ctrl + alt + f2 (I think) and reinstalled the unity desktop. This fixed the issue.

---

