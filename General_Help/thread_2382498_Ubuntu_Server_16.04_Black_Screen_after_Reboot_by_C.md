---
title: "Ubuntu Server 16.04 Black Screen after Reboot by Computer Reset Button"
date: 2018-01-14
forum: General Help
---

### Post by devilyan on 2018-01-14
Hello!

I'm not that new to Ubuntu however I'm not an expert either, I currently run an Ubuntu Server 16.04 at home dual boot with Windows 10 since I'm working with Odoo and wanted VSFTP, Plex, Samba amongst other for personal use at home, it's been working fine for months now, since November 2017.

Recently on one of the reboots to switch between Ubuntu Server and Win 10, the screen did not wanted to wake up (happened often) and just blindly typing sudo reboot and password like most of the times didn't work I had to reboot by reset button on the computer, after that Windows 10 works fine, Grub works fine but when I choose Ubuntu to reboot it just goes to a blank screen which wouldn't be so bad except for the fact that it seems to be stuck or frozen as well, can't access the server via SSH, or ping the Static IP I set it up on and of course Plex, FTP, etc is down.

There's no message, no sounds just a black screen after selecting on the Grub Ubuntu Server at reboot and each OS is installed on a separate SSD HD, what's the best way to approach it and try to solve it without loosing the configuration already done and the programs, it'll be a pain to setup again 3 Odoo environments, Git, VSFTP, Samba, Sendmail, Plex, Static IP, all the cron jobs I had to backup stuff I can't access now and remount the third disc that Ubuntu and Windows shared.

I did try the Recover broken System option from a Live USB but I either don't understand or know what to do or it's not recoverable, pretty sure it is the latter.

Thanks for the help and light anyone can give me.

---

