---
title: "help configuring serial console on uefi ubuntu server 21"
date: 2021-12-28
forum: General Help
---

### Post by nonick95 on 2021-12-28
Hello 

im trying to configure output to serial console but cant get into the username prompt

 [https://youtu.be/T7C_qcDqsc4](https://youtu.be/T7C_qcDqsc4)

```

sudo setserial -g /dev/tty*


Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
Cannot get serial info: Inappropriate ioctl for device
/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS10, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS11, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS12, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS13, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS14, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS15, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS16, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS17, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS18, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS19, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS20, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS21, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS22, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS23, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS24, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS25, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS26, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS27, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS28, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS29, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
/dev/ttyS30, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS31, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS4, UART: 16550A, Port: 0x0000, IRQ: 16
/dev/ttyS6, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS7, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS8, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS9, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyUSB0, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyUSB1, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyUSB2, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyUSB3, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyUSB4, UART: unknown, Port: 0x0000, IRQ: 0

```


my grub:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="console=tty1 console=ttyS4,115200n8"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL="console serial"
GRUB_SERIAL_COMMAND="serial --unit=4 --speed=115200"
GRUB_TERMINAL_INPUT="console serial"
GRUB_TERMINAL_OUTPUT="gfxterm serial"






# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```


i also tried with:
```
--unit=4  \ --unit=3 \ --unit=2 \ --unit=1 \ --unit=0
``` 
and also with and without this lines:
```
GRUB_TERMINAL_INPUT="console serial"
GRUB_TERMINAL_OUTPUT="gfxterm serial"
```


im booting the pc over serial i can see:
bios (can edit save ..)
grub menu (can edit)
on serial console and vga screen i see:
```
error: serial port `com4' isn't found.
error: terminal `serial' isn't found.
error: terminal `serial' isn't found.

```

after the grub menu i can see some prints on vga screen that not showing on serial console ( think its the hardware phase?)
on serial console the print coming back when Linux start to print [ ok ]  ( services phase ? )
serial console stop responding after the last print , its never get into the username prompt.
on vga i do get the username prompt

when poweroff or reboot i can see the serial console prints again till the 
```
[  OK  ] Reached target Reboot.
```

any ides why serial console stop responding ?

---

### Post by HermanAB on 2021-12-29
The very first line is already wrong:
setserial -g /dev/tty*

Setserial cannot work with a wildcard.

You are also mentioning a com4 device.  Linux is not Windows.

Consider using ssh instead - ethernet is more robust and less hassle than serial ports.

---

### Post by nonick95 on 2022-01-02
Hi , thanks for your reply
as you can see 
[COLOR=#000000]setserial -g /dev/tty*    (get)  work perfect and shows all serial on the pc

ssh is wonderful but i need serial console for this device
[/COLOR]

---

### Post by HermanAB on 2022-01-02
[https://www.kernel.org/doc/html/latest/admin-guide/serial-console.html](https://www.kernel.org/doc/html/latest/admin-guide/serial-console.html)

---

