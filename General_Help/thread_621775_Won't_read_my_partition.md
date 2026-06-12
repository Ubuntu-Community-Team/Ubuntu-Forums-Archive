---
title: "Won't read my partition"
date: 2007-11-24
forum: General Help
---

### Post by Gizkaguy on 2007-11-24
I have a 58 Gigabyte hard drive.

I was running OpenSUSE, but I also wanted to run Ubuntu. So, I used the Ubuntu Partitioning tool in the installation menu and gave OpenSUSE 20 Gig and Ubuntu 38. I decided I'd try CentOS 5 instead of OpenSUSE.

So I formatted the 20 Gig partition and installed CentOS on it. CentOS recognizes that it has 20 Gig, but when I reboot it goes to the CentOS GRUB screen. I only see 'CentOS' and 'Other' on the menu. I selected 'Other' and it told me 'There is no such partition. Press any key to continue ....'

Did the formatting of the 20 GB partition format the 38 GB one?

If not ... how do I get Ubuntu back? Will I have to install it again, and will I be able to keep CentOS?

---

### Post by Gizkaguy on 2007-11-24
Someone please help??

---

### Post by ntu on 2007-11-24
I am only a beginner, but I would doubt that GParted, when asked to format one partition would format the other. My guess is that the Grub for the new install is not configured to start the ubuntu partition, and sorry I don't know how to fiddle with Grub.

I have seen a number of people with what I recall as similar difficulties to yours in one of these ubuntu forums - probably Beginners. Have you done a thorough search?

It probably would have been better to put your original post in the Beginners Forum.

---

### Post by torgrot on 2007-11-25
Please see this page for everything GRUB
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

torgrot

---

