---
title: "Accessing ubuntu drive on a network laptop running Windows 8"
date: 2013-12-14
forum: General Help
---

### Post by ccdavis77 on 2013-12-14
Hello...I am running Ubuntu 13.1 on my media center htpc and want to be able to access these files on my network laptop running Windows 8 to edit music tags,etc.  I have tried mapping the network drive to no avail. Is there a tutorial somewhere on how to do this?; I can't seem to find one...thanks for any help!

---

### Post by SeijiSensei on 2013-12-15
You need to be running [Samba]("https://help.ubuntu.com/community/Samba/SambaServerGuide") on the htpc to share folders with Windows clients.

---

### Post by ccdavis77 on 2013-12-15
after some more searching RE having problems getting Samba to work ([http://askubuntu.com/questions/288229/i-just-upgraded-to-13-04-and-samba-isnt-working-it-is-installed-but-will-not-o)...finally](http://askubuntu.com/questions/288229/i-just-upgraded-to-13-04-and-samba-isnt-working-it-is-installed-but-will-not-o)...finally) got it working...thanks!

---

### Post by sammyp90 on 2013-12-15
you installed samba on your ubuntu machine? if so you will need to edit /etc/samba/smb.conf to add the path/permissions of the files/folders you want to share

---

### Post by jimmyh1972 on 2013-12-17
install & config samba (file sharing for windows clients)

[https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

---

