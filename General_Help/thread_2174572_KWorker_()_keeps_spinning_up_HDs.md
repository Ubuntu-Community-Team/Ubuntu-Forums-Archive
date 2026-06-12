---
title: "KWorker (?) keeps spinning up HDs"
date: 2013-09-15
forum: General Help
---

### Post by Someone1 on 2013-09-15
I've just set up Ubuntu Server 12.04.3 LTS wtith LAMP, installed Webmin and Samba and every 5 minutes something seems to call a smartctl command so two of the four HDs spin up. I tried stopping all services and cronjobs, but it still happens. According to blktrace the call comes from kworker - but I guess that could be anything then?
```
  8,16   1        1     0.000000000  3903  G   N [kworker/1:0]
  8,16   1        2     0.000001316  3903  I   N 0 (00 ..) [kworker/1:0]
  8,16   1        3     0.000002693  3903  D   N 0 (00 ..) [kworker/1:0]
  8,16   0        1     0.329879634  4183  Q WBS [parted]
  8,16   0        2     0.329881220  4183  G WBS [parted]
  8,16   0        3     0.329882773  4183  I WBS [parted]
  8,16   0        4     0.329972236     0  C  WS 0 [0]
  8,16   0        5     0.337736338     0  C   R (a1 08 2e 00 01 00 00 00 00 ec 00 ..) [2]
  8,16   0        6     0.337816016  4184  C  WS 0 [0]
  8,16   0        7     0.337848437  4103  G   N [kworker/0:0]
  8,16   0        8     0.337849010  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0        9     0.337849374  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   0       10     0.337860291  4103  G   N [kworker/0:0]
  8,16   0       11     0.337860443  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0       12     0.337860567  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   0       13     0.338675935  4187  G   N [scsi_id]
  8,16   0       14     0.338680944  4187  I   R 254 (12 00 00 00 fe 00 ..) [scsi_id]
  8,16   0       15     0.338682153  4187  D   R 254 (12 00 00 00 fe 00 ..) [scsi_id]
  8,16   0       16     0.338696471     3  C   R (12 00 00 00 fe 00 ..) [0]
  8,16   0       17     0.338709694  4103  G   N [kworker/0:0]
  8,16   0       18     0.338709900  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0       19     0.338710113  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   0       20     0.338733284  4187  G   N [scsi_id]
  8,16   0       21     0.338734875  4187  I   R 254 (12 01 80 00 fe 00 ..) [scsi_id]
  8,16   0       22     0.338735108  4187  D   R 254 (12 01 80 00 fe 00 ..) [scsi_id]
  8,16   0       23     0.338739594     3  C   R (12 01 80 00 fe 00 ..) [0]
  8,16   0       24     0.338750390  4103  G   N [kworker/0:0]
  8,16   0       25     0.338750525  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0       26     0.338750703  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   0       27     0.339654526  4103  G   N [kworker/0:0]
  8,16   0       28     0.339655372  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0       29     0.339656017  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   1        4     0.329995519  3903  G   N [kworker/1:0]
  8,16   1        5     0.329996433  3903  I   N 0 (00 ..) [kworker/1:0]
  8,16   1        6     0.329996880  3903  D   N 0 (00 ..) [kworker/1:0]
  8,16   1        7     0.331607731  4184  G   N [ata_id]
  8,16   1        8     0.331613298  4184  I   R 36 (12 00 00 00 24 00 ..) [ata_id]
  8,16   1        9     0.331614356  4184  D   R 36 (12 00 00 00 24 00 ..) [ata_id]
  8,16   1       10     0.331630921    13  C   R (12 00 00 00 24 00 ..) [0]
  8,16   1       11     0.331640580  4184  G   N [ata_id]
  8,16   1       12     0.331642169  4184  I   R 512 (a1 08 2e 00 01 00 00 00 00 ec 00 ..) [ata_id]
  8,16   1       13     0.331642462  4184  D   R 512 (a1 08 2e 00 01 00 00 00 00 ec 00 ..) [ata_id]
  8,16   1       14     0.332028042  4183  Q WBS [parted]
  8,16   1       15     0.332028929  4183  G WBS [parted]
  8,16   1       16     0.332029731  4183  I WBS [parted]
  8,16   0       30     0.550090780  4213  G   N [smartctl]
  8,16   0       31     0.550095383  4213  I   R 36 (12 00 00 00 24 00 ..) [smartctl]
  8,16   0       32     0.550096624  4213  D   R 36 (12 00 00 00 24 00 ..) [smartctl]
  8,16   0       33     0.550109772     3  C   R (12 00 00 00 24 00 ..) [0]
  8,16   0       34     0.550128920  4213  G   N [smartctl]
  8,16   0       35     0.550130211  4213  I   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       36     0.550130414  4213  D   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       37     0.556225991     0  C   R (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [0]
  8,16   0       38     0.556254761  4213  G   N [smartctl]
  8,16   0       39     0.556257088  4213  I   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       40     0.556257433  4213  D   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       41     0.562347115     0  C   R (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [0]
  8,16   0       42     0.564063991  4103  G   N [kworker/0:0]
  8,16   0       43     0.564064593  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0       44     0.564065282  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   0       45     0.576811973  4215  G   N [smartctl]
  8,16   0       46     0.576816832  4215  I   R 36 (12 00 00 00 24 00 ..) [smartctl]
  8,16   0       47     0.576818035  4215  D   R 36 (12 00 00 00 24 00 ..) [smartctl]
  8,16   0       48     0.576831319     3  C   R (12 00 00 00 24 00 ..) [0]
  8,16   0       49     0.576850268  4215  G   N [smartctl]
  8,16   0       50     0.576851602  4215  I   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       51     0.576851787  4215  D   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       52     0.582940438     0  C   R (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [0]
  8,16   0       53     0.582968372  4215  G   N [smartctl]
  8,16   0       54     0.582971277  4215  I   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       55     0.582971685  4215  D   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       56     0.589059959     0  C   R (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [0]
  8,16   0       57     0.590193857  4215  G   N [smartctl]
  8,16   0       58     0.590196594  4215  I   R 512 (85 08 0e 00 d0 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       59     0.590197046  4215  D   R 512 (85 08 0e 00 d0 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       60     0.848540567     0  C   R (85 08 0e 00 d0 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       61     0.848560145  4215  G   N [smartctl]
  8,16   0       62     0.848563002  4215  I   R 512 (85 08 0e 00 d1 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       63     0.848563355  4215  D   R 512 (85 08 0e 00 d1 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       64     0.981143896     0  C   R (85 08 0e 00 d1 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       65     0.981167896  4215  G   N [smartctl]
  8,16   0       66     0.981168621  4215  I   N 0 (85 06 2c 00 da 00 00 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       67     0.981169036  4215  D   N 0 (85 06 2c 00 da 00 00 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       68     1.378318940  4103  G   N [kworker/0:0]
  8,16   0       69     1.378319676  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0       70     1.378320278  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   1       17     1.391862310  4217  G   N [smartctl]
  8,16   1       18     1.391866682  4217  I   R 36 (12 00 00 00 24 00 ..) [smartctl]
  8,16   1       19     1.391867780  4217  D   R 36 (12 00 00 00 24 00 ..) [smartctl]
  8,16   1       20     1.391881050    13  C   R (12 00 00 00 24 00 ..) [0]
  8,16   1       21     1.391900602  4217  G   N [smartctl]
  8,16   1       22     1.391901817  4217  I   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   1       23     1.391902074  4217  D   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       71     1.397987331     0  C   R (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [0]
  8,16   0       72     1.398033151  4217  G   N [smartctl]
  8,16   0       73     1.398037116  4217  I   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       74     1.398037733  4217  D   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       75     1.404125431     0  C   R (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [0]
  8,16   0       76     1.406096795  4217  G   N [smartctl]
  8,16   0       77     1.406099374  4217  I   R 512 (85 08 0e 00 d0 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       78     1.406099937  4217  D   R 512 (85 08 0e 00 d0 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       79     1.665476298     0  C   R (85 08 0e 00 d0 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       80     1.665508703  4217  G   N [smartctl]
  8,16   0       81     1.665513502  4217  I   R 512 (85 08 0e 00 d1 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       82     1.665514086  4217  D   R 512 (85 08 0e 00 d1 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       83     1.798079241     0  C   R (85 08 0e 00 d1 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       84     1.798114105  4217  G   N [smartctl]
  8,16   0       85     1.798115270  4217  I   N 0 (85 06 2c 00 da 00 00 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       86     1.798115916  4217  D   N 0 (85 06 2c 00 da 00 00 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       87     2.195393687  4217  G   N [smartctl]
  8,16   0       88     2.195398959  4217  I   R 512 (85 08 0e 00 d5 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       89     2.195399731  4217  D   R 512 (85 08 0e 00 d5 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       90     2.327904842     0  C   R (85 08 0e 00 d5 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       91     2.327932477  4217  G   N [smartctl]
  8,16   0       92     2.327937200  4217  I   R 512 (85 08 0e 00 d5 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       93     2.327937775  4217  D   R 512 (85 08 0e 00 d5 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       94     2.460519284     0  C   R (85 08 0e 00 d5 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       95     2.460683100  4217  G   N [smartctl]
  8,16   0       96     2.460687756  4217  I   R 512 (85 08 0e 00 d5 00 01 00 06 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       97     2.460688385  4217  D   R 512 (85 08 0e 00 d5 00 01 00 06 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       98     2.592990338     0  C   R (85 08 0e 00 d5 00 01 00 06 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       99     2.593029337  4217  G   N [smartctl]
  8,16   0      100     2.593033939  4217  I   R 512 (85 08 0e 00 d5 00 01 00 09 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0      101     2.593034574  4217  D   R 512 (85 08 0e 00 d5 00 01 00 09 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0      102     2.725442891     0  C   R (85 08 0e 00 d5 00 01 00 09 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0      103     2.725515089  4103  G   N [kworker/0:0]
  8,16   0      104     2.725515638  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0      105     2.725516137  4103  D   N 0 (00 ..) [kworker/0:0]
```

