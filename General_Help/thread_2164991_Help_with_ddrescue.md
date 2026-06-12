---
title: "Help with ddrescue"
date: 2013-08-02
forum: General Help
---

### Post by c-m on 2013-08-02
A speaker fell onto my my 1TB 2.5" drive recently and resulted in the drive not working correctly.

The drive powers on and all partitions show up in Disk, but they do not mount. the main partition is at dev/sdc3 and is around 900GB.

It an NTFS partition and I can mount it from the command-line and even browse a few directories before I get an I/O error.

I've bought a new 1TB 2.5" drive, and plan to use ddrescue to try and recover date from the drive.

Are the options given in the commands on the wiki the best to use?
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

e.g.

```
sudo ddrescue -r 3 /dev/sda /media/usbdrive/image /media/usbdrive/logfile

```

I have started the process and so far it says it rescued over 600GB. IPOS and OPOS read also read 600GB whatever that means, and errorsize and errors are being reported as 0 bytes.

Does that sound like ddrescue is doing the job of recovering the data?

---

### Post by TheFu on 2013-08-02
yep. Sounds like you are lucky.
Having a backup would probably have been easier, however.

---

### Post by c-m on 2013-08-03
> **TheFu said:**
> yep. Sounds like you are lucky.
Having a backup would probably have been easier, however.

I did. Technically I still do, on a 1TB WD caviar green. Unfortunately this drive failed within an hour of me finding out about 1TB 2.5" drive.

Typical.

---

