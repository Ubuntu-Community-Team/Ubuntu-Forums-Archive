---
title: "can not find bluetooth devices"
date: 2007-01-06
forum: General Help
---

### Post by Choad on 2007-01-06
i have all the bluetooth stuff installed, and when i turn on gnome-bluetooth, i can send things to my laptop, but when i right click a file and send it, it never detects any bluetooth devices.

any help?

im running ubuntu edgy

---

### Post by Choad on 2007-01-09
bump

please help!

---

### Post by vedanuzal on 2007-01-09
I am having the same problem but under dapper it worked fine.  Where has the bluetooth manager gone?

I can discover devices using the command line but a working gui would be nice and i don't want to add all the devices i use at work (about 50 mobile phones) to the config file.

I hope removing the bluetooth manager wasn't done deliberately cause that would be a bad idea cause discovering of devices takes time and doing that each time you want to send a file is a waist of time.

---

### Post by defishguy on 2007-01-09
I haven't figured out a long term solution but I have gotten it to work when I need it  by typing the following in a terminal window

> sudo hcid

After you do that test it by turning on your device and typing

> hcitool scan

You should see the mac address of your device show up.

I don't transfer files often enough to make a permanent fix.  Possibly someone smarter than me can offer a better solution!

---

### Post by vedanuzal on 2007-01-09
Yeah since found this bug

[https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718]("https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718")

So its a known problem and happens with kdebluetooth as well but it doesn't seem a high priority to fix.

But considering the commandline tools work it should be a simple fix ie ~ couple of hours for some one who know the code, if it has been written well.

---

### Post by Choad on 2007-01-10
```
richard@richard-laptop:~$ sudo hcid
Password:
richard@richard-laptop:~$ sudo hcitool scan
Scanning ...
        00:17:D5:58:21:DB       Rich phone
richard@richard-laptop:~$ 

```

it works, but how can i send a file now?

---

### Post by vedanuzal on 2007-01-12
got it sending files using obexftp which i had to apt-get

first i had to pair with the computer (default PIN was 1234 i think)

then used *obexftp -b bluetooth address  -p file*

if they don't fix this soon should be simple to write a script for this.

---

### Post by wolfchri on 2007-01-13
Just add Marcels workaround to /etc/rc.local in order to get rid of this problem without having to jump to the command line every time.

See my /etc/rc.local as a example:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# to detect the card reader on the HP NX6325
setpci -s 02:04.2 4c=0x22

# to work around the nasty bluetooth bug in Edgy 
hciconfig hci0 inqmode 0

exit 0
```

---

### Post by Choad on 2007-01-13
you, sir, are a legend!!!

where did you find that tip?

---

### Post by wolfchri on 2007-01-13
Choad,

just have a look at Marcel Holtmanns postings on the Launchpad bug report for this issue (at the bottom):

[https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718](https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718)

Hopefully, the issue gets fixed with the next Gnome release, but I am not really sure about this. 

Essentially, Bluetooth is currently halfway broken on Ubuntu/Debian, but obviously, developers do not consider this a major issue. To me, it is a major bug that could easily be fixed or at least worked around (just switching back to the old inquiry mode in one of the init scripts). Lets see.

---

### Post by wolfchri on 2007-01-13
Choad,

just have a look at Marcel Holtmanns postings on the Launchpad bug report for this issue (at the bottom):

[https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718](https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718)

Hopefully, the issue gets fixed with the next Gnome release, but I am not really sure about this. 

Essentially, Bluetooth is currently halfway broken on Ubuntu/Debian, but obviously, developers do not consider this a major issue. To me, it is a major bug that could easily be fixed or at least worked around (just switching back to the old inquiry mode in one of the init scripts). Lets see.

---

