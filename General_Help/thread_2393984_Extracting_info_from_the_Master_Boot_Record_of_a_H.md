---
title: "Extracting info from the Master Boot Record of a Hard Drive using Ubuntu?"
date: 2018-06-11
forum: General Help
---

### Post by Hishighness on 2018-06-11
Good day all, I have a hard drive that is on the edge of complete failure. Windows won't boot up and It can't be repaired. I can access the undamaged portions using a Ubuntu live cd but I have a problem.

The HDD was in a laptop and it has my Windows key built into the MBR. To reinstall windows 10 I need this key. Normally I'd just use Belarc to get it but I can't get Windows to run as I mentioned. So I'm wondering if there's any way to extract this information using Ubuntu.

Thanks for your time.

---

### Post by yancek on 2018-06-11
The link below shows commands to extract info from the MBR although it may not get you the info you want in human readable form.  Make sure you get the right drive (if you have more than one) and also read the page completely before running commands.

[https://blog.philippklaus.de/2010/02/have-a-look-at-your-mbr-using-dd-and-hexdump](https://blog.philippklaus.de/2010/02/have-a-look-at-your-mbr-using-dd-and-hexdump)

My understanding of this is that the key is in the BIOS on the motherboard of the computer.  You might take a look at the link below for a person with a similar problem.

[https://hardforum.com/threads/recover-win-10-key-from-unbootable.1924010/](https://hardforum.com/threads/recover-win-10-key-from-unbootable.1924010/)

---

### Post by dragonfly41 on 2018-06-11
A few days ago I found this thread and bookmarked it ..

[https://askubuntu.com/questions/423827/how-can-i-read-the-windows-8-licence-key-with-ubuntu](https://askubuntu.com/questions/423827/how-can-i-read-the-windows-8-licence-key-with-ubuntu)

---

