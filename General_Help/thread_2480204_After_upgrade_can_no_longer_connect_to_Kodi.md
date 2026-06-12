---
title: "After upgrade can no longer connect to Kodi"
date: 2022-10-22
forum: General Help
---

### Post by Evil Wayz on 2022-10-22
I have a kodi box connected to my local network.  Near as I can figure, after the latest kernel upgrade I can't connect to it anymore.  For awhile networking didnt work at all, ive got it to see the other shares but it wont connect to them.  Ive tried raising the samba protocol level to smb3 on the Kodi box but that doesn't seem to be helping.  This is highly inconvenient.  I can connect to the server with my phone and my laptop so thats not the problem.  Also I can't ssh or ftp into the ubuntu computer anymore it times out.

I am using Ubuntu Studio 22.04.

---

### Post by #&amp;thj^% on 2022-10-22
Not sure if I can help you, but have you set a static IP for kodi?
I'm not using Ubuntu ATM, but I've seen what your now going through and I installed the flatpak version and all is well again.
[https://flatpak.org/setup/Ubuntu](https://flatpak.org/setup/Ubuntu)

---

### Post by Evil Wayz on 2022-10-23
Sorry for the confusion, the kodi box is a raspi4 on the local network.  Samba claims to be working but i cant see or access the kodi box.  I can access it from my laptop and my phone so the desktop is hosed.  I cant ftp or ssh in. But its connected to the internet. 

Can i just delete the smb.conf file and start over? I got the bright idea to upgrade to 22.10 but its still broken.

---

### Post by Evil Wayz on 2022-10-25
Ok the problem is definitely in the ubuntu pc.  I remove/purged samba and then reinstalled it. Samba status is up. But I can't see any shares except the ones local to the computer, and i just discovered I can't SSH into it either.

---

### Post by #&amp;thj^% on 2022-10-25
Around a year ago Morbius1 had to remind me to add this if not already there:
```

server min protocol = NT1
```

to "/etc/samba/smb.conf " >> under the workgroup = WORKGROUP line

I ended up adding two lines in there as:
```
client min protocol = NT1
server min protocol = NT1
```
Also related : [https://twosortoftechguys.wordpress.com/2020/08/16/if-you-have-reinstalled-kodi-in-ubuntu-and-it-will-no-longer-connect-to-your-media-server-or-nas-using-smb-samba-try-this/](https://twosortoftechguys.wordpress.com/2020/08/16/if-you-have-reinstalled-kodi-in-ubuntu-and-it-will-no-longer-connect-to-your-media-server-or-nas-using-smb-samba-try-this/)

---

### Post by Evil Wayz on 2022-10-31
my smb.conf is blank. How do i generate a new one?

---

