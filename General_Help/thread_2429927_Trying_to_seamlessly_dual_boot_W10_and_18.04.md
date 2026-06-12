---
title: "Trying to seamlessly dual boot W10 and 18.04"
date: 2019-10-25
forum: General Help
---

### Post by tahitiwibble on 2019-10-25
Hello to one and all.

I don't remember why, but I have foolishly been using Windows for the past couple of years. Yesterday I installed 18.04 as a dual boot setup. Wow! it's so much easier now than it used to be!!

Do any of you fine people have a link towards the easiest way to share my W10 folders whilst booted into 18.04? I will never more be booting into Windows unless I can't avoid it.

Many, many thanks for any input.

Martin

---

### Post by pushbike06 on 2019-10-25
Open your file manager and select "other locations" or the win10 drive may be listed e.g. Lubuntu  lists the win10 drive as say in my case S3A9982D003. You will need admin password to mount it and then you have access to the dirs and files of win10.

---

### Post by cruzer001 on 2019-10-25
Hello

Can't you just pull up your windows install using your file manager?  Works for me, I don't recall installing any special packages for reading ntfs.  I do run Nemo file manager instead of Nautilus, may want to try it.
```
sudo apt install nemo
```

---

### Post by sudodus on 2019-10-25
If Windows is hibernated or semi-hibernated (alias fast startup), the file system is marked such that Linux will stay away from it (in order to avoid corruption).

It can be worked around by rebooting Windows (instead of shutdown), but I suggest that you turn off Fast Startup in Windows. Then there will be no semi-hibernation: Ubuntu and other linux distros will be able to mount the Windows partition.

If you want to share data reading and writing from both operating systems, it is best to have a separate **data** partition with the file system NTFS. This way you will reduce the risk of corruption, when writing from 'the other' file system.

You can have a line in /etc/fstab to enter the data partition, so that you need not do it manually.

---

### Post by kurt18947 on 2019-10-27
> **sudodus said:**
> If Windows is hibernated or semi-hibernated (alias fast startup), the file system is marked such that Linux will stay away from it (in order to avoid corruption).

It can be worked around by rebooting Windows (instead of shutdown), **but I suggest that you turn off Fast Startup in Windows. **Then there will be no semi-hibernation: Ubuntu and other linux distros will be able to mount the Windows partition.

If you want to share data reading and writing from both operating systems, it is best to have a separate **data** partition with the file system NTFS. This way you will reduce the risk of corruption, when writing from 'the other' file system.

You can have a line in /etc/fstab to enter the data partition, so that you need not do it manually.

Turning off Fast Startup is a good idea but be aware it may be re-enabled by a Windows Update. I don't know if there's a way to prevent that or not. Storing data in a partition separate from Windows is a very good idea if you're able to do it.

---

### Post by tahitiwibble on 2019-11-02
Hey Cruzer, thanks. Yes I have been doing that. And thanks for the Nemo hint, it is the file manager that I much prefer from passed years.

---

### Post by tahitiwibble on 2019-11-02
Thank you gentlemen on and all.

---

### Post by HermanAB on 2019-11-02
If you don't use Windows to play games, then it is usually better to make a virtual machine and install Win7 in that.  Then you can run Windows in a window on Linux.  

A virtual Windows can use the network to save data on the host file system, so then sharing data is transparent also.

---

### Post by johnarnold on 2019-11-05
I've moved to this way of working albeit using VMware workstation. Windows is only fractionally slower as a VM and I have the ability to boot Ubuntu or any other flavour of Linux at the same time.

---

