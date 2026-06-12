---
title: "Connection to Siemens cellphone?"
date: 2005-05-31
forum: General Help
---

### Post by niels on 2005-05-31
I have a Siemens cellphone and a USB data cable. In windows I have no problems connecting the cellphone to the computer with the following software. After my intallation of Ubuntu, I miss this feature.
I have found the programs scmxx and obexftp which sould do it, but it doesent work. I know and graphical version of obexftp exist, but I can't find it.

Does anyone know thees programs?

Niels

---

### Post by burlap on 2005-06-09
I have succeeded with obexftp (but custom compiled) and irda, I don't have a cable yet. Mounting siefs and gnome-phone-manager also work. Multisync works partially. 

What kind of cable do you have? (generic, original Siemens)

What does ```
tail -f /var/log/messages
``` show, when you plug in cable/phone?

---

### Post by kamstrup on 2005-08-22
The following thread might be helpful... Provided somebody finds a way to get SieFS working...

[http://www.ubuntuforums.org/showthread.php?t=14448](http://www.ubuntuforums.org/showthread.php?t=14448)

Cheers

---

### Post by burlap on 2005-08-23
[quote=kamstrup]Provided somebody finds a way to get SieFS working...[/quote]
Done, see [http://www.ubuntuforums.org/showthread.php?p=314519#post314519](http://www.ubuntuforums.org/showthread.php?p=314519#post314519)

---

