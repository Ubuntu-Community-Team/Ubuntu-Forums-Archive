---
title: "Efax priveleges."
date: 2013-08-19
forum: General Help
---

### Post by mrjacque on 2013-08-19
Have installed efax-gtk on Ubuntu 12.04.
Have communicated to the fax and have efax going to that port. 
When I try to FAX, does not send.
error log says: 
efax-0.9a: 17:29:39 Error: can't open serial port /dev/ttyS1: Permission denied
efax-0.9a: 17:29:39 failed page /media/10GData/test.pdf.001
efax-0.9a: 17:29:39 finished - unrecoverable error
But when I do 
ls -l /dev/ttyS1
I get 
crw-rw---- 1 root dialout 4, 65 Aug 19 09:33 /dev/ttyS1
Which should give me write permissions to the modem.
What am I missing. Please be specific on the commands. Just learning Ubuntu.

---

### Post by steeldriver on 2013-08-19
Does the user you are running the efax application as belong to the 'dialout' group? If not, you can add them with the gpasswd command

```
sudo gpasswd --add *username* dialout
```

where *username* is the login name of the user. After that you will need to logout and back in for the change to take effect.

---

### Post by mrjacque on 2013-08-20
What I was looking for. I thought I tried that before but must have had the wrong syntax, 
Thank you

---

