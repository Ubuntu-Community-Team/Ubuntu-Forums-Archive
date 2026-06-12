---
title: "Is this a job for... NSF ?"
date: 2006-10-11
forum: General Help
---

### Post by newmonkey on 2006-10-11
I use four or five computers on a daily basis (all Linux). My laptop, my desktop, my work computer and a computer at the library. Unfortunately, this leaves my personal files all over the place, and while FTP is suitable, it's really not ideal to have to download, edit and upload files every time I change computers.

What's the best way for me to set up a network file server so that I can always have access to mounted files? Is this a job for NSF, or would that be a permissions nightmare to have four computers potentially reading (and/or writing) to the same fileshare simultaneously?

Any thoughts would be greatly appreciated!

---

### Post by Kateikyoushi on 2006-10-11
We also use windows on 2 machines so I solved it with [Samba]("https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29"). I can connect 2 ubuntu OSes very easily.

---

### Post by meng on 2006-10-11
I have a pure Ubuntu network at home and I still use Samba, although NFS is an alternative.

---

### Post by newmonkey on 2006-10-11
Maybe I'll give Samba a shot :)

Thanks

---

### Post by crazymonkey on 2006-10-11
If you are concerned about security i would suggest using sshfs. It allow you to mount folders trough ssh. I have yet to find a howto about it and maybe i will make one soon. I find it much easier to use since you only need ssh on the server side. I'll keep you updated with my howto (maybe tomorrow).

EDIT: [HOWTO:sshfs]("http://www.ubuntuforums.org/showthread.php?t=275856")

---

