---
title: "Sharing files with virtual machine"
date: 2007-06-26
forum: General Help
---

### Post by lhansen on 2007-06-26
I'm runny ubuntu 7.04 as my primary OS, and I have Virtual Box running a virtual partition of Windows XP Pro. I'd like to be able to access files on the Linux side from the Windows side. 

I really have no clue where to start. Does anyone have any tips?

---

### Post by AlexThomson_NZ on 2007-06-27
You should be able to set up Samba on your Linux box, and make them visible to the Windows box (think of them on the same lan with different ip addresses).  Installing WinSCP on the windows box is another (maybe easier) way, and then you can copy files back and forth (Linux has a built in scp command)

---

