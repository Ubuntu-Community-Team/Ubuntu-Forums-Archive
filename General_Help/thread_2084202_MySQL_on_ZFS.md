---
title: "MySQL on ZFS"
date: 2012-11-14
forum: General Help
---

### Post by henslok on 2012-11-14
I have a ZFS formated disks, the size is much bigger than system partition. I use to have partition mounted with *mount -t zfs tank/mysql /var/lib/mysql* After dist-upgrade mysql service is failing to start. I had to move files back to the system partition and leave /var/lib/mysql as per normal. Any ideas?
mysql server log:
> 121114 22:42:13 [Note] Plugin 'FEDERATED' is disabled.
121114 22:42:13 InnoDB: The InnoDB memory heap is disabled
121114 22:42:13 InnoDB: Mutexes and rw_locks use GCC atomic builtins
121114 22:42:13 InnoDB: Compressed tables use zlib 1.2.7
121114 22:42:13 InnoDB: Using Linux native AIO
121114 22:42:13 InnoDB: Initializing buffer pool, size = 128.0M
121114 22:42:13 InnoDB: Completed initialization of buffer pool
121114 22:42:13 InnoDB: highest supported file format is Barracuda.
121114 22:42:13  InnoDB: Operating system error number 22 in a file operation.
InnoDB: Error number 22 means 'Invalid argument'.
InnoDB: Some operating system error numbers are described at
InnoDB: [http://dev.mysql.com/doc/refman/5.5/en/operating-system-error-codes.html](http://dev.mysql.com/doc/refman/5.5/en/operating-system-error-codes.html)
InnoDB: File name ./ib_logfile0
InnoDB: File operation call: 'aio write'.
InnoDB: Cannot continue operation.


---

### Post by dajhorn on 2012-11-15
Setting the `innodb_use_native_aio` option should resolve this error. See this ticket:

  [https://github.com/zfsonlinux/zfs/issues/224](https://github.com/zfsonlinux/zfs/issues/224)

---

### Post by henslok on 2012-11-15
Thanks for quick and accurate response. Worked very well. Cheers.

---

