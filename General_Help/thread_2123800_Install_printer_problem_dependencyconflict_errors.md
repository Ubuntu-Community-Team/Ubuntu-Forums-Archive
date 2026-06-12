---
title: "Install printer problem dependency/conflict errors"
date: 2013-03-09
forum: General Help
---

### Post by rapattack1 on 2013-03-09
Hi i am at a friends house installing her printer which is a HP photosmart C5180. I got hplip via the HP site/opensource site. [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)
but when it comes to part of the install in the terminal this is where i am stuck
```
DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --assume-yes python-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #1...
Running 'sudo apt-get install --assume-yes python-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #2...
Running 'sudo apt-get install --assume-yes python-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #3...
Running 'sudo apt-get install --assume-yes python-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? 

```
She is using 10.04 Ubuntu and i don't know how to proceed. Appreciate any help thanks :0)

---

### Post by Mr. Shannon on 2013-03-09
Why not just use:
```
sudo apt-get install hplip
```
In fact, I think my install came with hplip, so the printer should work automatically.  If not then follow the instructions here ([https://help.ubuntu.com/10.04/printing/C/printing.html](https://help.ubuntu.com/10.04/printing/C/printing.html)) for how to add the printer.

---

### Post by rapattack1 on 2013-03-09
Yep did that. Thats at the beginning of what i did and later i got those errors

---

### Post by rapattack1 on 2013-03-09
Initially the printer installed the usual ways. Then i changed the cartridges and the system said the printer is idle which it wasn't. I couldnt print a test page or anything. So those errors are important and nothing else works

---

### Post by rapattack1 on 2013-03-11
Anyone? Sorry i really need help as i got cartridges for this person and ebay only gives you so much time to do the feedback thing :0)

---

### Post by rapattack1 on 2013-04-04
I am back at my friends now and not getting very far. I tested the copy feature on the printer that works independantly of the computer and that works so i know the printer/ink works. Good. Got into synaptic and installed the hp-toolbox and looked at the hp gui but its still not seeing the printer. lsusb doesn't list the printer. Is it because it is plugged into a hub? the only other thing plugged into the hub(4 port usb 2.0) is the mouse as she only has only other usb port in the computer and that is not functioning. So i had to attach the hub. She also uses a usb stick and usb bluetooth dongle but i pulled them out. It is a powered hub and just realised the adapter is not plugged in. Will reboot and see if that makes the difference

---

### Post by rapattack1 on 2013-05-03
Sorry i got this working but can't remember right now what i did as this was weeks ago

---

