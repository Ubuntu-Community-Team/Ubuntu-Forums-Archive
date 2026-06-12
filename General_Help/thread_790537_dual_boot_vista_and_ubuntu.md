---
title: "dual boot vista and ubuntu"
date: 2008-05-11
forum: General Help
---

### Post by cartesian on 2008-05-11
Hope I can get some help here in this forum, so thanks in anticipation!

I have a laptop with vista installed. I shrank one partition using vista's own tool and installed ubuntu.

The installation appeared to go well. The problem is when I reboot. I get the grub menu and if I select vista, it boots into vista no problem. If I leave it to boot into ubuntu I get the error "Error 17: cannot mount selected partition". I can't access ubuntu at all unless I use the live cd.

I would be grateful for any help pitched to a beginner in linux.

Thanks again

---

### Post by didooofidooo on 2008-05-11
may be you didn't shutdown vista but you hibernated it or you changed your hard-disk cable or jumper

---

### Post by cartesian on 2008-05-12
Thanks for your reply,

I've never hibernated vista and I didn't make any changes to cables or jumpers. It's a shop bought laptop that I've never had the back off.

Thanks

---

### Post by Sef on 2008-05-12
Applications > Accessories > Terminal

then type in this code:

```
sudo fdisk -l
``` Small L

then paste the results in here.

What file system did you install Ubuntu on?

---

### Post by cartesian on 2008-05-12
The file system will be whatever filesystem is used for vista. I've had a look at my C drive and it's NTFS.

I don't remember choosing a filesystem when I installed ubuntu.

Thanks for your reply.

I've attached a .txt file from the terminal window in ubuntu.

---

