---
title: "CIFS VFS: Free previous auth_key.response = ffff8f9c38a1aa00"
date: 2017-12-22
forum: General Help
---

### Post by malliman on 2017-12-22
Hey Guys,

I have a server that is running Ubuntu 17.10 and have started getting this error message ```
CIFS VFS: Free previous auth_key.response = ffff8f9c38a1aa00
```. I was wondering if anyone has seen this Or any idea on how to fix it 

Thank You,
Matt

---

### Post by apinky79 on 2017-12-23
> **malliman said:**
> Hey Guys,

I have a server that is running Ubuntu 17.10 and have started getting this error message ```
CIFS VFS: Free previous auth_key.response = ffff8f9c38a1aa00
```. I was wondering if anyone has seen this Or any idea on how to fix it 

Thank You,
Matt

I'm having the same trouble its driving me mad

---

### Post by malliman on 2018-01-02
Anyone have any ideas it is a driving me nuts and trying to figure out if it is related to another issue that i am having. as far as I can tell it has something to do with the samba mounts to windows. here is my fstab information?
```

//hhmh-shared/Shared          /mnt/s-drive            cifs            username=linuxsmb,password=Removed,rw,nounix,file_mode=0777,dir_mode=0777,vers=2.0,iocharset=utf8 0 0
//hhmh-shared/Home            /mnt/h-drive            cifs            username=linuxsmb,password=*Removed*,rw,nounix,file_mode=0777,dir_mode=0777,vers=2.0,iocharset=utf8 0 0

```

---

### Post by malliman on 2018-01-02
Ok, Think i have figured it out if you change vers=3.0 the message has gone away

---

### Post by malliman on 2018-01-09
Ok that did not fix it any one else have an idea of what is going on?

---

### Post by stuart.paterson18 on 2018-04-04
Hi Malliman, did you ever get a fix for this...I'm experiencing this error on my Ubuntu server (v16.04.4 LTS)

The only windows mount I have is over smb2 to a Server 2008 r2 box which is working fine, just this annoying pop up warning.

Thanks
Stuart

---

### Post by nraygun on 2018-04-04
I get it too on a clean Xubuntu 16.04.4 install. There's mention of a patch here but it seems like it's coming in 4.13.5. Am I reading that correctly?

[https://www.systutorials.com/linux-kernels/59092/cifs-release-auth_key-response-for-reconnect-linux-4-13-5/](https://www.systutorials.com/linux-kernels/59092/cifs-release-auth_key-response-for-reconnect-linux-4-13-5/)

Anyone find a workaround?

---

### Post by nraygun on 2018-05-02
Anyone get this one solved?

---

### Post by nraygun on 2018-05-13
I've since upgraded to 18.04 and changed my Win10 machine back to SMBv1 for the shares and this error/warning goes away. Not optimal, but close enough.

---

