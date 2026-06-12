---
title: "Printer sharing"
date: 2008-05-29
forum: General Help
---

### Post by feest on 2008-05-29
i want to have an ubuntu machine with a printer sharing the printer in a network for ubuntu machines and windows machines

printer<--ubuntu<--+-->windows

however in the printer configuration program i couldn't find anything about printer shares. how do i share my printer in ubuntu so that windows machines can use the printer (without installing extra non-driver software)

---

### Post by itaintover on 2008-05-29
I just shared my printer connected to my ubuntu laptop, so it can be accessed using XP machines. Just follow this tutorial like I did. Works perfectly.
[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

---

### Post by feest on 2008-05-30
thanks for you reply, i will have a look at it as soon as possible

---

### Post by lolwhites on 2008-05-31
I've tried this tutorial and I can't get the Windows PC to see the printer. When I try typing the URL into the right box in Windows I just get a "Could not connect" error message. Typing *http://<hostname>:631/printers/* into my browser brings up a 403 error. When I try to browse to my own printer on the network I am asked for the system password, which it promptly ignores!

Is the hostname the same as "Location" in the Printer configuration box? Is the printer name the same as the device URI in the Printer configuration box? How do I find the printer's address on the system?

---

### Post by plucky on 2008-05-31
> Is the hostname the same as "Location" in the Printer configuration box?


No the <Hostname> should be the inet address of the machine the printer is connected to.In a terminal on the machine the printer is connected to type ```
ifconfig
``` will show you the inet address.

So the line for the internet browser becomes ```
http://192.168.0.4:631/printers
``` should open the cups interface.


Good Luck

---

### Post by lolwhites on 2008-05-31
Thanks plucky, I can now get the cups interface in my browser but Windows still can't connect to it. Am I getting the printer name right? The URI is *usb://EPSON/Stylus%20D68*; is that what I need to type in?

Edit: I found the correct address by opening the cups interface in my browser, right clicking on the appropriate icon and selection *Copy link location*, then pasting into a text editor. Windows then found it no problem :)

---

### Post by itaintover on 2008-05-31
Correct address should look similar to this: ```
http://**191.162.87.2**:631/printers/**Deskjet_F4100_series**
```

Offcourse this one's mine, you'll have different local ip address and printer's name if you don't have the same printer

---

### Post by feest on 2008-06-08
I've followed the instruction but no luck for me, In windows, in the printers panel the status of the printer continously is saying: 'bezig met openen'wich should mean something like 'connecting' 

when i try to go to the printer's properties the explorer crashes. 

any ideas?

---

