---
title: "Win usb gives me error Exit code: 256"
date: 2016-06-19
forum: General Help
---

### Post by Alucard_De_Rosier on 2016-06-19
Installation failed !

```
Exit code: 256
Log:
Formatting device...
Wait 3 seconds for block device nodes to populate...
mkfs.fat: warning - lowercase labels might not work properly with DOS or Windows
mkfs.fat 3.0.28 (2015-05-16)
Mounting...
mount: /dev/loop1 is write-protected, mounting read-only
Copying...
Error occured!
Syncing...
Cleaning...
/usr/bin/winusb: line 78:  8518 Terminated              while true; do
    sleep 0.05; echo 'pulse';
done
Unmounting and removing '/media/winusb_iso_1466358007_4995'...
Unmounting and removing '/media/winusb_target_1466358007_4995'...
```

---

### Post by yancek on 2016-06-19
It appears from the limited info you posted that you are trying to create a bootable usb with some windows on it.  If that's the case, try the suggestions at the link below.

[http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by grahammechanical on 2016-06-19
Are you trying to install Windows USB drivers in an installation of Ubuntu? We do not do that.

[https://msdn.microsoft.com/en-gb/library/windows/hardware/ff540283(v=vs.85).aspx](https://msdn.microsoft.com/en-gb/library/windows/hardware/ff540283(v=vs.85).aspx)

Regards.

---

