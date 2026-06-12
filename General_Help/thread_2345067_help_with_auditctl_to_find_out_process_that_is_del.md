---
title: "help with auditctl to find out process that is deleting a file"
date: 2016-11-30
forum: General Help
---

### Post by NotQuiteSU on 2016-11-30
I have a file which is somehow being deleted from a directory. I'm trying to determine if it is a local process or remote host via smb. I'm pretty new to auditctl, so I'm not sure if I set it up right since I can't see the file being deleted.

```
 auditctl -w /FilePath/ -k TESTKEY
```

when I do ```
aureport -i -f | less
```

```

247. 11/29/2016 17:20:19 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 659
248. 11/29/2016 17:20:19 PATH/PARENTDIR open yes /usr/sbin/smbd unset 660
249. 11/29/2016 17:20:19 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 661
250. 11/29/2016 17:20:19 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 662
251. 11/29/2016 17:20:19 PATH/PARENTDIR open yes /usr/sbin/smbd unset 663
252. 11/29/2016 17:20:19 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 658
264. 11/29/2016 18:59:32 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 702
265. 11/29/2016 18:59:32 PATH/PARENTDIR open yes /usr/sbin/smbd unset 703
266. 11/29/2016 18:59:32 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 704
267. 11/29/2016 18:59:32 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 705
268. 11/29/2016 18:59:32 PATH/PARENTDIR open yes /usr/sbin/smbd unset 706
269. 11/29/2016 18:59:32 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 701
279. 11/29/2016 19:20:25 PATH/PARENTDIR open yes /usr/sbin/smbd unset 724
322. 11/29/2016 22:05:14 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 797
323. 11/29/2016 22:05:14 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 798
324. 11/29/2016 22:05:14 PATH/PARENTDIR open yes /usr/sbin/smbd unset 799
416. 11/29/2016 23:11:50 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 918
417. 11/29/2016 23:11:50 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 919
418. 11/29/2016 23:11:50 PATH/PARENTDIR open yes /usr/sbin/smbd unset 920
469. 11/30/2016 01:07:34 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 1002
470. 11/30/2016 01:07:34 PATH/PARENTDIR open yes /usr/sbin/smbd unset 1003
471. 11/30/2016 01:07:34 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 1004
472. 11/30/2016 01:07:34 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 1005
473. 11/30/2016 01:07:34 PATH/PARENTDIR open yes /usr/sbin/smbd unset 1006
474. 11/30/2016 01:07:34 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 1001
489. 11/30/2016 05:25:59 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 1070
490. 11/30/2016 05:25:59 PATH/PARENTDIR open yes /usr/sbin/smbd unset 1071
491. 11/30/2016 05:25:59 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 1072
492. 11/30/2016 05:25:59 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 1073
493. 11/30/2016 05:25:59 PATH/PARENTDIR open yes /usr/sbin/smbd unset 1074
494. 11/30/2016 05:25:59 PATH/PARENTDIR getxattr no /usr/sbin/smbd unset 1069

```

is auditctl blind to commends that occur via smb? so I have to run auditctl on the remote host?

---

