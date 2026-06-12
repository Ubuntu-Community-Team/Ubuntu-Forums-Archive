---
title: "Internet, sound and USB not working suddenly."
date: 2014-06-19
forum: General Help
---

### Post by smuks on 2014-06-19
Hi there! I installed ubuntu few weeks ago to my wifey and it was all smooth sail till today.

Suddenly she cannot access internet, sound stopped working and ubuntu does not recognize any usb. It is quite strange to me that all of this happened at once.

I tried to solve this myself, but hopefully you can help us! Does anybody have an idea what could this be?         Best regards, I hope you have a nice day :KS

---

### Post by nerdtron on 2014-06-19
What version of ubuntu?
And please elaborate more on technical details like what applications she last used/installed, or updates installed etc.

---

### Post by Sef on 2014-06-19
Does the Live CD work?  Possibly your computer hardware is having major problems.  If the Live CD works, then it is most likely a software issue.

---

### Post by smuks on 2014-06-19
Its 14.04 Thrusty Tahr. 

She used skype, libreoffice, VLC player and downloaded some torrents of her favorite vampire serise The Originals.

I find it strange. Because everything else seems ok. Just the sound not working at all, also no wireless nor cable if plugged and also if I put USB in, no action as well (I've booted live linux on the same comp, everyth. worked fine).

Its a bit tough one, I cannot figure what it is, tried to change sound and networtk settings, no improvement.

---

### Post by jjclonker on 2014-06-19
If you haven't shut down and restarted I would try that first.

---

### Post by smuks on 2014-06-19
oh sure, we restarted some times. I've put it on System test right now. Anybody has an idea what could this puzzle be?  :)

---

### Post by jjclonker on 2014-06-19
For starters I would push ctl+alt+t that will open a terminal then type "dmesg" into the terminal without the quotes.

Then post the results here.

I am not expert, but this should give them a place to start. ;)

---

### Post by smuks on 2014-06-19
Thanks for input. I have a slight problem of how should i copy/paste the text after "dmesg", because usb is not recognized nad 'net doesnt work..  :(

---

### Post by smuks on 2014-06-20
bump. Still havent figured:(

---

### Post by jjclonker on 2014-06-20
Is your computer recognizing your mouse (If you have one) or is it not recognizing any usb device?

---

### Post by Bucky Ball on 2014-06-20
Welcome. Please only bump your posts every twenty four hours. Also, to improve your chances of help, I have changed the title of your thread to something describing your problem.

Generic thread titles like 'Help please' don't generally get you much help. The majority of people here want help, so please describe what you want help with in your title (you might want to have a look at the third link in my signature to increase your chances of getting support here). ;)

Did you do an update/upgrade prior to this happening? You didn't mention it so I'm thinking not. What were you doing when this happened? Was the computer behaving normally and then things went wrong or did you restart it and the problems were there or did you install a program and then it happened? Can you think of anything?

---

### Post by smuks on 2014-06-20
It is not recognizing just usb flash disks, mouse is working. This is so strange.

---

### Post by Bucky Ball on 2014-06-20
Could you plug one in, open a terminal and enter this, then press return:

```
lsusb
```

Please post the output here. You should be able to see the USB dongle at least plugged in in the output.

---

### Post by smuks on 2014-06-20
I've reinstalled Ubuntu. Thanks for help Linux community! :)

---

### Post by Iowan on 2014-06-20
Hopefully your problem went away...

---

