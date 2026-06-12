---
title: "how to reach a flashdisk form terminal"
date: 2008-04-13
forum: General Help
---

### Post by d_deniz on 2008-04-13
I have a problem and the computer opens only a terminal
and I want to copy my data and format my computer
I know I should use "move" or similar command for this situation but my problem is about the direction of the flash disk
I dont know where it is 
what is the direction of a inserted flash disk?
what is the way to copy a file into this flash disk by using terminal?

---

### Post by d_deniz on 2008-04-13
the title should be *from flash disk,

---

### Post by sekinto on 2008-04-13
What is the output of "ls /media"?

---

### Post by d_deniz on 2008-04-13
```
[COLOR="Cyan"]cdrom[/COLOR] [COLOR="Blue"]cdrom0[/COLOR]
```

---

### Post by d_deniz on 2008-04-13
and when I got into these directories and looked into them by "ls -l" it says" total 0"

---

### Post by sekinto on 2008-04-13
Looks like Ubuntu isn't mounting your flash drive.
If it is a USB flash drive tell me the output of "lsusb".

---

### Post by d_deniz on 2008-04-13
```

Bus 003 Device 005: ID 0930:6354 Toshiba Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 09da:000a A4 Tech Co., Ltd
Bus 001 Device 001: ID 0000:0000

```

---

### Post by d_deniz on 2008-04-13
a4 tech is my mouse and the flash disk is kingston, it may be toshiba... thing there

---

### Post by d_deniz on 2008-04-13
but I dont know

---

### Post by sekinto on 2008-04-13
What is the output of: dmesg | grep -i "SCSI device"

---

### Post by d_deniz on 2008-04-13
it didn't give an output and it didn't change previous outputs

---

