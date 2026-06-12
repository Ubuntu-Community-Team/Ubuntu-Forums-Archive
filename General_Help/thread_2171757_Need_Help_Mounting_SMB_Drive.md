---
title: "Need Help Mounting SMB Drive"
date: 2013-09-01
forum: General Help
---

### Post by rob_b2 on 2013-09-01
Hey Guys hopefully someone can help me out here. After pretty much an entire day of googling I still can't seem to find out what is going wrong with what I am doing. All I want to do is mount an SMB drive. I had it working but once I rebooted I lost it and I have not been able to get it back. I wrote this line in /etc/fstab

//10.0.1.1/AIRDRIVE  /mnt/airdrive  cifs  username=msusername,password=mspassword,iocharset=utf8,sec=ntlm  0  0
(with the correct user and pass in there)

but when i type "sudo mount -a" it just hangs I get nothing. No error i can't ctrl-x out. I get nothing. 

If I do

"smbclient //10.0.1.1/AIRDRIVE/ -U username"

I get 

Domain=[WORKGROUP] OS=[Apple Base Station] Server=[CIFS 4.32]
smb: \>

and I get see and edit all of the files on the SMB drive. So I can definitely access the drive but I just can't mount it. Any suggestions on what I could be doing wrong? Like I said i did get it to work once using "sudo mount -a" but lost it after a reboot. I haven't changed anything in fstab since then so whatever is in there did work at some point.

---

### Post by TheFu on 2013-09-02
No spaces in the options. Remove those.

Also, it is poor security to put a password in a file that can be read by the entire world, as /etc/fstab can.

---

