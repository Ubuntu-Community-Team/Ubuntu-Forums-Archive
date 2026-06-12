---
title: "DOS and SAMBA... Need Help!!!"
date: 2007-07-23
forum: General Help
---

### Post by prodezigner on 2007-07-23
First I want to explain my network a bit.

Cable Modem / Voice Terminal to D-Link Wireless G Router. The router goes to one computer in that room itself and two 100' CAT5 cables ran. One to a single computer, the other to a 5-port D-Link hub. The hub is running to two computers and my printer, and is branched off to another 5-port hub which is being ran to two separate ethernet controllers on a Linux shared server on the internal network. The wireless signals is picked up by my laptop and other laptop.

SAMBA picks up my HL-2070N. Prints flawlessly actually, no additional drivers needed other than the Ubuntu HL2060 drivers it comes with.

I've got VirtualBox 1.4 running Windows XP Professional, it picks up the printer just fine also... but the DOS program locks up in WinXP using virtualization. So I resort to another means of running DOS programs.

I've ran DOSbox and it works fine, I just need the ability to print. DOSemu works fine also using FreeDOS... BUT... I don't have a lot of know-how to channel printing and so forth.

Now, I can use my printer via USB... I don't have a problem with it, because my laptop doesn't have a LPT port.

I will ALSO need access to a TXT file from this DOS based program to transfer, if I could have USB functionality inside of the method I use, I can use a thumbdrive for backing up and restoring which... is a plus.

---

### Post by prodezigner on 2007-07-23
No replies yet, so I thought I'd give this thread a little bump.

---

### Post by HermanAB on 2007-07-23
Try running your DOS application with Wine.

---

### Post by prodezigner on 2007-07-23
With the newest WINE build, and the one with Ubuntu 7.04 in TERMINAL I get the following message...

[email]brandon@brandon-laptop:~/Desktop/pos640.zip[/email]_FILES$ wine pos.exe
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.

and then nothing after that... any advice?

---

### Post by prodezigner on 2007-07-23
ALSO...

wineconsole gives me a message about getting mugged...

and running it from the explorer like file manager that comes with wine does nothing...

---

