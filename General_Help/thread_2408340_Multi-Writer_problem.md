---
title: "Multi-Writer problem"
date: 2018-12-17
forum: General Help
---

### Post by geovino on 2018-12-17
I'm trying to burn an .iso file to a usb stick with Multi-Writer. But it still thinks another iso is there but its been deleted and it won't see what is there. I even unsinstalled and reinstalled and still can't burn anything. Why does it still look for a file that's not there?

Is there a better app for burning to a usb stick? Thanks

---

### Post by speartip on 2018-12-17
Multi-Writer? Where did you get that from? It's not in the repos.
The usual tool for burning an iso to usb stick is usb-creator-gtk which is in the repos, & has always worked for me.

---

### Post by geovino on 2018-12-17
It was installed by default in version 18.04 . I didn't install it.
I'll try the one you recommended. Thanks

---

### Post by geovino on 2018-12-17
Trying with Make start up disc but doesn't work either.

Just formated the usb stick so it's OK, but both apps don't work. This is why I still burn DVDs, they don't have these problems.

---

### Post by ajgreeny on 2018-12-17
I suggest you install and try [mkusb]("https://help.ubuntu.com/community/mkusb"), easily the best application now available to create USB installation media disks.

---

### Post by HermanAB on 2018-12-17
Note that you don't actually need special SW to write an ISO to a memory schtick.  You can do it with dd, cat or even head or tail, if you can make head or tail of the syntax.

On UNIX, writing to a file, a file system, or a block device are equivalent and any utility that is advertised as being able to write to one of them, can write to all of them.  There is no difference in speed either.

---

### Post by speartip on 2018-12-18
Just an example for writing an iso to USB from the command line:    
First unmount USB: (You will need to find what drive your USB is so as not to destroy other data. On my system it's sdc.
[SIZE=3][FONT=arial]```
sudo umount /dev/sdc1 
```
then enter folder where iso is & open Terminal:  
```
sudo dd bs=4M if=*[COLOR=#ff0000]name_of_file[/COLOR]*.iso of=/dev/sdc status=progress  
```
[COLOR=#ff0000]Make sure of drive letter, it will destroy data.[/COLOR]


[/FONT][/SIZE]

---

### Post by ajgreeny on 2018-12-19
> **speartip said:**
> <snip>

[COLOR=#ff0000]Make sure of drive letter, it will destroy data.[/COLOR]

Which is one good reason for suggesting mkusb; it adds another safety level regarding the disk names meaning a much lower possibility of overwriting all your files using plain dd.

---

### Post by HermanAB on 2018-12-19
The good old kitty cat can do too:
sudo cat name_of_file.iso > /dev/sdc

---

