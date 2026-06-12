---
title: "[SOLVED] Help with /home partition"
date: 2007-10-22
forum: General Help
---

### Post by Tom B on 2007-10-22
While running Feisty, I moved my /home directory to its own partition, using [this guide]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/"). Then when I updated to Gutsy something went completely wrong, so I downloaded the install cd and installed Gusty over the partition that held Feisty. Then I tried to make Gutsy recognize that the /home was on another partition, using the same guide as a reference. However, before I added the line to the “/etc/fstab” file that tells it to mount home when I boot, a notification came up that because of some updates I needed to restart. So I restarted, and had no problems. When it booted up, my old files were in /home and all my applications' preferences were saved. Then I shut it down and when I turned it back on and try to log in, it gives me an error that my $Home directory doesn't exist. I've tried a failsafe session (it fails) and I have tried recovery mode, which worked, but I couldn't figure out how to fix my problem. Any suggestions?

---

### Post by dpar on 2007-10-22
I had a similar problem. I believe it's a problem with fstab. The edit you tried before didn't take and you will have to try again.
Once I got my fstab edited properly, everything booted ok.
Good luck.

---

### Post by Tom B on 2007-10-22
Thanks for the reply. How did you get your fstab edited properly? All I can do is run a recovery session, and I have no idea how to do it from the terminal.

---

### Post by logos34 on 2007-10-22
try 
[B]
nano -w /etc/fstab[/B]

---

### Post by dondad on 2007-10-22
> **Tom B said:**
> While running Feisty, I moved my /home directory to its own partition, using [this guide]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/"). Then when I updated to Gutsy something went completely wrong, so I downloaded the install cd and installed Gusty over the partition that held Feisty. Then I tried to make Gutsy recognize that the /home was on another partition, using the same guide as a reference. However, before I added the line to the “/etc/fstab” file that tells it to mount home when I boot, a notification came up that because of some updates I needed to restart. So I restarted, and had no problems. When it booted up, my old files were in /home and all my applications' preferences were saved. Then I shut it down and when I turned it back on and try to log in, it gives me an error that my $Home directory doesn't exist. I've tried a failsafe session (it fails) and I have tried recovery mode, which worked, but I couldn't figure out how to fix my problem. Any suggestions?

If you log into a console, can you see the folder? If so, can you change into it and view the files? (might need sudo). If you can, then change to that folder and do ls-l to see if your files are there and what the ownership and permissions are set to. I had a problem like that when I screwed up my permissions and ownership. If this is the case, you can use chown and chmod to reset the owner and permissions. that fixed it for me.

---

### Post by Tom B on 2007-10-22
Fixed! Thank you both for the help. I used nano and edited fstab properly, then I logged in and everything was back to normal (except I had to configure my network again, which is weird and possibly unrelated). Thanks again.

Also, how do you change the title to say fixed in it?

---

### Post by logos34 on 2007-10-22
> **Tom B said:**
> Fixed! Thank you both for the help. I used nano and edited fstab properly, then I logged in and everything was back to normal (except I had to configure my network again, which is weird and possibly unrelated). Thanks again.

Also, how do you change the title to say fixed in it?

>Thread Tools>mark as SOLVED

---

