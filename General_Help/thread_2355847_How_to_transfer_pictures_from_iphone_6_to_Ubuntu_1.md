---
title: "How to transfer pictures from iphone 6 to Ubuntu 16.04?"
date: 2017-03-17
forum: General Help
---

### Post by lou.degenaro on 2017-03-17
Having trouble getting iphone6 pictures xferred to Ubuntu 16.04.

1. plug-in iphone via usb port
2. iphone asks do I trust computer: yes
3. Two iphone camera icons appear on gnome
4. a pop-up windows says: You have just launched a medium with digital photos. Choose which application to launch. 
5. I choose Shotwell
6. a pop-up window says: Shotwell, Unable to fetch previews from the camera.  Could not claim the USB device (-53).

Please advise.

Thanks.

Lou.

---

### Post by mörgæs on 2017-03-18
Are you able to transfer the pictures using an ordinary file manager?

---

### Post by efflandt on 2017-03-18
Even with Android connected with USB as MTP (media transfer protocol) and default file manager (nautilus), you cannot directly open photos on the phone with an image viewer (I have not tired Shotwell). But they can be copied to your computer and opened.

Since iPhones typically use iTunes in Windows to access files, I don't know if you need something else in Linux.

Is there any sftp client app for Apple devices? When I still had Ubuntu 12.04 and could not get MTP to work, I used an Android app called AndFTP to sftp transfer files to/from Ubuntu over WiFi.

---

