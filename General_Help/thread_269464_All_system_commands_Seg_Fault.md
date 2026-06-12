---
title: "All system commands Seg Fault"
date: 2006-10-01
forum: General Help
---

### Post by faceoftheearth on 2006-10-01
I just tried to install/configure open-afs on Dapper using [this]("http://doc.kom.aau.dk/software/unix_software/afs_on_linux/tbd_afs_on_ubuntu/"). The process seemed to work, however upon attempting to restart the open-afs client I got "Segmentation Fault." I thought that was strange, but not exactly out of the ordinary for attempts at using Linunx constructively to fail miserably. However, the problem is that now everyting seg faults. I type sudo shutdown -r now because compiz got rid of my restart buttons and that'll seg fault. All apt commands seg fault. I've narrowed it down to every command I try to do using sudo will seg fault. EG: 'sudo ls' will result in a segmentation fault. What can I do? I'm afraid if I restart this will be a hosed Linux install suddenly and I'll just go back to Windows like I have in the past. 

Thanks!

---

### Post by Mr Frosti on 2006-10-01
When you performed the installation of new software were any dependencies listed? I have seen segmentation faults occur if the kernel was upgraded, and headers were not. Was anything involving "kernel" listed in your terminal?

---

### Post by faceoftheearth on 2006-10-01
The thing is that I didn't actually install anything new. I had installed afs before using the same guide. Nothing had changed , but the afs system wasn't working any longer. The only part I did this time was the modules. This includes the depmod -a section. If I have a problem with my linux headers, what can I do since no sudo commands work?

---

