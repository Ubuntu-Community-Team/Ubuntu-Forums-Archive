---
title: "Unable to connect to printer"
date: 2007-05-16
forum: General Help
---

### Post by ronald_stall on 2007-05-16
I have two computers setup in my home. Both have Feisty. I have an HP Photosmart on one of them. One I have a dual boot with WinXP installed. When I setup my printer for WinXP to print to the other computer with the printer also on Feisty it finds the printer fine but when I try to print I get an error in WinXP that it is unable to connect, access denied. Can anyone give me some insight. I can print to this printer from the same computer when running Feisty just not WinXP. I am using smb.

---

### Post by mitch.c on 2007-05-16
> **ronald_stall said:**
> Can anyone give me some insight. I can print to this printer from the same computer when running Feisty just not WinXP. I am using smb.
I assume that means you are trying to print using samba on Feisty. Look, when it comes to printing from Win XP to Ubuntu, the easiest way by far is IPP. If you need samba for file sharing, or to support a larger Windows network, then use it. If you want pain-free printing (IMHO), make it easy on yourself and follow the link in my sig below.

-- 
Mitch

---

### Post by ronald_stall on 2007-05-17
Tried this but now in the access log for cups I get this

```
192.168.1.105 - - [17/May/2007:11:09:10 -0500] "POST /printers/Photosmart_C3100 HTTP/1.1" 200 75 windows-ext client-error-bad-request
```

in error log get this
```

E [17/May/2007:11:09:10 -0500] Missing printer-uri or job-uri attribute!
```

any ideas?

---

### Post by mitch.c on 2007-05-17
Did you delete the original Win XP printer you set up using samba? It looks to me like it might still be printing over smb.

Delete the printer and recreate. Make sure you select Network Printer and use a URL like:
```
http://your_server:631/printers/your_printer
```
This has always worked flawlessly for me. I have both a PhotoSmart 1000 and a LaserJet 1300 on an Edgy machine.

---

### Post by ronald_stall on 2007-05-18
When you say delete the original WinXp printer you do mean the one I installed in WinXP trying to print to the Feisty box printer right.? I have done so. and used the URL [http://192.168.1.100:631/printers/Photosmart_C3100](http://192.168.1.100:631/printers/Photosmart_C3100) which is the address that works fine if I boot up Feisty on my dual boot box it will print there just not if I use WinXP. Hmmmmm?

---

