---
title: "Ubuntu 1804 on Raspberry Pi4 - Forgot Password - Can I recover?"
date: 2020-05-25
forum: General Help
---

### Post by k3nden on 2020-05-25
Installed Ubuntu 18.04.02 on a raspberry pi4. Set it up with ROS and much more - got distracted by Corona, and now I am at a complete loss as to the password that I created for the ubuntu user. 

All searches indicate that I should append cmdline.txt with either init=/bin/sh or init=/bin/bash.  This has not worked. The boot continues to "Ubuntu login:"

Is there a way for me to recover this microSD? 

TIA

---

### Post by HermanAB on 2020-05-25
The whole RPi system is on the SD card, so you can stick the card into any other Linux computer with a SD card socket and edit the files in /etc.  So, unless something changed in the last 30 years, you should be able to clear the entry in the passwd file so that you can log in with no password.

---

### Post by k3nden on 2020-05-25
Thank you for your response. Would i delete the entire line for the ubuntu user or some portion of it (x)?  

'ubuntu:X:1000:1000:Vivek Gite:/home/ubuntu:/bin/bash'

SOLUTION that Worked for me:
I did figure out how to edit the /boot/cmdline.txt file to make it halt and allow me to change the passwd for the ubuntu user. The trick for me was to add " [COLOR=#000000]init=/bin/sh 1".  The 1 stopped execution and i was able to change the password, update the cmdline.txt file, and login using the new password. 
[/COLOR]

---

