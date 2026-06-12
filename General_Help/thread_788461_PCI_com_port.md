---
title: "PCI com port"
date: 2008-05-09
forum: General Help
---

### Post by Maky001 on 2008-05-09
Hi,
have a litle prob and need help.
So here it is
i have 1 comport on motherboard and 2 PCI cards with 2 comports each so in this moment have 5 comports but i can use only 4 comports .
The comport 5 aint working and tried already with other PCI card so it isnt prob with them.
Maybe its default cause i read somewhere that by default it has only 4 comports alowed in Ubuntu.
So please if any of you have solutions for this would be great.
THX in advance....

---

### Post by Maky001 on 2008-05-13
Anyone can help please.
As i said i have one comport on MB and 2 PCI cards each have 2 comports so in total its 5 but i can only get 4 to work.
I read about setserial but can anyone tell how to excatly do it without screwed up previous settings just to add comport5(ttyS4).

THX!!!!

---

### Post by DjangosClouds on 2008-08-12
Hi,
   I don't know if you're still watching this thread but I've just solved a very similar problem.

This can be tricky to do so I’m giving an example instead.
The Motherboard has one built-in serial port and I have fitted two dual serial cards, the OS names the ports /dev/ttyS0 to /dev/ttyS3 but one remains unnamed.
The first thing is to find out the details of the existing ports.
```
dmesg | grep ttyS
```
This returns this:
```
[    1.096195] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.096511] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.096677] 0000:05:02.0: ttyS1 at I/O 0xd000 (irq = 18) is a 16550A
[    1.096765] 0000:05:02.0: ttyS2 at I/O 0xd100 (irq = 18) is a 16550A
[    1.096860] 0000:05:04.0: ttyS3 at I/O 0xd600 (irq = 19) is a 16550A
```
Looking at this we can see that the address for each port changes by 0x100 (0xd100 - 0xd000 is 0x100, etc.)so we can guess that ttyS4 will need to be at 0xd700 (0xd600 + 0x100) on IRQ 19.

We use that information.
Create the file “/etc/init.d/extraserial.sh” with these contents:

```
#!/bin/sh

case "$1" in
  start)
    sudo mknod /dev/ttyS4 c 4 64
    sudo chgrp dialout /dev/ttyS4
    sudo chmod 660 /dev/ttyS4
    sudo setserial /dev/ttyS4 irq 19 port 0xd700 autoconfig
esac

exit 0
```

Note 1: You must change the port and IRQ to match the ones we discovered earlier.
Note 2: This adds 1 extra port, to add more copy everything between “start)” and “esac” for each extra device required.

Now make sure the file is executable (sudo chmod +x /etc/init.d/extraserial.sh) 

Next we run:
```
update-rc.d extraserial.sh defaults
```

This creates links in the correct place for the file to be executed when the system starts up.

As I said, this worked for me. I've spent a whole day working it out. Hope it helps you.

---

