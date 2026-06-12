---
title: "weird message in syslog"
date: 2008-04-19
forum: General Help
---

### Post by jessika-kaos on 2008-04-19
this is completely filling my syslog, it repeats every few seconds. Does anyone have an idea as to what this means? I am using Hardy as of two days ago, but when I first installed it this was not filling up the logs because I checked them in relation to another issue. 

```
Apr 19 19:37:04 HIVE kernel: [   79.303333] ata2.01: qc timeout (cmd 0xa0)
Apr 19 19:37:04 HIVE kernel: [   79.303340] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Apr 19 19:37:04 HIVE kernel: [   79.303347] ata2.01: cmd a0/00:00:00:08:00/00:00:00:00:00/b0 tag 0 pio 8 in
Apr 19 19:37:04 HIVE kernel: [   79.303348]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Apr 19 19:37:04 HIVE kernel: [   79.303349]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
Apr 19 19:37:04 HIVE kernel: [   79.303352] ata2.01: status: { DRDY ERR }
Apr 19 19:37:04 HIVE kernel: [   79.303364] ata2: soft resetting link
Apr 19 19:37:04 HIVE kernel: [   79.576803] ata2.00: configured for UDMA/33
Apr 19 19:37:05 HIVE kernel: [   79.648435] ata2.01: configured for UDMA/33
Apr 19 19:37:05 HIVE kernel: [   79.648447] ata2: EH complete
Apr 19 19:37:35 HIVE kernel: [   93.582671] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Apr 19 19:37:35 HIVE kernel: [   93.582700] ata2.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
Apr 19 19:37:35 HIVE kernel: [   93.582701]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
Apr 19 19:37:35 HIVE kernel: [   93.582702]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr 19 19:37:35 HIVE kernel: [   93.582705] ata2.00: status: { DRDY }
Apr 19 19:37:35 HIVE kernel: [   93.582717] ata2: soft resetting link
Apr 19 19:37:35 HIVE kernel: [   93.852149] ata2.00: configured for UDMA/33
Apr 19 19:37:35 HIVE kernel: [   93.920710] ata2.01: configured for UDMA/33
Apr 19 19:37:35 HIVE kernel: [   93.920718] ata2: EH complete
```

---

### Post by jessika-kaos on 2008-04-20
No ideas? I'm assuming it has something to do with a hard drive, but both disks seem to be working fine and I can't figure out the message.

---

### Post by pseudo-random on 2008-04-20
It looks like minor I/O problems with your Hard drive. If you say it works fine then leave it. Its just your syslog logging level being a bit too verbose. I don't know where you can adjust the logging level for that BTW but it seems fine otherwise.

---

### Post by jessika-kaos on 2008-04-20
Thanks. Even though I didn't have this problem with Gutsy, I guess I am just worried it could be some foreshadowing of a hardware problem or something.

---

### Post by gimfred on 2008-05-02
I'm having a very similar problem(same error essentially) but my system is continually hanging. I'd be ever so grateful if someone could point me in the direction of how to fix it. My situation is that I eventually noticed that my home directory seems to go missing just before the hang, then I have to do a hard reboot. dropping to a shell doesn't work either.

---

### Post by kiev on 2008-05-20
it takes place for many, many users

The system droops periodically, it is sometimes impossible to reboot her - file system is not accessible.

I changed hard drive and sata port, became a little better, but then errors appeared again

May 20 13:42:04 mserv kernel: [64982.149445] ata4.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
May 20 13:42:04 mserv kernel: [64982.149479] ata4.01: cmd ca/00:20:97:04:cb/00:00:00:00:00/f3 tag 0 dma 16384 out
May 20 13:42:04 mserv kernel: [64982.149481]          res 40/00:00:ce:70:eb/84:00:03:00:00/f3 Emask 0x4 (timeout)
May 20 13:42:04 mserv kernel: [64982.149512] ata4.01: status: { DRDY }
May 20 13:42:04 mserv kernel: [64987.182353] ata4: port is slow to respond, please be patient (Status 0xd0)
May 20 13:42:04 mserv kernel: [64992.163315] ata4: device not ready (errno=-16), forcing hardreset
May 20 13:42:04 mserv kernel: [64992.163323] ata4: soft resetting link
May 20 13:42:04 mserv kernel: [65023.140425] ata4.01: qc timeout (cmd 0xec)
May 20 13:42:04 mserv kernel: [65023.140435] ata4.01: failed to IDENTIFY (I/O error, err_mask=0x4)
May 20 13:42:04 mserv kernel: [65023.140439] ata4.01: revalidation failed (errno=-5)
May 20 13:42:04 mserv kernel: [65023.140463] ata4: failed to recover some devices, retrying in 5 secs
May 20 13:42:04 mserv kernel: [65033.178281] ata4: port is slow to respond, please be patient (Status 0xd0)
May 20 13:42:04 mserv kernel: [65038.159242] ata4: device not ready (errno=-16), forcing hardreset
May 20 13:42:04 mserv kernel: [65038.159250] ata4: soft resetting link
May 20 13:42:04 mserv kernel: [65038.416615] ata4.01: configured for UDMA/33
May 20 13:42:04 mserv kernel: [65038.416638] ata4: EH complete

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920)
[https://bugs.launchpad.net/ubuntu/+bug/164183](https://bugs.launchpad.net/ubuntu/+bug/164183)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229747](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229747)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159521](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159521)
[https://bugs.launchpad.net/ubuntu/+bug/164183](https://bugs.launchpad.net/ubuntu/+bug/164183)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187146)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221437](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221437)
[https://bugs.launchpad.net/ubuntu/+bug/226600](https://bugs.launchpad.net/ubuntu/+bug/226600)

HEEELLP!!!!!

---

