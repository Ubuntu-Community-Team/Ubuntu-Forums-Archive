---
title: "Help I can not access shared folders, made by windows"
date: 2018-08-16
forum: General Help
---

### Post by darktobipy on 2018-08-16
good morning, I just installed Ubuntu 18.04.1 LTS, my problem is that I have another pc sharing folder, and from my linux I am not able to enter the folder, someone can give me a guide please

---

### Post by Mark Phelps on 2018-08-16
Are you trying to access a Windows folder from Ubuntu? If you're running Win10, that is not possible using the default Win10 setup because Windows keeps its filesystem mounted, even when not running, and that prevents Linux from opening that same filesystem.

---

### Post by QIII on 2018-08-16
Hello!

To add to that ...

It would be helpful if you would describe exactly what it is you are doing and exactly what behavior you are observing.  Your issue as stated is vague.  It would also be helpful if you would describe what you are attempting to illustrate with your image.

Cheers!

---

### Post by ghostis on 2018-08-16
Is the folder on a different PC on your network? In that case, you can use a CIFS mount. Something like:

```


mkdir -p ~/Mounts/computername_sharename

sudo mount -t cifs //computername/sharename /home/ubuntu_username/Mounts/computername_sharename --verbose -o username=windows_username,workgroup=WORKGROUP_FOR_WINDOWS_MACHINE,uid=ubuntu_username,gid=ubuntu_usergroup,file_mode=0700,dir_mode=0700,rw

Note: Replace computername, sharename, windows_username, ubuntu_username, ubuntu_usergroup, and WORKGROUP_FOR_WINDOWS_MACHINE with real values.


```

---

