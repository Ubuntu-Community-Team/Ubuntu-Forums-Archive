---
title: "X server"
date: 2008-02-22
forum: General Help
---

### Post by satyaban on 2008-02-22
Dear Ubuntu User,
I am using Ubuntu linux in the AMD64 machine.
This is connected through LAN to sets of computer installed
with Linux and Windows.
I am trying to check Graphical package from Windows machine 
to remote linux (Ubuntu) machine.
But I am unable to connect the X window and it is showing following error.
Error in GXSTRT: Unable to connect to X server
From linux to Linux also X server is not working.
So please suggest me, how can I solve this problem.
Thanking you.
Best regards
Satyaban

---

### Post by u-foka on 2008-02-22
Hy!

If I understand your problem well, you want to connect direcly to the other computer's Xserver?
I can suggest you two different way's.
First if you don't need a full X session, youst want to run one or two apps remotelly, you can use ssh. From a linux box you can fire this command in a terminal: "ssh username@host -X -C" what tell ssh to forward the remote X connections to your local Xserver (-X) and to compress the communication (-C) this is recommended because the X protocol uses uncompressed bitmaps.
The second method is less secure, so you only want to use it if you absolutley trust your lan, and DO NOT USE IT FROM THE NET! So to use it you can go to System/Administration/Lgin Window, the remote tab, and then enable remote logins, then you can use the terminal server client app to connect to it (select the xdmcp protocol).

From windows box's, both ways are usable, you need Xming Xserver for windows from sf.net and for the first method you need the putty ssh client too.
The first way: simply run Xming.exe and then open putty, enter your connection parameters, and go to the Connection/SSH, check Enable compression, and go to X11 subcategory and check: Enable X11 Forwarding, then connect to your linux box, and any app you started in putty, show's up on your windows desktop perfectly ;)
Second way you can use Xming's configuration wizard to connect your xdmcp server.

---

