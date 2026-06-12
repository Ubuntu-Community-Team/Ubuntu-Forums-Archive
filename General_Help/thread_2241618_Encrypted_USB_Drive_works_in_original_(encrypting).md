---
title: "Encrypted USB Drive works in original (encrypting) machine only."
date: 2014-08-27
forum: General Help
---

### Post by bpm253 on 2014-08-27
I have encrypted a USB drive using the 'disk' utility and have no problems with it on the machine which I used for this. 

However, when I try and use this drive on another machine (also with Ubuntu 14.04) I am asked for the password and when I enter it correctly get the message,

[FONT=arial][I][FONT=verdana][COLOR=#000000]This location could not be displayed.[/COLOR][/FONT]
[/I][/FONT]
[FONT=arial][COLOR=#000000][FONT=verdana]*&#8203;You do not have the permissions necessary to view the contents of “<drive-name>”.&#8203;*[/FONT][/COLOR]
[/FONT]

I know very little about Ubuntu (you can tell, right?) so please feel free to speak to me very slowly :) ....

1. Is this an encryption or permissions issue?
2. How do I solve so that drive works on both (and therefore I assume, any) Ubuntu machine.

Any help very gratefully received. If any further info is required then please just let me know and I will respond quickly.

Ben

---

### Post by CaptainMark on 2014-08-29
It's easy enough to figure out if its a permissions issue using either of these methods, if either one works, its permissions that are your problem
1. (If you're ok with terminal use) Once you have typed in your password to decrypt the drive can you view the contents using ```
sudo ls /path/to/drive
```Obviously you would put your real path name instead of /path/to/drive

2. On your machine that created the encryption, in a file manager, right click on the folder where the drive is mounted and select properties, there should be a tab named permissions (or similar) change the permissions so everyone has read + write access, then try again on the other machine.

These methods should show you if it is permissions causing the problem and it it is then this guide to special permissions should come in useful [http://docs.oracle.com/cd/E19683-01/816-4883/secfile-69/index.html](http://docs.oracle.com/cd/E19683-01/816-4883/secfile-69/index.html)

---

### Post by bpm253 on 2014-08-30
Many thanks for taking the time to reply to this CaptainMark.

Yes, this was indeed a permissions problem. I had failed to appreciate the subtleties of ext4 (compared to FAT etc) when moving drives between machines. After reading a few sources, inc. the one you suggested, I am now slightly less of a beginner!

Thanks again,

Ben

---

