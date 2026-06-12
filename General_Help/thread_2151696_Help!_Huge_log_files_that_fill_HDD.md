---
title: "Help! Huge log files that fill HDD"
date: 2013-06-05
forum: General Help
---

### Post by PC_load_letter on 2013-06-05
Running Ubuntu 12.10 64 bit, on a Xeon workstation, and the following log files (with excerpts from each) are growing to HUGE sizes as detailed below.

1. /var/log/kern.log is about 194 GB right now, here is the recurring error:
```
Jun  3 13:21:59 ZeusUbuntu kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791306] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791314] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791318] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791322] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791326] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791330] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791334] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791338] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791342] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791346] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791349] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791353] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791357] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791361] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791365] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791368] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791372] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791376] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791380] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791383] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791387] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791391] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791395] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791399] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791402] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791406] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791410] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791416] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791419] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791422] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791424] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791427] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791430] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791433] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791435] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791438] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791441] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791444] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791447] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791449] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791452] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791455] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791457] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791460] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791463] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791465] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791468] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791471] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791473] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791476] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  3 13:21:59 ZeusUbuntu kernel: [955536.791479] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
``` 

2. /var/log/syslog.1 is about 102 GB, here is the recurring error
```
Jun  5 08:24:14 ZeusUbuntu kernel: [154058.485097] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 08:24:14 ZeusUbuntu kernel: [154058.485099] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 08:24:14 ZeusUbuntu kernel: [154058.485102] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 08:24:14 ZeusUbuntu kernel: [154058.485105] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 08:24:14 ZeusUbuntu kernel: [154058.485107] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 08:24:14 ZeusUbuntu kernel: [154058.485110] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 08:24:14 ZeusUbuntu kernel: [154058.485112] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 08:24:14 ZeusUbuntu kernel: [154058.485115] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 08:24:14 ZeusUbuntu kernel: [154058.485118] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 08:24:14 ZeusUbuntu kernel: [154058.485120] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)

```

3. /var/log/syslog is about 10 GB in size, here is a sample:
```
Jun  5 11:06:34 ZeusUbuntu kernel: [163782.751798] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 11:06:34 ZeusUbuntu kernel: [163782.751805] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 11:06:34 ZeusUbuntu kernel: [163782.751812] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 11:06:34 ZeusUbuntu kernel: [163782.751818] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 11:06:34 ZeusUbuntu kernel: [163782.751821] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 11:06:34 ZeusUbuntu kernel: [163782.751823] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 11:06:34 ZeusUbuntu kernel: [163782.751826] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 11:06:34 ZeusUbuntu kernel: [163782.751829] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 11:06:34 ZeusUbuntu kernel: [163782.751831] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
Jun  5 11:06:34 ZeusUbuntu kernel: [163782.751834] EDAC MC0: CE error on CPU#0Channel#2_DIMM#0 (channel:2 slot:0 page:0x0 offset:0x0 grain:8 syndrome:0x0)
```

So any idea what the heck is going on? Help is much appreciated.

Thanks.

---

### Post by aromo on 2013-06-05
EDAC has to do with memory.  Did you run a memtest to verify that your RAM is in good order?

---

### Post by PC_load_letter on 2013-06-05
We have error correcting memory and it seems that one of them is failing. 

In any case, is there a way to suppress the reporting of this error?

---

### Post by abyrne on 2013-06-05
> **PC_load_letter said:**
> We have error correcting memory and it seems that one of them is failing. 

In any case, is there a way to suppress the reporting of this error?
I would suggest dumping and replacing that bad memory instead of just suppressing the error. Nevertheless, syslog has filtering capabilities. Run:
```
sudo nano /etc/rsyslog.d/01-blocklist.conf
```
(replace 'sudo nano' with 'gksudo gedit' if you prefer to edit with a GUI)
and add in the following line:
```

:msg,contains,"EDAC MC0: CE error on CPU" ~

```
Save it and restart the logging service
```
sudo service rsyslog restart
```
(Source: [http://askubuntu.com/a/21648](http://askubuntu.com/a/21648))
That should stop the incessant logging. Seriously though, fix the memory problem, don't just suppress it.

---

