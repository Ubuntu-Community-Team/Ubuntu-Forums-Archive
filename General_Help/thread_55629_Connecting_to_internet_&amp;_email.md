---
title: "Connecting to internet &amp; email"
date: 2005-08-09
forum: General Help
---

### Post by Chrissie on 2005-08-09
Good morning,

I've succesfully switched to Linux... but the connection doesn't seem to transmit anything.

Using: Ubuntu 5.04 / Gnome 2.10.0 / kernel 2.6.10 (dual-boot machine)
Modem: winmodem PCTel HSP56 Micromodem (bus id 134d:7891) on dev/modem
for which I downloaded the driver pctel-0.9.7-9-rht-4.tar.gz from linmodems.technion.ac.il

After 2 months of frustration of undetected modem under Mandrake, I switched to Ubuntu and the modem was finally recognized!

I entered all parameters in System>Networking and I can now connect to my ISP (only I have to reinstall the driver everyday otherwise the modem is not detected) BUT:
* when I try to browse, all addresses I enter return the message "Cannot find [www.whateversite.com](www.whateversite.com). Please check address and try again" (using Mozilla Firefox)
* when I try to download my emails in Evolution I get "Temporary failure in name resolution"
* the "Modem Monitoring" utility tells me that I am indeed connected and even monitors the length of time I am connected (to nothingness??).

I tried the alternative of using ppp and wvdial; but to no avail (though I don't really know how to configure wvdial and the man pages are not helpful).

To note:

1/ when I first installed Ubuntu I got the following errors (but it works fine, though):
* Gnome display manager not running *(what I have on the screen looks very much like gnome to me... and works just fine)*
* Don't have defomized font package *(no matter, I don't care for funky fonts)*
* Cannot load default font config file *(ditto)*
* It also advised me to run "cron" but the line scrolled too fast for me to read, so I've no idea what it is or why I have to run it.
I did not run "cron" and everything (but the net) seems to be working fine.

2/ Everytime I boot Ubuntu I get the following lines:
* Gnome display manager not running
* Temporary failure in name resolution *(YES! the very same line as above in Evolution)*.

What am I doing wrong?
I've read somewhere that I had to make sure that my ISP was Linux friendly, which I know they are are because their website & webmail welcomes us with a cute little Tux.

Thank you in advance for any help,
Christel

---

### Post by costoa on 2005-08-10
It sounds like a dns issue. When connected to the net try this from a shell:

1. ```
ping 127.0.0.1
```
Check and see if your ip stacks are up.

2. Run ifconfig and see if you have a routable ip address tied to the ppp device.


3. ```
ping 216.239.57.99
```
This is an ip address for google. If it pings you should be able to put the address in your browser and reach google.

4. ```
host google.com
```
You should see something like "google.com has address 216.239.57.99" if dns is working and "Host google.com not found" if dns is down.

also ```
cat /etc/resolv.conf
``` and post your results.

This might take a bit to fix but is quite fixable. I'll watch the thread.

costoa

---

### Post by excelsior on 2005-08-10
I have the exact same problem... since I moved to campus I can't transmit anything on my ethernet connection. The only failure I get in startup is "failed to synchronize time at ntp.ubuntulinux.org" or sumwhat like that.

---

### Post by excelsior on 2005-08-10
oops, sorry it's "failed to connect to ntp.ubuntulinu.org- temporary failure in name resolution"

---

### Post by costoa on 2005-08-10
If you're connecting to the net via a modem and getting the "failed to connect to ntp.ubuntulinu.org- temporary failure in name resolution" error its to be expected and fine. Nothing to worry about.

After you boot, connect to the net and try the steps above.

costoa

---

### Post by Chrissie on 2005-08-10
YES! YES! YES! OH Joy, oh rapture! K'Plaa at last!
You are amazing! Will you marry me?
Writing this from Ubuntu as we speak.
Forever grateful. If I win the lotto, you'll get half.
Christel

---

