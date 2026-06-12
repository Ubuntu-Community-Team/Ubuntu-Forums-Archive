---
title: "mount windows share help"
date: 2012-11-13
forum: General Help
---

### Post by bilboubu on 2012-11-13
I put this in my fstab which works fine:
//192.168.0.2/Media3/recordings /home/billy/oscar cifs username=Billy,password=yessir,billy,uid=1000,gid=1000,iocharset=utf8,mode=0777,dir_mode=0777 0 0

But both my windows server and ubuntu machine are set to sleep. My ubuntu wakes my windwows server via a wake on lan command when it resumes from sleep.

Is there another way I should be mounting this other than using the fstab.

Since the fstab entry sometimes the ls command stops working and winscp stops working and I have to reboot.

Maybe I should be mounting/unmounting with a suspend resume script?

---

### Post by kiasta on 2012-11-13
I sure hope that is not your real username/password. Just pointing that out to you.

---

### Post by bilboubu on 2012-11-13
thank you, no it is not my real password.

---

