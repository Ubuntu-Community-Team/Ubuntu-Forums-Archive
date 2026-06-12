---
title: "motorolla device manager not working in 13.10"
date: 2014-02-14
forum: General Help
---

### Post by iamrandy on 2014-02-14
i just recently got a new cpu and installed ubuntu 13.10 on it. but, my motorolla device manager won't mount my xt907. is there anyone that has any suggestions about what i can do?  Any help would be appreciated

---

### Post by iamrandy on 2014-02-15
i installed it through wine is there maybe a chance the install didn't work

---

### Post by 3rdalbum on 2014-02-15
You can't use Wine for USB communication. So, forget this Motorola program.

Your phone should mount on your Ubuntu desktop if you are using 13.04 or later. If this doesn't happen, try a different USB port and ensure your phone is going into Media Transfer mode when you plug it in. Not Picture Transfer mode.

Plug in the phone, wait twenty seconds then run the 'dmesg' command in the terminal. Copy and paste the last twenty lines into a reply to this message and we might be able to help.

---

### Post by iamrandy on 2014-02-16
[ATTACH=CONFIG]250410[/ATTACH][ATTACH=CONFIG]250411[/ATTACH] i hope this helps. also when  i get the message that it is unable to mount the notification on my phone goes from "connected as a media device"  to no usb connection but the charge continues

---

### Post by iamrandy on 2014-02-20
if no one can help me with this, this will be the first time ubuntu forums has not been able to help me out:sad:

---

