---
title: "Syntax errors related to tty USB command lines"
date: 2013-08-27
forum: General Help
---

### Post by robert22 on 2013-08-27
Need help figuring out the error messages after i entered a command line

Under the directory:

/usr/local/bin $ 

There is a application called "modem diagnostics" that I am trying to run by using the following command

 /usr/local/bin $ sudo modem-diagnostics 169.254.51.159 --export_device=/dev/ttyUSB1 --noconfigure_interface

instead of running the application I get the following messages.

1) /usr/local/bin/modem-diagnostics: 1: modem-diagnosticsC:HP: not found
2) /usr/local/bin/modem-diagnostics: 47: Syntax error: end of file unexpected (expecting "fi")

I typed $ lsusb and the followign showed up

Bus 001 Device 026: ID 0b95:772a ASIX Electronics Corp. AX88772A Fast Ethernet
Bus 001 Device 018: ID 0bda:5776 Realtek Semiconductor Corp
Bus 001 Device 020: ID 0cf3:311e Atheros Communications, Inc.
Bus 001 Device 021: ID 12d1:1570 Huawei Technologies Co., Ltd.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

Does anyone have an idea why im getting these syntax messages above? And what i need to do to make the command "  sudo modem-diagnostics 169.254.51.159 --export_device=/dev/ttyUSB1 --noconfigure_interface" go through successfully?

Why am i doing all of this?

I have two notebooks. One is the server the other is the client. The modem diagnostics app sits on the client side and is suppose alert/awaken the server that it is ready for commands to control it from the server side. So in other words the modem diagnostics that sits on the client side allows the server to control it and I can do certain things on the client via the server side.

I know the server and client are talking because i can ping each other in either direction. Thanks to a free virtual serial port configuration utility. server IP is 169.254.51.130, client IP is 169.254.51.160, both have the same mask.

The connection between the server and client notebooks is ethernet with the exception that the client notebook does not have a ethernet port just USB so oi had to use a USB to ethernet adapter on the client side.

---

### Post by steeldriver on 2013-08-28
What is modem-diagnostics, and where did you get it? if it's throwing an error at line 1 that suggests it's a corrupted script

---

### Post by robert22 on 2013-08-28
> **steeldriver said:**
> What is modem-diagnostics, and where did you get it? if it's throwing an error at line 1 that suggests it's a corrupted script

modem-diagnostics is a just an specific application. The application allows a server to control the client notebook via a virtual serial port.

Is line 1 error saying something is wrong with the script or is something wrong with my [COLOR=#000000]/dev/ttyUSB1 configuration?[/COLOR]

---

