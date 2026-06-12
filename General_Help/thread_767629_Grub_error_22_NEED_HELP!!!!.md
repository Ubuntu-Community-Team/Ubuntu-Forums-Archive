---
title: "Grub error 22 NEED HELP!!!!"
date: 2008-04-25
forum: General Help
---

### Post by wazdown355 on 2008-04-25
I have windows vista home basic a set up a partion on my hard drive and but ubuntu 7.10 then i deleted the partion and now when i boot up my computer it says grub error 22 and i don't have thr windows install disk my laptop did not come with it

thanks in advanced

---

### Post by dnzz on 2008-04-25
Try installing ubuntu to the same partition and be careful about the partition where you install grub. Do not delete that partition.

Once I did and saved like this :lolflag:

---

### Post by wazdown355 on 2008-04-26
but i got rid of the old partion and added it to my vista partition

---

### Post by Juffo-Wup on 2008-04-26
Well, GRUB (the boot manager) is still in your master boot record, but you wiped out its config along Ubuntu's partition (where it resided).

I have **never** done this, but according to this (well rated) [help page]("http://www.novell.com/coolsolutions/qna/1742.html") from Novell, you can just wipe out GRUB from the MBR with fdisk. This also seems to be supported by [Microsoft's knowledge base]("http://support.microsoft.com/?scid=kb%3Ben-us%3B315224&x=13&y=16") (or whatever it is called now).

Or... you could install Ubuntu again (and possibly edit GRUB's menu.lst to make it boot directly to Windows).

Of course, using a Windows install CD would be your safest bet, but you don't have one...

---

