---
title: "HP 900 Inkjet Printer drivers needed"
date: 2007-07-18
forum: General Help
---

### Post by berniedd on 2007-07-18
I recently installed Feisty on a Sempron set-up and now need printer drivers for an HP 900 Inkjet. I've gone to the HP website but didn't find the specific drivers I was looking for. Can you guys point me to the right direction/links? Thanks in advance.

---

### Post by Sef on 2007-07-18
Have you tried System > Administration > Printing > (don't click install, but click foward when you get to that menu.)

---

### Post by berniedd on 2007-07-18
Yes, I tried that route, but the HP 900 Inkjet model is not among those listed.

---

### Post by rbmorse on 2007-07-18
Check and see if the package

hplip

is installed. It should be listed under the system menu, otherwise install it from a terminal window with

sudo apt-get install hplip

Once that is complete, run the hp-setup utility either from the menu or from the terminal

sudo hp-setup

select "install new printer" from the menu and follow the prompts.

---

### Post by berniedd on 2007-07-19
rbmorse, thanks for the tips. From Terminal,  I ran sudo apt-get install hplip and got a message that the latest hplip is already installed. Next I ran sudo hp-setup but got a return message that said command not found. What should I do next?

---

### Post by phidia on 2007-07-19
One of the best sources for linux printing is [www.linuxprinting.org](www.linuxprinting.org)
The list for hp printers is [here]("http://openprinting.org/printer_list.cgi")
Unfortunately I don't see a 900 listed does your printer have another designation like deskjet 900?

---

### Post by rbmorse on 2007-07-19
> **berniedd said:**
> rbmorse, thanks for the tips. From Terminal,  I ran sudo apt-get install hplip and got a message that the latest hplip is already installed. Next I ran sudo hp-setup but got a return message that said command not found. What should I do next?

Odd.  Plan "B" is to open a user level terminal window and try

hp-toolbox

from there select device > setup new device from the toolbox menu.

---

### Post by berniedd on 2007-07-19
You're right. The HP 900Inkjet is not listed there. Unfortunately, it's really a 900 Inkjet Printer (exactly what's printed on the driver disk for Windows it came with and the front panel of the device as well), not a Deskjet 900. 

I tried the sudo hp-setup again and this is what came up:

error: PyQt not installed. GUI not available. Exiting.
error: PyQt init failed. Reverting to interactive mode.
error: No devices found.
error: Error occured during interactive mode. Exiting.

Next I tried the hp-toolbox command and I got the message:
 
error: PyQt not installed. GUI not available. Exiting.
error: PyQt/Qt initialization error. Please check install of PyQt/Qt and try again.

Sigh. I may be just tempted to install Windows on this box. 

BTW, are the commands the same if I were trying this on a Dapper Drake setup? Regards.

---

### Post by phidia on 2007-07-19
The resource I posted about previously has an install guide for a [HP 910]("http://openprinting.org/show_printer.cgi?recnum=HP-910") it's basically the same method you've been following-there are other info sources there too.

---

### Post by kloudy on 2007-08-17
OK, I found the printer designation I needed.  I highlighted it.  If I click "Install Drivers", where are they located?

Thanks.

:popcorn:

---

### Post by hiramabiff on 2007-12-10
I also have the same issue...  the only difference is that I dont have the printer yet.... but will be buying it anyways....  I have to rely on my current MS OS....  However, I still need help with the Linux driver for the said printer...  the reason?  I want to start a new life w Linux!:)

---

### Post by clemrasul on 2008-07-02
HP Inkjet 900 is compatible with the "910" selection under HP.

---

