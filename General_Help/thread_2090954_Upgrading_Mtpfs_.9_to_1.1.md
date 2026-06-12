---
title: "Upgrading Mtpfs .9 to 1.1"
date: 2012-12-04
forum: General Help
---

### Post by Zarckon on 2012-12-04
I was listening to the Linux Action Show a couple weeks ago and Matt Hartley [https://plus.google.com/108392504208314197482/posts/da7TRKVViWx](https://plus.google.com/108392504208314197482/posts/da7TRKVViWx) talked about the problem with Ubuntu 12.04 not being able to connect properly with Android devices running MTP. He just says to upgrade and gives a link to the launchpad build for MTPFS 1.1-2. [https://launchpad.net/ubuntu/+source/mtpfs/](https://launchpad.net/ubuntu/+source/mtpfs/).

I was hoping for a step by step in the upgrade. I can follow directions, but don't have the technical knowledge to just put all the files where they are supposed to go.

I've been looking through the forums here and MTP appears to be a problem for many with varied results depending on the device (I'm running an Asus A200 tablet. Most people are trying to connect phones).

Has anyone tried the upgrade suggested by Mr. Hartley? If so, has it worked for you? And, if it has, would you be so kind as to run through a step by step for the upgrade (for those of us like me who are a little slower and need the help)?

Thanks in advance.

---

### Post by Zarckon on 2012-12-06
Bump. Anyone?

---

### Post by Zarckon on 2012-12-08
Well, I was able to add the ppa for the mtpfs 1.1 build

sudo add-apt-repository ppa:olci/ppa1

But, it didn't work out quite the way I'd hoped. The device says that it's connected (but, it's done that all along). And when I do an "lsusb" it's in the list. But, it's not showing up in Dolphin. And not showing up anywhere else that I can see. So, close, but not quite there.

Did get a message saying that it doesn't exist in fstab when I tried mounting the directory I'd made for it in media. I had hoped that the upgrade to mptfs 1.1 would mean that I didn't have to muck around in fstab. I have seen something somewhere that gave examples of lines to put there. Forgot where that is at the moment. Anyone?

---

### Post by Zarckon on 2012-12-09
Okay, I found the following link and followed the directions with appropriate changes for my tablet (Acer A200).

[http://bernaerts.dyndns.org/linux/247-ubuntu-automount-nexus7-mtp](http://bernaerts.dyndns.org/linux/247-ubuntu-automount-nexus7-mtp)

udev shows the tablet connecting and disconnecting. But, KDE and Dolphin don't recognize it as connected. 

When I open a terminal with the tablet connected I get the following lines:

“alias: command not found
“alias android-disconnect=”fusermount -u /media/Asus”

Not a clue at present what's calling the alias command. It's not in either of the files I edited with Gedit.

Help, someone?

---

### Post by Zarckon on 2012-12-09
Okay, found the file that the error was coming from ".bashrc". It was a file I had changed earlier based on what I'd found in this article: [http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)

After correcting the offending lines, I was able to connect using the "android-connect" command from the article. So, following the steps there was more productive than the steps in the first article I posted.

However, there is still a problem. Now I can see all of the folders on the tablet in both main memory and on the SD card. But, all of the folders at the bottom level report as empty (with the exception of my Nook folder which does show the books there). Folders report as empty (e.g. my downloads folder in main memory) that are not empty when accessed using the tablet itself. So, steps forward, but something is still missing. 

Since it's sort of working what's here may be useful to others with the same or similar problem. I'd sill like help on getting actual access to the tablet in the sense of being able to see the files there, but am despairing of receiving any at this point.

---

### Post by Zarckon on 2012-12-09
Okay, this thread can be marked [Solved]. I was able to get full access to the tab. Follow the instructions in the link in my fourth (4th) post. Then if that doesn't get you in automagically, then go to a terminal and type "go-mtpfs -allow-other=true /media/Whatever_name_you_gave_this_folder". Then use your browser and go to root, media, Your_folder_name, and you should then see both main storage and your SD card (if you have one). I was able to see all files this time and was able to transfer a file to the device.

A huge pain to get this working and probably not really worth it since there are other ways to move files back and forth from your tab (bluetooth, ftp, etc). But, if, like me, you want to use a GUI to browse your tab and transfer files, then it does work. Yay!

---

