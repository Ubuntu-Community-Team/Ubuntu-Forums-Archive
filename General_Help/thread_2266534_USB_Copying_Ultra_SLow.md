---
title: "USB Copying Ultra SLow"
date: 2015-02-23
forum: General Help
---

### Post by box02-0 on 2015-02-23
Monday, February 23, 2:03 PM

Ubuntu 14.04 -  OS updated as of Feb.23.2015  - ASUS Z-97PRO with latest BIOS Update

Hi.

I'm having a strange timing problem copying data to usb2.0 or usb3.0 thumb drives.

I use GParted to format a 32gb usb3.0 thumbdrive to ntfs, and then Nemo drag/drop a 3gb file to it. Works fast and perfect. When I try copying another 3gb file to it, the last 1% takes several minutes. The data ends up there, but the transfer time is of concern.

The first large file xfer is fine, but successive large files always have the same problem. If I take the same 32gb USB3 drive and plug it into a USB2 port, it has a similar problem - that last 1% of data takes 8 minutes to transfer.

When I take the same 32gb thumb drive to WIN8, it can copy many 3gb files without a timing problem. Similarly, my old DELL (Ubuntu 12.10), with it's USB2 ports, can xfer all the data linearly in time. 

Finally, I took an 8gb **usb2** thumbdrive and tried copying a 3gb file to it. The first 99% took about 30 seconds, but the last 1% took about 8 minutes. CPU is at 1% load, but something called iowait is at 25%. It's like it's waiting on the thumbdrive to say "i'm done" (thumb drive light flashes periodically over the 8 minutes)

Any ideas ?

Thanks, 

M...

---

### Post by nerdtron on 2015-02-23
> Finally, I took an 8gb **usb2** thumbdrive and tried copying a 3gb  file to it. The first 99% took about 30 seconds, but the last 1% took  about 8 minutes. CPU is at 1% load, but something called iowait is at  25%. It's like it's waiting on the thumbdrive to say "i'm done" (thumb  drive light flashes periodically over the 8 minutes)

3GB, 8 minutes USB2.0 looks normal. As for the last 1%, I also experienced it on my NTFS 16 GB USB drive. I think the OS cached the data to be written. Xubuntu 14.04 here.

---

### Post by box02-0 on 2015-02-24
Hi.

Okay, I will buy that the USB2 3gb transfer should take 8 mintes. Good point about the caching. I do have 32gb of RAM. 

But it doesn't explain the USB3.0 transfer - the first 3gb file transfers in 30 seconds, the second one transfers like it's going to a USB2 port. 

I have since tried going back to an older ASUS BIOS with the same results.

Thanks for the reply.


M....

---

### Post by HermanAB on 2015-02-24
You can try ionice and see if that helps:
ionice -c 3 cp largefile /new/directory

---

