---
title: "Can't shut off internet connection..."
date: 2005-09-29
forum: General Help
---

### Post by djheadley on 2005-09-29
I'm running Hoary on an NEC 433 with 256M RAM with a US Robotics external modem.  I have to use NetZero as my ISP, at least for now and I FINALLY got the program to work. I can connect OK but how do I disconnect?

After I find out how to do this then I have a couple of other internet related problems to fix then I'll be free from MS!!!!!

djheadley

---

### Post by heimo on 2005-09-29
It's dialup modem, right? Have you seen this:
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

If you're using pon to connect, use poff to disconnect.

---

### Post by djheadley on 2005-09-29
I don't use pon and poff, I have to use NetZero's software which is run from a bash script. I tried poff but it didn't work.  Would it help to see the script?

#!/bin/sh

cd /opt/nzclient

cp=./lib/zcast1_6.jar:./lib/bwt300.jar

java -cp $cp -Dnz.browser=mozilla -Dnz.clientName=$0 -Dnz.RAS=./nzppp -Dnz.rasdelay=60000 -Dnz.TextFontName=SansSerif -Dnz.TextFontSize=7 -Dnz.FontName=Arial -Dnz.FontSize=9 nzcom.ZCast

The only thing I added was to link the modem - it wasn't being done at boot-up.

djheadley

---

### Post by heimo on 2005-09-29
Ok, I don't know anything about this netzero, but have your checked if you have other scripts under: /opt/nzclient? If I couldn't get it working, I'd probably just switch off my external modem... :) If applications don't get mad about it. Or try to use the guide I linked above. :-/

---

### Post by Ruddigger on 2005-09-29
you can also check what processes are running with ps and then kill it...

---

### Post by djheadley on 2005-09-29
NetZero is one of those free/cheap ISPs that you have to use their software in order to get online.  If I could afford a "regular" ISP I would dump them in a minute.  The Linux software is supported for Linspire only.  I have been just turning off the modem but I would like to be able to "properly" shut this program off and disconnect.

Oh well, I geuss I'll just have to live with it for now and concentrate on my other problems.

Thanks for you really quick replies :) 

djheadley

---

### Post by djheadley on 2005-09-29
I didn't know how to list running processes.  Then how do I kill it?

djheadley

---

### Post by heimo on 2005-09-29
You can try something like
```
ps aux | grep nzclient | grep -v grep
``` or substitute the end (|grep nzclient ...) with |less to list everything. If you see nzclient as a process, you should be able to kill it using killall nzclient

---

### Post by puter on 2005-11-26
I just turn of the  mdm power switch !!!

---

### Post by djheadley on 2005-11-27
That's what I usually do.  I just thought there might be a more elegant way.
:lol:

---

