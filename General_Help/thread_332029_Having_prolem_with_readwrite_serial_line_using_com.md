---
title: "Having prolem with read/write serial line using communication tool"
date: 2007-01-05
forum: General Help
---

### Post by instcode on 2007-01-05
Hi all,

I'm using Ubuntu 6.10 Egdy Elf Desktop version but I can't get the serial works anymore.
It seems that there's no stranger with my serial port:
```

instcode@hell:~$ cat /var/log/dmesg | grep tty
[17179571.132000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.136000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

instcode@hell:~$ setserial -g /dev/ttyS[01]
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4

instcode@hell:~$ cat /proc/tty/drivers 
/dev/tty             /dev/tty        5       0 system:/dev/tty
/dev/console         /dev/console    5       1 system:console
/dev/ptmx            /dev/ptmx       5       2 system
/dev/vc/0            /dev/vc/0       4       0 system:vtmaster
rfcomm               /dev/rfcomm   216 0-255 serial
serial               /dev/ttyS       4 64-111 serial
pty_slave            /dev/pts      136 0-1048575 pty:slave
pty_master           /dev/ptm      128 0-1048575 pty:master
pty_slave            /dev/ttyp       3 0-255 pty:slave
pty_master           /dev/pty        2 0-255 pty:master
unknown              /dev/tty        4 1-63 console

instcode@hell:~$ stty -a
speed 38400 baud; rows 53; columns 157; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = M-^?; eol2 = M-^?; swtch = M-^?; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R; werase = ^W;
lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread -clocal -crtscts
-ignbrk brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff -iuclc ixany imaxbel iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt echoctl echoke

instcode@hell:~$ ls -la /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 2007-01-05 23:53 /dev/ttyS0

instcode@hell:~$ groups
instcode adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

```

... But I don't know why I can send/receive any data using communication tools such as: minicom, gtkterm, uucp-cu...

Note: This serial port works well with Hyper-Terminal of Windows OS.

Anyone experienced this problem, please help me :)

---

