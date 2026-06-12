---
title: "Lost files after moving some folders"
date: 2013-10-16
forum: General Help
---

### Post by saplatok on 2013-10-16
I am on Xubuntu 11.10. I moved some folders in one new folders in my usb key. Now all the subfolders are empty, the name of the foders are cerrect but there is noting inside. 
I have a big casper-rw file on my usb key. Maybe my files are stuck in it? is it possible?

Do you think it's possible to access to my files?

Thank you

---

### Post by varunendra on 2013-10-17
Was it a Live bootable USB key? Were you booted from it when moving the folders?

It sounds like you moved them into some folder in your 'Home' or Desktop while booted into the live session. In that case, yes, the casper-rw file is what is holding it all. It is just a virtual filesystem, usually ext3 which you can always access just by booting with the same usb key, or by mounting it manually. Usually -
```
sudo mount -o loop <casper-rw file> /mnt
```
Note that /mnt is just as an example. You can mount it at any directory you wish, and the <casper-rw file> should be replaced by the full path of the file.

---

