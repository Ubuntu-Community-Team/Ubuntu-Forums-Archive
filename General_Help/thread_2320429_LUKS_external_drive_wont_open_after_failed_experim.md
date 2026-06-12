---
title: "LUKS external drive wont open after failed experiment with Calibre library."
date: 2016-04-13
forum: General Help
---

### Post by brandon49 on 2016-04-13
Hello, 

Last year I encrypted an old laptop hard drive with LUKS. I made 2 50GB partitions (Skulldar, Muldy) each with the same password. After downloading Calibre I was experimenting with making multiple libraries of books on my different hard drives. I have a main library on one of my unencrypted drives and I wanted one on my encrypted drive as well. I figured when I opened Calibre when the encrypted drive was not connected via USB I would only see the library that was available on my unencrypted drive.

However, during the process of moving some books from the unencrypted to the LUKS drive, the transfer stalled. Not only that, but I was unable to do anything with GUI with the LUKS drive. I ended up disconnecting it and reconnecting it. Now I am unable to gain access to the encrypted partition that I used the most (Skulldar). I kept a file inside it that has all the login info to all the sites I have accounts with (paypal, amazon...etc) which is a huge hassle as I have been adding to that file for years. 

I want to supply as much info as is possible but Im no computer tech by any means. I have attached 3 images of the errors that I receive when the drive autostarts after being connected via USB. 

[ATTACH=CONFIG]268369[/ATTACH][ATTACH=CONFIG]268370[/ATTACH][ATTACH=CONFIG]268371[/ATTACH]

Also, I ran fdisk -l /dev/sdc1 (sdc1 is Skulldar) and the last line of output says that there isn't a partition table, I'm not sure how to proceed from here.

Thanks for any help or input

---

