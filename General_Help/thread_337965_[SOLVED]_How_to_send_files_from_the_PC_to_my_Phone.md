---
title: "[SOLVED] How to send files from the PC to my Phone via Bluetooth"
date: 2007-01-13
forum: General Help
---

### Post by siddartha on 2007-01-13
Hello,

So far I can send files from the phone to the PC painless and all the files are dumped in the home folder. How can I set the destination directory anyway?

I have searched the net and found the answer only about setting up what I already have Phone->PC. But no refference about how to send files the other way around from the PC to the phone. My Nautilus (dapper with all updates) doesn't know the bluetooth:/// location and also the Bluetooth manager doesn't do anything when I drop a file over the phone's icon.

---

### Post by siddartha on 2007-01-14
I just solved that myself. There is a gnome-obex-send command which asks for the destination device in a nice menu than sends the file after the command. Probably it could be put in the right-click menu in Nautilus as well to simplify things.

---

### Post by tkjacobsen on 2007-01-14
if you install "gnome-bluetooth" via synaptic you can right click on files and choose "send to". Then choose bluetooth in the send as dropdown menu...

---

### Post by siddartha on 2007-01-28
In my old Dapper there wasn't that send to... maybe I missed some package.

---

### Post by siddartha on 2007-10-16
For KDE is Bluetooth file transfer, for Gnome is Bluetooth file sharing - the former goes into the 'internet' menu category and the latter into the 'accessories'. Both work well and out of the box once you have established the connection with the phone. This is valid for feisty.

---

