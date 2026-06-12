---
title: "the X server error message..."
date: 2008-01-09
forum: General Help
---

### Post by firedragonsf on 2008-01-09
Here is my problem...

Grub Crashed, don't ask me how all i get when i boot is "error 17".

 ive had this problem before, where the problem was that windows had reformatted the Linux disk. the solution was to reinstall Linux. that worked. grub came back and booted anything. 

Now i have the same problem so i think, hey lets put the linux cd in again  and reinstall that should work... it didnt, the ubuntu cd wants to start ubuntu, but half way thrugh the loading it stiops and gives me the message:

Failed to start the X server( your graphical interface). it is likely that it is not set up correctly. would you like to view the X server output to diagnose the problem?
                                           <yes>                                       <no>

help? 

thanks...

---

### Post by Thyme on 2008-01-09
Hey, Thfiredragonsf:

The grub 17 error is when the "root=<partition>" (e.g. root=/dev/sda1) part in the grub entry is pointing to a non-existant or invalid partition.

The "Failed to start the X server" part can result from many errors. Whenever I get this message it's either because I have errors in my xorg.conf file or because I have the wrong nvidia graphics driver.

Try and log into a virtual terminal - <ctrl><alt>F6 - and check you xorg.0.log in the /var/log  directory.

Hope this helps :)

---