/Edit: I just noticed that the other two HDs won't go to sleep either - smartctl keeps them awake even though it seems not to get called if they are sleeping.

---

### Post by cristian-tarsoaga on 2014-01-22
Hi there,

I'm having the same problem,
Anyone found the issue? Or a solution for this?

---

### Post by cristian-tarsoaga on 2014-01-23
*had* exactly the same problem

I have two external usb hard drives connected to my computer, both Western Digital (Elements/My Book).
1st - model 1170, 2nd - model 1230, both SMART enabled.

*my problem is that 2nd does go to sleep for about 1 second, then immediately wakes up (1st one has no such problem)*

First, I must note that Western Digital does not officially support linux for WD My Book (nice!!)

I want 10 minutes idle timeout, before going to sleep so I tried the following

- [FONT=courier new]hdparm -y[/FONT]
- [FONT=courier new]sdparm --command[/FONT]
- [FONT=courier new]hdparm -S 120[/FONT]
- [FONT=courier new]idle3ctl -s 148 ([/FONT][idle3-tools]("http://idle3-tools.sourceforge.net/") is a [FONT=courier new]wdidle.exe[/FONT] replacement on linux)
- [FONT=courier new][hd-idle]("http://hd-idle.sourceforge.net/") ([FONT=arial]ubuntu [/FONT][/FONT][guide ]("http://askubuntu.com/questions/196473/setting-sata-hdd-spindown-time")is available [here]("http://blog.is-a-geek.org/festplatten-in-den-standby-modus-versetzen-unter-ubuntu-desktopserver-mit-hd-idle").[FONT=courier new])[/FONT]

