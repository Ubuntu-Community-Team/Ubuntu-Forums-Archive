---
title: "Connecting to the Internet"
date: 2005-07-14
forum: General Help
---

### Post by Deacon on 2005-07-14
Ok, firstly let me explain that I am a complete novice when it comes to Linux. I have managed to download the Live iso, burn it to disc and get it to run on my laptop (a major achievement in my case!!).

Everything goes swimmingly until I try to connect to the internet.  I have checked in device manager and it shows that I have an ADSL usb modem connected but I have absolutely no idea how I actually get on to the net.

How do I configure my modem to connect to the net in Linux.  I am running a speedtouch ADSL modem and in Windows (sorry for swearing) I use AOL as my ISP.

If anyone could help I'd really appreciate it.

Remember I am a Linux virgin so please make your answers as simple as possible.  All idiot guides greatly received.

Many Thanks,

Deac

---

### Post by adwait on 2005-07-14
Hello!

Well, if you have to use some kind of dialer/software to connect to your ADSL account in windows, you should try running pppoeconf. To run it, in a terminal window type,

sudo pppoeconf

---

### Post by Deacon on 2005-07-14
[QUOTE=adwait]Hello!

Well, if you have to use some kind of dialer/software to connect to your ADSL account in windows, you should try running pppoeconf. To run it, in a terminal window type,

sudo pppoeconf[/QUOTE]
 Thanks for that.  Ran it but all I got was a message saying sorry unable locate.

---

### Post by adwait on 2005-07-15
That's odd.......are you sure spelled it right? Try sudo /sbin/pppoeconf. If it still gives the same error try

sudo apt-get install pppoeconf

After that try the sudo pppoeconf command again.

---

