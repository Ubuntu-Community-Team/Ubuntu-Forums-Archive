---
title: "suppressing specific syslog message?"
date: 2013-02-13
forum: General Help
---

### Post by iaw4 on 2013-02-13
my syslog file is full of these funny errors---every 10 seconds, I get a couple of them:

> 
Feb 13 14:43:56 iaw-office kernel: [788497.249479] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 61
Feb 13 14:43:56 iaw-office kernel: [788497.249480] Raw EDID:
Feb 13 14:43:56 iaw-office kernel: [788497.249482]  	00 ff ff ff ff ff ff 00 00 a0 00 00 00 00 00 01
Feb 13 14:43:56 iaw-office kernel: [788497.249483]  	02 10 01 03 80 40 28 78 2a 85 85 a8 43 34 a0 25
Feb 13 14:43:56 iaw-office kernel: [788497.249485]  	02 50 54 00 00 00 01 01 01 00 01 00 01 00 01 00
Feb 13 14:43:56 iaw-office kernel: [788497.249486]  	01 00 01 01 01 01 a0 68 00 a0 a0 40 2e 60 30 20
Feb 13 14:43:56 iaw-office kernel: [788497.249488]  	36 00 81 90 21 00 00 1a 00 00 00 a0 00 00 00 30
Feb 13 14:43:56 iaw-office kernel: [788497.249489]  	00 00 32 00 00 10 20 00 00 0a 00 00 00 fc 00 40
Feb 13 14:43:56 iaw-office kernel: [788497.249491]  	40 00 4c 00 11 30 30 31 00 00 20 20 00 00 00 fd
Feb 13 14:43:56 iaw-office kernel: [788497.249492]  	00 01 46 0c 31 10 00 00 20 00 20 00 20 20 00 84


is it possible to suppress these messages and only these messages?

---

### Post by matt_symes on 2013-02-13
Hi

> **iaw4 said:**
> my syslog file is full of these funny errors---every 10 seconds, I get a couple of them:
```

Feb 13 14:43:56 iaw-office kernel: [788497.249479] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 61
Feb 13 14:43:56 iaw-office kernel: [788497.249480] Raw EDID:
Feb 13 14:43:56 iaw-office kernel: [788497.249482]      00 ff ff ff ff ff ff 00 00 a0 00 00 00 00 00 01
Feb 13 14:43:56 iaw-office kernel: [788497.249483]      02 10 01 03 80 40 28 78 2a 85 85 a8 43 34 a0 25
Feb 13 14:43:56 iaw-office kernel: [788497.249485]      02 50 54 00 00 00 01 01 01 00 01 00 01 00 01 00
Feb 13 14:43:56 iaw-office kernel: [788497.249486]      01 00 01 01 01 01 a0 68 00 a0 a0 40 2e 60 30 20
Feb 13 14:43:56 iaw-office kernel: [788497.249488]      36 00 81 90 21 00 00 1a 00 00 00 a0 00 00 00 30
Feb 13 14:43:56 iaw-office kernel: [788497.249489]      00 00 32 00 00 10 20 00 00 0a 00 00 00 fc 00 40
Feb 13 14:43:56 iaw-office kernel: [788497.249491]      40 00 4c 00 11 30 30 31 00 00 20 20 00 00 00 fd
Feb 13 14:43:56 iaw-office kernel: [788497.249492]      00 01 46 0c 31 10 00 00 20 00 20 00 20 20 00 84                      
```is it possible to suppress these messages and only these messages?

The EDID message is from your monitor. It's a block of data that specifics the monitors characteristic. Yours is broken though. 

It is possible to fix these issues by creating a custom EDID but the process is a bit complicated.

To surpress the messages, try this. 

Open a terminal and type this to start nano.

```
sudo nano /etc/rsyslog.d/01-remove.conf
```Enter your password. It will not be echoed to the screen.

Copy and paste this into it.

```
:msg,contains,"EDID checksum is invalid" ~
:msg,contains,"00 ff ff ff ff ff ff 00 00 a0 00 00 00 00 00 01" ~
:msg,contains,"02 10 01 03 80 40 28 78 2a 85 85 a8 43 34 a0 25" ~
:msg,contains,"01 00 01 01 01 01 a0 68 00 a0 a0 40 2e 60 30 20" ~
:msg,contains,"36 00 81 90 21 00 00 1a 00 00 00 a0 00 00 00 30" ~
:msg,contains,"00 00 32 00 00 10 20 00 00 0a 00 00 00 fc 00 40" ~
:msg,contains,"40 00 4c 00 11 30 30 31 00 00 20 20 00 00 00 fd" ~
:msg,contains,"00 01 46 0c 31 10 00 00 20 00 20 00 20 20 00 84" ~
```Save the file.

Restart syslogd using this command.

```
sudo service rsyslog restart
```

It should perform a regex match on the strings in the message part of the syslog entry.

Kind regards

---

### Post by iaw4 on 2013-02-15
thank you.  this worked great.  /iaw

---

