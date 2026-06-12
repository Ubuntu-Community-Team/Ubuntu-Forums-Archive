---
title: "Ubuntu 14.04 LTS doesn`t boot after changes in BIOS"
date: 2017-01-03
forum: General Help
---

### Post by nurr on 2017-01-03
Sony vaio notebook doesn`t boot ubuntu 14.04 after following changes in BIOS:

1) Secure Boot = Disabled, and then back to Enabled
2) Boot Mode = Legacy, and then back to UEFI.

The reason for changing these settings was my attempt to solve problem with connection to the wi-fi.

---

### Post by nurr on 2017-01-04
Hello!
Sony vaio notebook doesn`t boot ubuntu 14.04 after following changes in BIOS:
1) Secure Boot = Disabled, and then back to Enabled
2) Boot Mode = Legacy, and then back to UEFI.

My current settings and an error message are in attachments.The reason for changing these settings was my attempt to solve problem with connection to the wi-fi. Could you please give a wise advice on my problem?

At first there was a message "Cannot find operational system", now it doesn`t show anything, just moves me back to Sony assistance interface with a message "Cannot boot windows" and suggests booting OS recovery or going back to BIOS. But there is no Windows on my computer, i deleted it long ago, before installing ubuntu. If I am choosing booting OS recovery, there is a message "Secure boot is failed. Operation system is invalid".

---

### Post by howefield on 2017-01-04
Threads merged, please do not create duplicate threads.

---

### Post by Geoffrey_Arndt on 2017-01-04
Why would you think changing bios & uefi would have any effect on wifi?   Since those are not even part of the Operating System (except partially for MS-Windows).

So, change the settings back to Legacy (in Legacy mode, secure boot should not be an option - - secure boot was brought on as a component of UEFI.)

Boot into a LIVE mode Linux such as Ubuntu, and be sure to save off any important files to external media such as flash-stick or external ssd/hdd.

IF the system will still not boot Ubuntu after resetting the bios back to Legacy, you may just need to re-install which should take less than an hour, whereas hunting down the specific problem could take much longer.

Note:   for the wifi connectivity issues, if you want to save time and aggravation, just get a Panda Wireless USB adapter from Amazon (about $10.00 usd).   I have several, and all work perfectly with no driver installs needed.   Go for the Panda Ultra nano sized dongle.    
[URL="http://www.pandawireless.com/"]
http://www.pandawireless.com/[/URL]

---

### Post by nurr on 2017-01-04
Thank you very much!!! :-) I ended up re-installing ubuntu 14.04  - installation alongside with existing one. So now i have a dual boot, from which my original ubuntu boots okay, with all my files and documents in it.

---

