---
title: "com port? serial?"
date: 2007-04-25
forum: General Help
---

### Post by sivel27 on 2007-04-25
hello everyone.

i cant seem to figure this one out.

im trying to see if my com port is recognized/works in feisty. is there a command i an type
to test the com port out? in my bios, the port is enabled.

my main goal is to control a fta reciever [pansat 2700] via the serial cable for mythtv.


thanks in advance,

sivel27

p.s-

i bought a straight throughrs232 cable, as the cable it comes with is a null modem cale.

---

### Post by Skrynesaver on 2007-04-25
```
statserial
```part of the universe/utils and not installed by default, so enable universe repositries apt-get and Robert is your mothers brother

---

### Post by sivel27 on 2007-04-25
allrighty, 

i installed and ran it, and this is what i got:


statserial: TIOCMGET failed: Input/output error


any ideas?


thanks,
sivel27

---

### Post by Skrynesaver on 2007-04-25
Have you a device attached and turned on ?

---

### Post by sivel27 on 2007-04-25
> **Skrynesaver said:**
> Have you a device attached and turned on ?



yes i do, 

i have my pansat fta reciever connected to the comp via serial cable.


thanks,
sivel27

---

### Post by bernied on 2007-04-25
I haven't tried this stuff for a while, but I think [minicom](http://alioth.debian.org/projects/minicom/) is the standard serial terminal program. You could use this to see if you can talk to your device.

I found this [here](http://www.vanemery.com/Linux/Serial/serial-console.html):
> Step 1: Check your system's serial support

First, let's make sure that your operating system recognizes serial ports in your hardware. You should make a visual inspection and make sure that you have one or more serial ports on your motherboard or add-in PCI card. Most motherboards have two built-in ports, which are called COM1: and COM2: in the DOS/Windows world. You may need to enable them in BIOS before the OS can recognize them. After your system boots, you can check for serial ports with the following commands:

[root@oscar root]# dmesg | grep tty
ttyS0 at 0x03f8 (irq = 4) is a 16550A
ttyS1 at 0x02f8 (irq = 3) is a 16550A

[root@oscar root]# setserial -g /dev/ttyS[01]
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3

As you can see, the two built-in serial ports are /dev/ttyS0 and /dev/ttyS1. 

EDIT: I was a bit slow answering the original post - feel free to ignore...

---

### Post by sivel27 on 2007-04-25
> **bernied said:**
> I haven't tried this stuff for a while, but I think [minicom](http://alioth.debian.org/projects/minicom/) is the standard serial terminal program. You could use this to see if you can talk to your device.

I found this [here](http://www.vanemery.com/Linux/Serial/serial-console.html):


EDIT: I was a bit slow answering the original post - feel free to ignore...



ok, i did as you suggested, and heres what i got:


sivel@media:~$ dmesg | grep tty
[   15.415777] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.415993] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   15.416326] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.416494] 00:0a: ttyS2 at I/O 0x3e8 (irq = 0) is a 16550A

and heres the setserial output:

sivel@media:~$ setserial -g /dev/ttyS[01]
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3


now, on this motherboard i only hav 1 com port. reading the output of the commands, does it look ok?


thanks,
sivel27

---

### Post by bernied on 2007-04-25
It looks right to me. I would say that your serial port is /dev/ttyS0

Have you tried talking to your device with minicom? It's not the easiest program to use, but the documentation is there somewhere (I think).
Try 'man minicom' for instructions.

---

### Post by sivel27 on 2007-04-26
> **bernied said:**
> It looks right to me. I would say that your serial port is /dev/ttyS0

Have you tried talking to your device with minicom? It's not the easiest program to use, but the documentation is there somewhere (I think).
Try 'man minicom' for instructions.


ok, so i installed mnicom, and ran the config file as far as to set 
the dfault serial port, however, im lost as to what to do next
in it, as far as issuing commands.


i also installed the newest version of vmware server on it with win xp pro
installed. as far as the hardware goes, i was under the impression that
the guest os in vmware can use only the hardware that is detected by the
host os. when i tried to use a program to update the firmware for the STB
in windows, it gives me a can not connect type of error.


now, using that sme program on my other hdd, which has winxp installed, the 
software that communicates with my STB works well. im lost as to wether or
not ubuntu is in fact recognizing my serial/com port.



thanks in advance,

sivel27

---

### Post by imasickboy on 2007-05-01
I've been trying to figure this one out, myself. So far, no one anywhere that I've found has been able to do anything with a FTA receiver with either linux or Mac. I have tried running under wine, and tryed the vmware option as well, with your same results. I intend to keep looking for an answer, though.