The most I got was to put hdd to sleep for about 1 second or so, then hdd wakes up.

The source of the problem?

Some people suggest this is an [apm]("http://askubuntu.com/questions/39760/how-can-i-control-hdd-spin-down-time") problem. Others blame [FONT=courier new][smartmontools]("http://markblog.hjarding.dk/index.php?/archives/14-Western-Digital,-Linux,-S.M.A.R.T")[/FONT], see the comments.

[FONT=courier new]- /etc/fstab[/FONT] contains [FONT=courier new]noatime[/FONT], so access time is not the issue here. And by the way, happens even with the disk not mounted.
- No file was read/written to that disk ([FONT=courier new]echo 1 | sudo tee /proc/sys/vm/block_dump[/FONT] and later [FONT=courier new]watch grep /dev/wd /var/log/syslog[/FONT])
- Still, using [FONT=courier new]btrace, [/FONT]I saw [FONT=courier new]parted[/FONT] threads/processes reading some blocks from the hdd. 
I suspected **this **to be the problem. 
After uninstalling [FONT=courier new]parted[/FONT], problem appeared to be temporarily gone.
But then I noticed (using [FONT=courier new]btrace[/FONT]) that [FONT=courier new]fdisk [/FONT]was causing the same behavior.

So the culprit is the one that starts parted/fdisk. But who is it?
These processes were not reading/writing files. AS a bonus, they are spawned and die soon so I cannot easily get info about who starts them.
We'll see.

