---
title: "USB copier?"
date: 2023-02-17
forum: General Help
---

### Post by josephchrzempiec on 2023-02-17
Hello, I was wondering What would b the best way of doing a usb copier? I have a 16 Port USB Powered hub and I wanted to make it into a copier. What I wanted to do is have one usb port for the main Copy on the hub or the pc usb port and 15 or all 16 ports for the client usbs.

Joseph

---

### Post by HermanAB on 2023-02-17
Well, be sure to use a fast type of USB, such as USB3, otherwise you will wait forever.

---

### Post by TheFu on 2023-02-17
> **josephchrzempiec said:**
> Hello, I was wondering What would b the best way of doing a usb copier? I have a 16 Port USB Powered hub and I wanted to make it into a copier. What I wanted to do is have one usb port for the main Copy on the hub or the pc usb port and 15 or all 16 ports for the client usbs.

Joseph

Beware.  Many USB devices don't work correctly through external USB hubs.

I take it you don't plan to use this like a scanner with 15 paper printers?  Perhaps you could clarify what sort of USB device you plan to copy?

---

### Post by SeijiSensei on 2023-02-17
.

---

### Post by josephchrzempiec on 2023-02-25
A Friend of mine ask me to help him to come up with a USB copier. He works on making documents for his work and he having a hard time doing one flash drive at a time. I'm just trying to help him out.

---

### Post by HermanAB on 2023-02-25
Sure, it is really no big deal to do multiple copy actions in parallel, but due to the limitations of the USB bus and the USB memory devices, there will be a bottleneck at 2 or 3 devices.

Anyhoo, try something like this:
$ ls /dev/sd?
and note what you see.

Plug the source widget in and repeat the above to see what was added - probably sdb

Plug the destinations in and repeat - probably sdc, sdd and sde

Note that I have not tried this. I’m leaving the experimenting to you since I don’t want to accidentally mess up my own systems.

Note that a typing error can result in erasing your main disk drive which is probably sda!

Thinking about it some more - multiple cat commands will not work since the first cat will probably open sdb for read/write which will lock out subsequent cats, so you would need one cat to read the file, with a tee command for writing it to multiple files.

Try something like this:
$ sudo cat /dev/sdb | tee sdc sdd sde

That looks so simple, that it is probably correct!

---

### Post by mIk3_08 on 2023-02-25
> **josephchrzempiec said:**
> Hello, I was wondering What would b the best way of doing a usb copier? I have a 16 Port USB Powered hub and I wanted to make it into a copier. What I wanted to do is have one usb port for the main Copy on the hub or the pc usb port and 15 or all 16 ports for the client usbs.

Joseph

There will be a difference between the chip based storage and the spinning hdd when it comes to usb storage enclosure. 
If you have a 3.5" desktop size hdd in the usb enclosure be sure that the enclosure have a power built-in enclosure but if you have 2.5" hdd it will sustain without any power built enclosure. 
Usb can always give power to the enclosure. It will give you best speed but compared to ssd storage it has a big difference. Regards and cheers.

---

### Post by TheFu on 2023-02-25
> **josephchrzempiec said:**
> A Friend of mine ask me to help him to come up with a USB copier. He works on making documents for his work and he having a hard time doing one flash drive at a time. I'm just trying to help him out.

So ... you want a "disk duplicator for USB devices?"  Do you want it to perform a bit-for-bit copy or to be efficient?  You can't have both, well, not automatically.  There are good reasons for both.  You can create 2 scripts ... one that does bit-for-bit copying and one that uses gdisk+rsync and only copies the actual data.  

Regardless, you'll probably want to use the /dev/disk/by-path/  symbolic links to get to the USB storage devices and keep them separate.

Since you enjoy this, I'll leave it up to you to figure out. The language used to solve the problem will matter.  IF you plan to use bash, search for "bash absg" to find the guide for all that bash can do.

---

