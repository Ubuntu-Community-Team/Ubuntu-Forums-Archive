---
title: "CARD READER - can't open cards over 2 GB"
date: 2019-06-25
forum: General Help
---

### Post by freebirdek on 2019-06-25
Good/Bad Morning,

I have problem with my Ubuntu 18.10 and external USB card reader (any).

My SD cards 1 and 2 GB is read correctly.
When I try to do it with bigger SD cards (4, 16, 32 GB) reader show me "reading" card but I have no information on screen that anything happened.

I tried all cards on Windows Laptop, on DSLR, on ZOOM recorder... and cards are OK.

Any idea?

---

### Post by Claus7 on 2019-06-25
Hello,

I think that you should verify the connected cards with the ubuntu box. What is the output of df -h command after you have connected the card in question to your ubuntu box?

Regards!

---

### Post by Impavidus on 2019-06-26
What filesystem is on those cards? Nornally SD cards smaller than 64GiB are fat32, larger are exfat, but it could be different in your case.

Don't forget that Ubuntu 18.10 will reach end of life next month. Make sure to get upgraded before that happens.

---

### Post by emre-atakuru08 on 2019-06-26
[LIST=1]
[*]sudo apt-get install --reinstall udisks2
[*]please write this code after that rewrite here.
[*]but don't forget reboot your system.
[*]some sd card has lock. did you open that ?
[*]&#304;f you don't, you don't read to inside.
[/LIST]

---

