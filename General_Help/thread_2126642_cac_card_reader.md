---
title: "cac card reader"
date: 2013-03-17
forum: General Help
---

### Post by canislatrans on 2013-03-17
I've been trying for days to get my elitebook 8740w cac card reader working with the latest ubuntu.[INDENT]uname -a
Linux coyote-HP-EliteBook-8740w 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
[/INDENT]

I've been googling and reading but just don't know enough to be able to figure it out.  Any help is appreciated.  My understanding is that pcsc_scan should not hang at "Waiting for the first reader..."  The cac reader is built into the laptop and I really don't know the manufacturer so don't know if it is supported or not.  Thanks for your help

when I start pcscd with: sudo pcscd --foreground --debug

and run pcsc_scan

pcsc_scan outputs the following[INDENT]PC/SC device scanner
V 1.4.20 (c) 2001-2011, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.8.3
Using reader plug'n play mechanism
Scanning present readers...
Waiting for the first reader...
[/INDENT]

pcscd output the following[INDENT]17653216 winscard_msg_srv.c:230:ProcessEventsServer() Common channel packet arrival
00000039 winscard_msg_srv.c:242:ProcessEventsServer() ProcessCommonChannelRequest detects: 5
00000018 pcscdaemon.c:93:SVCServiceRunLoop() A new context thread creation is requested: 5
00000070 winscard_svc.c:297:ContextThread() Thread is started: dwClientID=5, threadContext @0xbcfe00
00000031 winscard_svc.c:315:ContextThread() Received command: CMD_VERSION from client 5
00000017 winscard_svc.c:327:ContextThread() Client is protocol version 4:2
00000013 winscard_svc.c:347:ContextThread() CMD_VERSION rv=0x0 for client 5
00000120 winscard_svc.c:315:ContextThread() Received command: ESTABLISH_CONTEXT from client 5
00000031 winscard.c:193:SCardEstablishContext() Establishing Context: 0x2B04EDE0
00000014 winscard_svc.c:408:ContextThread() ESTABLISH_CONTEXT rv=0x0 for client 5
00000072 winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 5
00000103 winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 5
00000032 winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 5
00000019 winscard_svc.c:389:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 5
00000052 winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 5
00000123 winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 5
00000084 winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 5
00000069 winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 5
00000084 winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 5
[/INDENT]

pcscd prints this at start```
[INDENT]00000000 debuglog.c:269:DebugLogSetLevel() debug level=debug
00000129 configfile.l:245:DBGetReaderListDir() Parsing conf directory: /etc/reader.conf.d
00000025 configfile.l:298:DBGetReaderList() Parsing conf file: /etc/reader.conf.d/libtowitoko2
00000071 configfile.l:257:DBGetReaderListDir() Skipping non regular file: .
00000011 configfile.l:257:DBGetReaderListDir() Skipping non regular file: ..
00000020 readerfactory.c:978:RFInitializeReader() Attempting startup of Towitoko Chipdrive Reader 00 00 using /usr/lib/libtowitoko.so.2.0.0
00000081 dyn_unix.c:81:DYN_GetAddress() IFDHCreateChannelByName: /usr/lib/libtowitoko.so.2.0.0: undefined symbol: IFDHCreateChannelByName
00000016 readerfactory.c:836:RFBindFunctions() Loading IFD Handler 2.0
00000083 readerfactory.c:1009:RFInitializeReader() Open Port 0x103F8 Failed (/dev/ttyS0)
00000011 readerfactory.c:312:RFAddReader() Towitoko Chipdrive Reader init failed.
00000012 readerfactory.c:529:RFRemoveReader() UnrefReader() count was: 1
00000009 readerfactory.c:1029:RFUnInitializeReader() Attempting shutdown of Towitoko Chipdrive Reader 00 00.
00000008 readerfactory.c:905:RFUnloadReader() Unloading reader driver.
00000035 pcscdaemon.c:516:main() pcsc-lite 1.8.5 daemon ready.
00000537 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/001/001
00000091 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/001/001
00000093 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0020, path: /dev/bus/usb/001/002
00000093 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x03F0, PID: 0x231D, path: /dev/bus/usb/001/003
00000091 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x03F0, PID: 0x231D, path: /dev/bus/usb/001/003
00000089 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x03F0, PID: 0x231D, path: /dev/bus/usb/001/003
00000088 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x03F0, PID: 0x231D, path: /dev/bus/usb/001/003
00000089 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0020, path: /dev/bus/usb/001/002
00000094 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x138A, PID: 0x0007, path: /dev/bus/usb/001/004
00000090 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0020, path: /dev/bus/usb/001/002
00000121 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/003/001
00000180 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0003, path: /dev/bus/usb/004/001
00000115 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/002/001
00000087 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/002/001
00000094 hotplug_libudev.c:260:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0020, path: /dev/bus/usb/002/002

[/INDENT]

```
I also see this in /var/log/syslog  but I read somewhere that it is just a warning```
[INDENT]Mar 17 16:28:20 coyote-HP-EliteBook-8740w pcscd: dyn_unix.c:81:DYN_GetAddress() IFDHCreateChannelByName: /usr/lib/libtowitoko.so.2.0.0: undefined symbol: IFDHCreateChannelByName
Mar 17 16:28:20 coyote-HP-EliteBook-8740w pcscd: readerfactory.c:1009:RFInitializeReader() Open Port 0x103F8 Failed (/dev/ttyS0)
Mar 17 16:28:20 coyote-HP-EliteBook-8740w pcscd: readerfactory.c:312:RFAddReader() Towitoko Chipdrive Reader init failed.

[/INDENT]

```

---

