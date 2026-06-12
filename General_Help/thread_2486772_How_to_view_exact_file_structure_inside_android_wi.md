---
title: "How to view exact file structure inside android within linux?"
date: 2023-05-10
forum: General Help
---

### Post by anmac1789 on 2023-05-10
How can I view all hidden files and folders from inside a android phone which is mounted inside a ubuntu vm on vmware ? I can see only part of the directory, whereas there are 3 additional folders and 1 file that begin with .

---

### Post by MAFoElffen on 2023-05-10
I found this article:
[https://www.debugpoint.com/how-to-access-android-devices-internal-storage-and-sd-card-in-ubuntu-linux-mint-using-media-transfer-protocol-mtp/](https://www.debugpoint.com/how-to-access-android-devices-internal-storage-and-sd-card-in-ubuntu-linux-mint-using-media-transfer-protocol-mtp/)

I had to change a few package names for it to install. But it was a good read.

---

### Post by anmac1789 on 2023-05-10
I receive an error message whenever i try mtp-detect it says the phone is not initialized

---

### Post by MAFoElffen on 2023-05-10
Did you change the USB mode in the phone's setting from charging mode to... I think either debug, file transfer or mass storage mode? It says different things on different phones. To see that... On my phone I have to go to system information and press the last line 10 times for it to toggle into developer mode. Check your phone model information to see how to change yours into dev mode.

---

### Post by anmac1789 on 2023-05-10
On my galaxy s8, I have turned on USB debugging in developer options.

---

