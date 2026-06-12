---
title: "Unable to reinstall Ubuntu after forgetting disk encryption password"
date: 2017-03-20
forum: General Help
---

### Post by long-net on 2017-03-20
I forgot the disk encryption password on my laptop and intended to reinstall Ubuntu but I am unable to boot from USB or from an external optical drive. I've checked the BIOS settings and selected the USB as the boot drive but still no go. I know that my laptop support booting from USB since that's how I installed Ubuntu on it in the first place. What options do I have at this point?

---

### Post by #&amp;thj^% on 2017-03-20
What tool was used to burn with?
Also could be a corrupt download.
More info please.
And Welcome to the Forums.

---

### Post by RobGoss on 2017-03-20
Depending on what machine you have you should be able to boot from the USB by pressing **F-12** that's what works on most machines. I also have a small Mini book and I need to hit F-9 in order to boot from a USB

---

### Post by long-net on 2017-03-21
I have tried that and it does bring up the boot menu. However, after I select the USB drive, it won't boot the installer and instead start up Ubuntu and bring me back to the screen asking for my disk encryption password. I've tried the same USB drive on my other laptop and desktops and the Ubuntu installer boots up just fine. I know it's not a corrupt download or anything. I've scoured the forums but this seems like a lost cause.

What frustrates me the most is that I've been running Ubuntu on the laptop for months and have turned the laptop off many times yet this is the first time the OS asked me for the password so I naturally forgot it.

---

### Post by RobGoss on 2017-03-22
Try this to see if you can reset your admin password this post it might be of help
[http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

---

### Post by long-net on 2017-03-23
Thanks for the help but the solution in that thread only applies to forgotten root password, not the disk encryption password. I just need to figure out why my laptop is not booting from my USB drive.

---

### Post by RobGoss on 2017-03-24
After searching for an answer for your question I came across this post that may help, [http://askubuntu.com/questions/109898/how-to-change-the-password-of-an-encrypted-lvm-system-done-with-the-alternate-i](http://askubuntu.com/questions/109898/how-to-change-the-password-of-an-encrypted-lvm-system-done-with-the-alternate-i)

Someone else may have better knowledge working with encryption passwords I've never had to use them, hope this helps

---

