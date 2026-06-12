---
title: "Low-level suspend (/sys/power/state) works, GUI and pm-suspend don't (Asus 1015E)"
date: 2014-08-22
forum: General Help
---

### Post by gaussian on 2014-08-22
I have a Asus 1015E that originally came with 12.04 preinstalled. Yesterday I upgraded to 14.04.1 and almost everything seems to be working fine. Fn-F2 does not kill the wireless (reported elsewhere by many users) and that does not bother me. What on the other hand bothers me that it does not suspend. Or more correctly:

1) It did suspend when I tried running from a USB stick install of 14.04.1. Please do not recommend reinstalls, I'd like to solve it within my current upgraded version. I have been upgrading Ubuntu computers (and before that, Mandriva/Mandrake) without almost never having to revert to clean installs for a decade now. Life is more exciting that way.

2) It does not suspend (these are obviously related):
 a) closing the lid
 b) choosing suspend from the menu
 c) running pm-suspend from the command line (as a root)

3) It does suspend (and resume) perfectly from the command line (as a root) "echo mem > /sys/power/state". 

My question is: what to do to get 2) working properly given that there really is no hardware incompatibility reason for them not work?

---

### Post by gaussian on 2014-08-22
Apologies for answering my own thread: after little digging through the logs (/var/log/pm-suspend.log) found out that /etc/pm/sleep.d/11_usb_s3 was the offending script and removing it solved the problem. For posteriority (for less technical users): 

sudo mv /etc/pm/sleep.d/11_usb_s3 ~ 
This moves the file to your home directory. If this does not cure the problem you probably want to move it back to

sudo mv ~/11_usb_s3 /etc/pm/sleep.d/


Source: [http://askubuntu.com/questions/391051/ubuntu-13-10-wont-suspend](http://askubuntu.com/questions/391051/ubuntu-13-10-wont-suspend)

---

### Post by neilhuang on 2014-08-25
> **gaussian said:**
> Apologies for answering my own thread: after little digging through the logs (/var/log/pm-suspend.log) found out that /etc/pm/sleep.d/11_usb_s3 was the offending script and removing it solved the problem. For posteriority (for less technical users): 

sudo mv /etc/pm/sleep.d/11_usb_s3 ~ 
This moves the file to your home directory. If this does not cure the problem you probably want to move it back to

sudo mv ~/11_usb_s3 /etc/pm/sleep.d/


Source: [http://askubuntu.com/questions/391051/ubuntu-13-10-wont-suspend](http://askubuntu.com/questions/391051/ubuntu-13-10-wont-suspend)

I have the same laptop and thanks so much for figuring this out. You have done the Ubuntu community, including myself, a great favor by solving problems that helps many of us.

Thanks, Gaussian!

---

