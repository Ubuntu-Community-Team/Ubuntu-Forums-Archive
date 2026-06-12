---
title: "[SOLVED] +4 serial ports"
date: 2008-05-22
forum: General Help
---

### Post by erikthijs on 2008-05-22
Hi,

I have ubuntu server 8.04 64bit installed on a Dell poweredge server. Purpose of the server is to monitor APC ups devices throug serial port connections. I added a 4-port serial card to the server that already contains an integrated serial port. After hardware installation, only devices ttyS0 to ttyS3 are available, so one serial port is missing... I read somewhere that a kernel recompilation would be necessary to support over 4 serial ports. Can somebody confirm this, or is there another solution to this problem?

tnx!

---

### Post by erikthijs on 2008-05-23
Problem solved:

check number of supported and activated serial ports in kernel config:

# grep UARTS /boot/config-2.6.x-y-server
CONFIG_SERIAL_8250_NR_UARTS=48
CONFIG_SERIAL_8250_RUNTIME_UARTS=4

To increase the number of serial ports activated, change grub configuration. The line starting with kernel ... should be modified to include the number of serial ports to activate:

kernel /vmlinuz-2.6.x-y-server ... [COLOR="Red"]8250.nr_uarts=8[/COLOR]

Reboot, and check number of serial ports:

#cat /proc/tty/driver/serial
serinfo:1.0 driver revision:
0: uart:16550A port:000003F8 irq:4 tx:0 rx:0
1: uart:unknown port:000002F8 irq:3
2: uart:unknown port:000003E8 irq:4
3: uart:unknown port:000002E8 irq:3
4: uart:16550A port:0000BCE0 irq:16 tx:0 rx:0
5: uart:16550A port:0000BCE8 irq:16 tx:0 rx:0
6: uart:16550A port:0000BCC0 irq:16 tx:0 rx:0
7: uart:16550A port:0000BCC8 irq:16 tx:0 rx:0

thanx to the serial howto on tldp.org :)

---

