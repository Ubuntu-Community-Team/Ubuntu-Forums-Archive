---
title: "Using Putty for serial connection to a router or switch."
date: 2015-02-14
forum: General Help
---

### Post by diddy2 on 2015-02-14
Hello, 

I am trying to use Putty to connect to a Cisco router via a serial connection. This is to
configure the router out of the box. Security is not a problem until it is connected to a 
network. Then it will be confgured with SSH. 

Serial line: /dev/ttyUSB0 Baud rate: 9600   Data bits 8  stop bits 1

Using a Cisco USB serial cable.


When I try to connect I get this error.

Putty Fatal Error

Unable to open connection to:
Unable to open serial port

OK

Checked and it looks like it is using the correct paths.

/usr/bin/telnet

:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/loc

ls -l /usr/bin/telnet
lrwxrwxrwx 1 root root 24 Feb 13 22:14 /usr/bin/telnet -> /etc/alternatives/telnet/usr/bin/telne


I have connected via minicom. My friend uses CentOS and is able to use Putty with my 
cable.


Also tried CtkTerm. Received this message.

Cannot open /dev/ttyUSB0: Permission denied

Any help would be appreciated!!!

Thank you, 

Diddy

---

### Post by nerdtron on 2015-02-14
Have you tried using putty as root?
Also, is the /dev/ttyUSB0 the correct device for your cable?

---

### Post by diddy2 on 2015-02-14
Thank you for replying. I am not sure how to use in root? I am new. Would I open Putty from the terminal window?

---

### Post by diddy2 on 2015-02-14
Here is the usb serial cable. It is currently not connected. Just unplugged it from
my laptop. Looks that I am using the right one?

dmesg | grep tty
[    0.000000] console [tty0] enabled
[    1.025308] 0000:00:16.3: ttyS4 at I/O 0x1808 (irq = 17, base_baud = 115200) is a 16550A
[    1.267114] tty tty7: hash matches
[ 3967.041464] usb 2-1.2: FTDI USB Serial Device converter now attached to ttyUSB0
[ 9125.490026] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[10877.163472] usb 2-1.2: FTDI USB Serial Device converter now attached to ttyUSB0
[14115.666926] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0


Tried both of these combos in Putty.

/dev/ttyUSB0
/dev/usb/ttyUSB0

---

### Post by nerdtron on 2015-02-14
well if it's the correct device then try running putty as root.

```
gksudo putty
```

I think gksudo is not installed by default so you can try installing it first.
```
sudo apt-get install gksu
```

---

### Post by efflandt on 2015-02-15
Isn't PuTTY a "network" terminal client (does it even do serial directly?)? It would work for network connection to a router or switch that has ssh or telnet. I have never used PuTTY in Linux, since it has native ssh related utilities (I only use PuTTY in Windows).

I have used minicom over the years to connect to dial up modems and other serial devices, just not in recent years, so forgot most of that. To configure it you might first need to do: [B]sudo minicom -s
[/B]
Not sure what gui serial terminal programs are available, but a quick search in synaptic found **gtkterm**, so you might try installing that. If it needs to be run as root just use "gksu " (without quotes) before it.

**sudo** can be used to run things as root from terminal or for X, it is just that **gksu** does the same with a gui popup for the password.

---

### Post by diddy2 on 2015-02-15
Thank you!!! gksudo putty worked!!!! I am so glad. I need this tool and was thinking I would need to go back to windows 
for this one app.

Thank you again!!!!!

---

### Post by diddy2 on 2015-02-15
Thank you!!! I am going to try this with gtkterm. I will follow up in a bit.

---

### Post by diddy2 on 2015-02-15
This also worked. Thank you for taking the time to assist!!!!!

---

### Post by diddy2 on 2015-02-15
By chance is there a way for it to default to open without gksudo command each time?

---

### Post by nerdtron on 2015-02-15
> **diddy2 said:**
> By chance is there a way for it to default to open without gksudo command each time?

No idea on that one.

---

### Post by TeDeJeM on 2015-05-05
Finally! Running as root fixed that for me - I was getting ready to use Windows VM just for that cable thing. Thanks!

> **nerdtron said:**
> Have you tried using putty as root?
Also, is the /dev/ttyUSB0 the correct device for your cable?

---

### Post by Lars Noodén on 2015-05-05
It was probably a question of not being in the right group.  Serial devices default to rw for the group 'dialout'.  

```

$ ls -lh /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 0 May  5 13:51 /dev/ttyUSB0

```

So if your user account is a member of the group 'dialout' then you will be able to use the device with cu, putty. minicom or whathaveyou.

---

### Post by HermanAB on 2015-05-05
Next time, use Cutecom.

---

