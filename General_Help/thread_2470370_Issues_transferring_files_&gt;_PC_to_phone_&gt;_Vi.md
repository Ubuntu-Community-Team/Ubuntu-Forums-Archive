---
title: "Issues transferring files &gt; PC to phone &gt; Via cable &gt;"
date: 2021-12-27
forum: General Help
---

### Post by GeordieJedi on 2021-12-27
Hi there guys I was hoping you could provide some advice
for an annoying issue that I have been experiening recently.

Issue:
I am trying to transfer some files (mainly music) between my Linux PC and my
phone (Samsung S21 Ultra)

However when I attempt this, I am experiening very slow speeds, and frequent
failures, where some of the files wont copy accross, and then errors
stating that either -

1. It "cannot find" the dir on the phone where I'm  copying the files to.

2. The phone "drops out" / from the PC (as if it's disconnected - even when
it's not)


Troubleshooting / extra info:

3. I'm trying to copy these files via USB cable (USB-C (phone) to USB-A (PC))
This cable was bought from a shop, (didnt come with the phone).
And is a standerd, basic cable.

4. My PC is hardwired into my network. So even though the phone and PC are on
the same network, I'd much rather use the USB cable to transfer the files
between each other

5. I've managed to do this with my previous phone (Huawei Mate 20 pro)
using the supplied USB cable (USB-C to USB-A cable) without any issues at all.


Questions:
1. Has anyone had similar issues ?
2. How did you overcome them ?
3. Is there anything that I'm missing, to get this to work successfully ?


TIA for any help or advice.



Equipment details:

Phone: Samsung S21 Ultra
OS: Android version: 12
One UI version: 4.0


PC:
Ubuntu 18.04 (LTS)
DE: KDE 5.12.9
Kernel version: 4.15.0-163-generic
OS Type: 64 bit

---

### Post by HermanAB on 2021-12-28
Hmm, you may have a bad cable.  However, since it is an Android phone I would install a ssh client/server and use scp over the home network.

---

### Post by kurt18947 on 2021-12-28
Some sort of Android problem? I have a Nokia 7.1 running Android 10 and it works as expected. I assume your phone asks if it should allow USB data transfer - however it's phrased?

---

### Post by tea for one on 2021-12-28
Have you considered [https://kdeconnect.kde.org/](https://kdeconnect.kde.org/)?

---

### Post by GeordieJedi on 2021-12-29
Hi guys.

Thanks very much for the replies so far.

@HermanAB
That's a fair point, however I dont currently have another USB-C to USB-A cable to test

I also have a USB-C to USB-C cable (used for charging)
I could, perhaps try getting a a USB-C to USB-A converter head for it, and retry

Also - Do you have any suggestions for SSH clients for Android, please ?

@Kurt18947
Yes - The phone shows a dialogue box, asking if I want to allow my PC to access the phone
Which I then chose "Allow"

@ tea for one
Yes I did try KDE connect, I havent had much joy with it (but TBF) I havent spent much time with it
Just a quick blast,
and (remembering that I'm trying to copy files from a hardwired PC to my phone
with the phone being on Wi-Fi).

---

### Post by Tadaen_Sylvermane on 2021-12-29
I don't move much around. There are countless ftp server apps that you can use. I don't know about sftp but for a quick transfer it's pretty simple and quick.

---