---

### Post by cristian-tarsoaga on 2014-01-30
seems that on my machine (a small server), [FONT=courier new]**webmin** [/FONT]is the culprit

[FONT=courier new]webmin [/FONT]uses [FONT=courier new]parted/fdisk[/FONT] to determine harddrives status and wakes them up (via [FONT=courier new]webmincron.pl[/FONT])

problem solved

---

### Post by cristian-tarsoaga on 2014-01-30
webmin is probably the cause
uses webmincron.pl to check the status of the available hard drives which wakes them up


> **Someone1 said:**
> I've just set up Ubuntu Server 12.04.3 LTS wtith LAMP, installed Webmin and Samba and every 5 minutes something seems to call a smartctl command so two of the four HDs spin up. I tried stopping all services and cronjobs, but it still happens. According to blktrace the call comes from kworker - but I guess that could be anything then?
```
  8,16   1        1     0.000000000  3903  G   N [kworker/1:0]
  8,16   1        2     0.000001316  3903  I   N 0 (00 ..) [kworker/1:0]
  8,16   1        3     0.000002693  3903  D   N 0 (00 ..) [kworker/1:0]
  8,16   0        1     0.329879634  4183  Q WBS [parted]
  8,16   0        2     0.329881220  4183  G WBS [parted]
  8,16   0        3     0.329882773  4183  I WBS [parted]
  8,16   0        4     0.329972236     0  C  WS 0 [0]
  8,16   0        5     0.337736338     0  C   R (a1 08 2e 00 01 00 00 00 00 ec 00 ..) [2]
  8,16   0        6     0.337816016  4184  C  WS 0 [0]
  8,16   0        7     0.337848437  4103  G   N [kworker/0:0]
  8,16   0        8     0.337849010  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0        9     0.337849374  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   0       10     0.337860291  4103  G   N [kworker/0:0]
  8,16   0       11     0.337860443  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0       12     0.337860567  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   0       13     0.338675935  4187  G   N [scsi_id]
  8,16   0       14     0.338680944  4187  I   R 254 (12 00 00 00 fe 00 ..) [scsi_id]
  8,16   0       15     0.338682153  4187  D   R 254 (12 00 00 00 fe 00 ..) [scsi_id]
  8,16   0       16     0.338696471     3  C   R (12 00 00 00 fe 00 ..) [0]
  8,16   0       17     0.338709694  4103  G   N [kworker/0:0]
  8,16   0       18     0.338709900  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0       19     0.338710113  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   0       20     0.338733284  4187  G   N [scsi_id]
  8,16   0       21     0.338734875  4187  I   R 254 (12 01 80 00 fe 00 ..) [scsi_id]
  8,16   0       22     0.338735108  4187  D   R 254 (12 01 80 00 fe 00 ..) [scsi_id]
  8,16   0       23     0.338739594     3  C   R (12 01 80 00 fe 00 ..) [0]
  8,16   0       24     0.338750390  4103  G   N [kworker/0:0]
  8,16   0       25     0.338750525  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0       26     0.338750703  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   0       27     0.339654526  4103  G   N [kworker/0:0]
  8,16   0       28     0.339655372  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0       29     0.339656017  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   1        4     0.329995519  3903  G   N [kworker/1:0]
  8,16   1        5     0.329996433  3903  I   N 0 (00 ..) [kworker/1:0]
  8,16   1        6     0.329996880  3903  D   N 0 (00 ..) [kworker/1:0]
  8,16   1        7     0.331607731  4184  G   N [ata_id]
  8,16   1        8     0.331613298  4184  I   R 36 (12 00 00 00 24 00 ..) [ata_id]
  8,16   1        9     0.331614356  4184  D   R 36 (12 00 00 00 24 00 ..) [ata_id]
  8,16   1       10     0.331630921    13  C   R (12 00 00 00 24 00 ..) [0]
  8,16   1       11     0.331640580  4184  G   N [ata_id]
  8,16   1       12     0.331642169  4184  I   R 512 (a1 08 2e 00 01 00 00 00 00 ec 00 ..) [ata_id]
  8,16   1       13     0.331642462  4184  D   R 512 (a1 08 2e 00 01 00 00 00 00 ec 00 ..) [ata_id]
  8,16   1       14     0.332028042  4183  Q WBS [parted]
  8,16   1       15     0.332028929  4183  G WBS [parted]
  8,16   1       16     0.332029731  4183  I WBS [parted]
  8,16   0       30     0.550090780  4213  G   N [smartctl]
  8,16   0       31     0.550095383  4213  I   R 36 (12 00 00 00 24 00 ..) [smartctl]
  8,16   0       32     0.550096624  4213  D   R 36 (12 00 00 00 24 00 ..) [smartctl]
  8,16   0       33     0.550109772     3  C   R (12 00 00 00 24 00 ..) [0]
  8,16   0       34     0.550128920  4213  G   N [smartctl]
  8,16   0       35     0.550130211  4213  I   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       36     0.550130414  4213  D   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       37     0.556225991     0  C   R (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [0]
  8,16   0       38     0.556254761  4213  G   N [smartctl]
  8,16   0       39     0.556257088  4213  I   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       40     0.556257433  4213  D   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       41     0.562347115     0  C   R (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [0]
  8,16   0       42     0.564063991  4103  G   N [kworker/0:0]
  8,16   0       43     0.564064593  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0       44     0.564065282  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   0       45     0.576811973  4215  G   N [smartctl]
  8,16   0       46     0.576816832  4215  I   R 36 (12 00 00 00 24 00 ..) [smartctl]
  8,16   0       47     0.576818035  4215  D   R 36 (12 00 00 00 24 00 ..) [smartctl]
  8,16   0       48     0.576831319     3  C   R (12 00 00 00 24 00 ..) [0]
  8,16   0       49     0.576850268  4215  G   N [smartctl]
  8,16   0       50     0.576851602  4215  I   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       51     0.576851787  4215  D   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       52     0.582940438     0  C   R (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [0]
  8,16   0       53     0.582968372  4215  G   N [smartctl]
  8,16   0       54     0.582971277  4215  I   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       55     0.582971685  4215  D   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       56     0.589059959     0  C   R (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [0]
  8,16   0       57     0.590193857  4215  G   N [smartctl]
  8,16   0       58     0.590196594  4215  I   R 512 (85 08 0e 00 d0 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       59     0.590197046  4215  D   R 512 (85 08 0e 00 d0 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       60     0.848540567     0  C   R (85 08 0e 00 d0 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       61     0.848560145  4215  G   N [smartctl]
  8,16   0       62     0.848563002  4215  I   R 512 (85 08 0e 00 d1 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       63     0.848563355  4215  D   R 512 (85 08 0e 00 d1 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       64     0.981143896     0  C   R (85 08 0e 00 d1 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       65     0.981167896  4215  G   N [smartctl]
  8,16   0       66     0.981168621  4215  I   N 0 (85 06 2c 00 da 00 00 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       67     0.981169036  4215  D   N 0 (85 06 2c 00 da 00 00 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       68     1.378318940  4103  G   N [kworker/0:0]
  8,16   0       69     1.378319676  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0       70     1.378320278  4103  D   N 0 (00 ..) [kworker/0:0]
  8,16   1       17     1.391862310  4217  G   N [smartctl]
  8,16   1       18     1.391866682  4217  I   R 36 (12 00 00 00 24 00 ..) [smartctl]
  8,16   1       19     1.391867780  4217  D   R 36 (12 00 00 00 24 00 ..) [smartctl]
  8,16   1       20     1.391881050    13  C   R (12 00 00 00 24 00 ..) [0]
  8,16   1       21     1.391900602  4217  G   N [smartctl]
  8,16   1       22     1.391901817  4217  I   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   1       23     1.391902074  4217  D   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       71     1.397987331     0  C   R (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [0]
  8,16   0       72     1.398033151  4217  G   N [smartctl]
  8,16   0       73     1.398037116  4217  I   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       74     1.398037733  4217  D   R 512 (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [smartctl]
  8,16   0       75     1.404125431     0  C   R (85 08 0e 00 00 00 01 00 00 00 00 00 00 00 ec 00 ..) [0]
  8,16   0       76     1.406096795  4217  G   N [smartctl]
  8,16   0       77     1.406099374  4217  I   R 512 (85 08 0e 00 d0 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       78     1.406099937  4217  D   R 512 (85 08 0e 00 d0 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       79     1.665476298     0  C   R (85 08 0e 00 d0 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       80     1.665508703  4217  G   N [smartctl]
  8,16   0       81     1.665513502  4217  I   R 512 (85 08 0e 00 d1 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       82     1.665514086  4217  D   R 512 (85 08 0e 00 d1 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       83     1.798079241     0  C   R (85 08 0e 00 d1 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       84     1.798114105  4217  G   N [smartctl]
  8,16   0       85     1.798115270  4217  I   N 0 (85 06 2c 00 da 00 00 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       86     1.798115916  4217  D   N 0 (85 06 2c 00 da 00 00 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       87     2.195393687  4217  G   N [smartctl]
  8,16   0       88     2.195398959  4217  I   R 512 (85 08 0e 00 d5 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       89     2.195399731  4217  D   R 512 (85 08 0e 00 d5 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       90     2.327904842     0  C   R (85 08 0e 00 d5 00 01 00 00 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       91     2.327932477  4217  G   N [smartctl]
  8,16   0       92     2.327937200  4217  I   R 512 (85 08 0e 00 d5 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       93     2.327937775  4217  D   R 512 (85 08 0e 00 d5 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       94     2.460519284     0  C   R (85 08 0e 00 d5 00 01 00 01 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       95     2.460683100  4217  G   N [smartctl]
  8,16   0       96     2.460687756  4217  I   R 512 (85 08 0e 00 d5 00 01 00 06 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       97     2.460688385  4217  D   R 512 (85 08 0e 00 d5 00 01 00 06 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0       98     2.592990338     0  C   R (85 08 0e 00 d5 00 01 00 06 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0       99     2.593029337  4217  G   N [smartctl]
  8,16   0      100     2.593033939  4217  I   R 512 (85 08 0e 00 d5 00 01 00 09 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0      101     2.593034574  4217  D   R 512 (85 08 0e 00 d5 00 01 00 09 00 4f 00 c2 00 b0 00 ..) [smartctl]
  8,16   0      102     2.725442891     0  C   R (85 08 0e 00 d5 00 01 00 09 00 4f 00 c2 00 b0 00 ..) [0]
  8,16   0      103     2.725515089  4103  G   N [kworker/0:0]
  8,16   0      104     2.725515638  4103  I   N 0 (00 ..) [kworker/0:0]
  8,16   0      105     2.725516137  4103  D   N 0 (00 ..) [kworker/0:0]
```

/Edit: I just noticed that the other two HDs won't go to sleep either - smartctl keeps them awake even though it seems not to get called if they are sleeping.

---

