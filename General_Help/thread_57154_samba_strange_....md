---
title: "samba strange ..."
date: 2005-08-15
forum: General Help
---

### Post by tunnelblick on 2005-08-15
Hi everyone.

I get the following problem: I have 3 instances of my smbd running! is this normal? I installed Ubuntu the standard way, then installed the samba-package with apt. The first thing I noticed was a very bad performance. This issue is still unsolved. Before I get to mention it, I also created a "real" root user. The samba-daemon is started on boot. I just ran "top" and sorted by MEM-usage and saw 3 instances of smbd. 2 were from root, 1 from my normal user I created during install. Is this ok? Btw, when I copy files via TotalCommander, everything works just fine (ca. 7Mb/sec). Windows-transfers are very slow, meaning that transfer goes "drop-wise" with little pauses (so it looks to me) during transfer.
Anyone knows this problem?
P.S. With SuSE everything worked just fine.

Regards,
Tunnelblick

---

### Post by guy_uk on 2005-08-15
i vaguely remember reading during my own samba searches that samba opens an smbd instance for each open smb connection...

my memory does however suck, but it may be something worth looking into

---

### Post by tunnelblick on 2005-08-16
One other thiung I forgot: I also get this output from smbstatus:

Locked files:
Pid    DenyMode   Access            R/W        Oplock           Name
--------------------------------------------------------------
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/004.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/024.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/022.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/001.part   Tue Aug 16 10:22:19 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/007.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/002.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/025.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/028.part   Tue Aug 16 09:22:05 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/029.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/008.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/027.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/011.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/023.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/020.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/010.part   Tue Aug 16 11:59:21 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/003.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/013.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/015.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/006.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/030.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/021.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/026.part   Tue Aug 16 09:22:12 2005
12450  DENY_WRITE 0x2019f     RDWR       NONE             /TEST/temp/009.part   Tue Aug 16 09:22:12 2005

What exactly is that? Is there any option to turn this off? I never saw this with SuSE. Thanks for your help

---