If I knew what .dll's the software used, I would try replacing those in wine with native ones, but I really don't want to replace them all, but I'll likely end up trying that at some point anyway.

Good luck to you.

---

### Post by imasickboy on 2007-05-21
I've finally acheived flashing a new .bin to my Pansat 2500, something I haven't seen anyone else do under Linux. I've seen some success with the Viewsat's recently, but never a Pansat before. I'm thrilled, and will explain tomorrow, because it's late, and I'm exhausted.

There's hope for your issue yet!

Edit:

Here's what I have:

Pansat 2500

Goal:

Flash new .bin to the Pansat. Windows loader won't download to receiver when used in WINE.

Solution:

Install Minicom and lrzsz, both easily found using Synaptic.

Follow these instructions for settings changes in Minicom, (provided by _Blackie_ at curious-contraptions.com):

1.Open a terminal and become root with the SU command and supply password when prompted.

2.)Type minicom to open the application. Once started, type ctrl-a then type o to enter the settings menu. Settings should be as follows, keeping in mind that the paths and filenames will be dependent on your system.
A.) Filenames and paths:
&#9474; A - Download directory : /home/username/
&#9474; B - Upload directory : /home/username/
&#9474; C - Script directory :
&#9474; D - Script program : runscript
&#9474; E - Kermit program :
&#9474; F - Logging options

B.)File transfer protocols:
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
&#9474; Name Program Name U/D Fu
&#9474; A zmodem /usr/bin/sz -vv -b Y U
&#9474; B ymodem /usr/bin/sb -vv Y U
&#9474; C xmodem /usr/bin/sx -vv Y U
&#9474; D zmodem /usr/bin/rz -vv -b -E N D
&#9474; E ymodem /usr/bin/rb -vv N D
&#9474; F xmodem /usr/bin/rx -vv Y D
&#9474; G kermit /usr/bin/kermit -i -l %l -s Y U
&#9474; H kermit /usr/bin/kermit -i -l %l -r N D
&#9474; I ascii /usr/bin/ascii-xfr -dsv Y U
&#9474; J -
&#9474; K -
&#9474; L -
&#9474; M Zmodem download string activates... D
&#9474; N Use filename selection window...... Yes
&#9474; O Prompt for download directory...... No






C.) Serial Port Setup: For com1 service
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
&#9474; A - Serial Device : /dev/ttyS0
&#9474; B - Lockfile Location :
&#9474; C - Callin Program :
&#9474; D - Callout Program :
&#9474; E - Bps/Par/Bits : 115200 8N1
&#9474; F - Hardware Flow Control : No
&#9474; G - Software Flow Control : No
&#9474;
&#9474; Change which setting?
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

All other settings can be left at default for our purposes with this project.Once you have all your settings configured properly, navigate down and highlight to Save setup as dfl and hit enter to save as your default settings.Then Exit.

Now, the interesting part. For anyone using a Viewsat, the following is said to work, though it does not for my Pansat:

3.) Now you have minicom configured we can go ahead and send whatever files we need to the unit. Type ctrl-a and then S to start the send process. Select Zmodem from the list and hit Enter. Select the file you wish to send navigating to it and use the space to select and then Enter to start the process.
Turn the viewsat off, then on, with the power switch on the back and the transfer will start.
Once complete, hit ctrl-a and then X to exit.

For my Pansat, WITH MINICOM OPEN, I then used the Windows loader and it immediately connected and downloaded the file to the receiver. Problem solved, (for me anyway).

I think for your question, you would likely need minicom installed and set up, and lrzsz installed, and MythTV should easily then be able to talk to your Pansat via serial cable.

I really hope this helps you. Good luck and keep me posted, as I'd like to use MythTV with my Pansat also sometime.

---

### Post by hotweiss on 2007-09-26
Can someone help me?

With dmesg | grep tty I get this:

> 
[ 1777.600000] usb 5-3.2: pl2303 converter now attached to ttyUSB0

So my serial port is ttyUSB0. Fine, but when I use setserial, I get this:

> setserial -g /dev/ttyUSB0
Cannot get serial info: Invalid argument

Does anyone have any ideas?

---

### Post by hotweiss on 2007-09-27
bump

---

### Post by hotweiss on 2007-09-27
Problem solved, I had to reset and bind ttyS0 with ttyUSB0:

> 
sudo rm /dev/ttyS0
sudo ln -s /dev/ttyUSB0 /dev/ttyS0

---

### Post by corte123 on 2007-11-19
I just tried this with my pansat 2700a ,works great!  much thanks to the poster :)

---

