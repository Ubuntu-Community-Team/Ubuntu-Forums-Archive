---
title: "USB-DVD-player for Ubuntu"
date: 2023-03-20
forum: General Help
---

### Post by hhdyve on 2023-03-20
Hello, my new laptop has no DVD-player. I tried several kinds and brands of USB players, but no one was well accepted by Ubuntu. Is there any usable player on the market? Best regards heiho

---

### Post by MAFoElffen on 2023-03-20
I have a USB Portable LG BP50NB40 Blueray/DVD Writer ([https://www.lg.com/us/burners-drives/lg-BP50NB40-external-blu-ray-dvd-drive](https://www.lg.com/us/burners-drives/lg-BP50NB40-external-blu-ray-dvd-drive)) that works great. Was a bit spendy, but I needed a good drive that was fast, and that I knew would work with Windows, MAC and Linux.

The best compatibility I've found for portable optical drives with Linux were LG and Pioneer.

---

### Post by Holger_Gehrke on 2023-03-20
Basically any will do, I even used an old ATAPI-DVD-burner through an ATA to USB bridge device. As long as all you want to do is read and/or burn data discs that's all covered. The problem is in playing commercial video DVDs. Those are partially encrypted using the Content Scrambling System. To get around this you need libdvd-pkg from the repositories ('sudo apt install libdvd-pkg'), which uses some well known exploits to get around CSS. Please check on the legality of this approach in your jurisdiction before using.

Holger

---

### Post by hhdyve on 2023-03-31
Thank you very much! I'll try. It worked! Thanks again. Heiho

---

