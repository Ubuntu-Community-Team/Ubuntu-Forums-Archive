---
title: "Serial port found, but not sending or reciving data"
date: 2017-06-01
forum: General Help
---

### Post by vnikolaas on 2017-06-01
Hello all! I have been having trouble with my serial port on my ubuntu server 16.04 machine. First off its a lenovo thinkcentre M-57 model 6071, and here is the output of uname -a:
```
Linux server 4.4.0-78-generic #99-Ubuntu SMP Thu Apr 27 15:28:22 UTC 2017 i686 i686 i686 GNU/Linux
```
So here is the deal, this machine has a serial port on the motherboard, and I am trying to use it with my modem. The serial port is recognized by the system as ttyS4, and I can even enter a screen session on that port, but when I start typing no data is sent to my modem (My modem has an analog loopback feature so that it will return everything typed back to the terminal, and this has worked on other computers) and no data is received either, it acts as though I am not sending data to the right port, but this is the only physical port detected. The serial port is providing some current, because when I connect my modem to it, the DTR light comes on. So here is some more information:
```
nikolai@server:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    0.987516] 0000:00:03.3: ttyS4 at I/O 0x1c90 (irq = 17, base_baud = 115200) is a 16550A

```
```
nikolai@server:~$ sudo setserial -g /dev/ttyS[0123456]
[sudo] password for nikolai: 
/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
/dev/ttyS4, UART: 16550A, Port: 0x1c90, IRQ: 17
/dev/ttyS5, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS6, UART: unknown, Port: 0x0000, IRQ: 0
```
```
nikolai@server:~$ stty -F /dev/ttyS4 -a
speed 9600 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>;
eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
werase = ^W; lnext = ^V; discard = ^O; min = 1; time = 0;
-parenb -parodd -cmspar cs8 hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr -icrnl -ixon -ixoff
-iuclc -ixany -imaxbel -iutf8
-opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
-isig -icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt
echoctl echoke -flusho -extproc


```
I'm pretty stumped on this one, I hope one of you out there can help me out. I went ahead and ordered a pci serial port card, but that's coming from China so it'll take a month. Meanwhile I'd like to get to the bottom of this, I'm hoping it's not a driver issue. Thanks in advance.

---

