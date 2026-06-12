---
title: "Pcscd daemon not starting"
date: 2023-07-28
forum: General Help
---

### Post by bobhart2 on 2023-07-28
I am running Ubuntu 22.04.2 LTS. BTW, my Linux capabilities are fairly limited.

I am trying to get a Yubikey to work. In communicating with the Yubico support person, the problem is with the pcscd daemon. 

I tried these commands with no success:

1) sudo snap install pcsc-daemon -- didn't help

2) sudo apt-get install pcscd

.... many lines
Setting up libccid (1.5.0-2) ...
Setting up libpcsclite1:amd64 (1.9.5-3ubuntu1) ...
Setting up pcscd (1.9.5-3ubuntu1) ...
Created symlink /etc/systemd/system/sockets.target.wants/pcscd.socket &#8594; /lib/systemd/system/pcscd.socket.
pcscd.service is a disabled or a static unit, not starting it.
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Processing triggers for man-db (2.10.2-1) ...

-- third from bottom line is probably not good

3) sudo systemctl status pcscd

&#9675; pcscd.service - PC/SC Smart Card Daemon
     Loaded: loaded (/lib/systemd/system/pcscd.service; indirect; vendor preset>
     Active: inactive (dead) since Fri 2023-07-28 08:02:29 EDT; 1min 27s ago
TriggeredBy: &#9679; pcscd.socket
       Docs: man:pcscd(8)
    Process: 5431 ExecStart=/usr/sbin/pcscd --foreground --auto-exit $PCSCD_ARG>
   Main PID: 5431 (code=exited, status=0/SUCCESS)
        CPU: 7ms

Jul 28 08:01:28 bob-MS-7B54 systemd[1]: Started PC/SC Smart Card Daemon.
Jul 28 08:02:29 bob-MS-7B54 systemd[1]: pcscd.service: Deactivated successfully.

-- last line also not good

Any suggestions?

---

### Post by Xian on 2023-07-28
Try these commands in sequence:

$ sudo systemctl enable pcscd
$ sudo systemctl enable pcscd.socket

Reboot then post output of:

$ sudo systemctl status pcscd

---

### Post by bobhart2 on 2023-07-29
$ sudo systemctl status pcscd 
[sudo] password for bob: 
&#9675; pcscd.service - PC/SC Smart Card Daemon
     Loaded: loaded (/lib/systemd/system/pcscd.service; indirect; vendor preset>
     Active: inactive (dead)
TriggeredBy: &#9679; pcscd.socket
       Docs: man:pcscd(8)
lines 1-5/5 (END)

---

### Post by Xian on 2023-07-29
It might not be expected that pcscd is started when a reader is connected.
Yet pcscd should be active when there's an application wanting to use it.

Review this info: 
[https://ludovicrousseau.blogspot.com/2011/11/pcscd-auto-start-using-systemd.html](https://ludovicrousseau.blogspot.com/2011/11/pcscd-auto-start-using-systemd.html)
[https://support.yubico.com/hc/en-us/articles/360013708900-Using-Your-U2F-YubiKey-with-Linux](https://support.yubico.com/hc/en-us/articles/360013708900-Using-Your-U2F-YubiKey-with-Linux)
[https://easylinuxtipsproject.blogspot.com/p/bugs.html#ID11](https://easylinuxtipsproject.blogspot.com/p/bugs.html#ID11)

---

### Post by bobhart2 on 2023-07-31
Nothing works. I am calling it quits. Thanks for your help.

---

