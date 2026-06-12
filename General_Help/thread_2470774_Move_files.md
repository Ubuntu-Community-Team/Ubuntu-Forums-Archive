---
title: "Move files"
date: 2022-01-10
forum: General Help
---

### Post by rick-fleckner on 2022-01-10
Very simple for some, tricky for me. How do I move a PDF from my desk top to a thumb drive?

---

### Post by yancek on 2022-01-11
You would first need to determine the mount location of the USB.  Mount meaning 'accessible' and this is generally under /media/username.  A simple way to do this is to look at the directory /media/username (replace unsername with your actual user's name) before plugging in the usb and then again after plugging in the usb.  THe new entry should be it  You can then use the 'mv' command in a terminal or you can use a GUI..  You may need to check the permissions on the USB you wish to copy to.


Explained in more detail at the link below.  There are numerous sites available explaining this process.

[https://askubuntu.com/questions/895733/copying-files-to-a-usb-drive](https://askubuntu.com/questions/895733/copying-files-to-a-usb-drive)

---

### Post by mIk3_08 on 2022-01-11
> **rick-fleckner said:**
> Very simple for some, tricky for me. How do I move a PDF from my desk top to a thumb drive?
you can simply apply the command below in your terminal
```
sudo mv '/home/Directory/Downloads/Filefolder/filename.jpg' '/media/Home/destinationFolder/foldername' 
```
Good Luck and cheers

---

### Post by schragge on 2022-01-11
When you insert a pen drive, does it appear in your file manager (GNOME Files aka Nautilus, or whatever you're using)? It would be in the sidebar.

---

### Post by TheFu on 2022-01-11
> **rick-fleckner said:**
> Very simple for some, tricky for me. How do I move a PDF from my desk top to a thumb drive?

Just like with that other OS?
Plug in the USB storage, it should show up in the file manager, copy and paste the file from where it is to where you want it.  To move, use cut/paste.

If that doesn't work, please describe exactly where it fails and we can ask more questions about file systems, permissions, exact programs used ... all of which could make it different on your system than on everyone else's where this works easily.

---

