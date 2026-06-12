---
title: "write permssions in SMB share"
date: 2008-05-06
forum: General Help
---

### Post by rtptucks on 2008-05-06
I have just installed Ubuntu to a spare PC which has 2 addtional harddrives for storage, both are formatted with the ext3 file system

initially i had write problems locally on the pc so i changed owernship and write permisons with

sudo chmod -R 0777 /media/disk-1/
sudo chmod -R 0777 /media/disk/

i also made sure i was the correct owner using

sudo chown -R /media/disk-1 /
sudo chown -R /media/disk/

I updated Ubuntu with the lates updates and enabled SMB sharing so my windows system and media centre can see the share on the network.

Viewing the shares seem to be okay but when i write to them from my windows PC sometimes it will write and then after i have succesfully sent some files i will then try and write to another share and it says permission denied, even though i have the set the permission to allow other users to read & write?  say if i create a new folder and share i can then write to this but after writing i then get the same error?

I hope somebody has some ideas on how to fix this?

Many thanks in advance.

Wayne

---

### Post by rtptucks on 2008-05-07
Bump!!

this must be easy for you linux guru's!

---

### Post by rtptucks on 2008-05-07
someone told me

" oh dont worry if you get problems with Ubuntu, the forums are ace, people reply quick"

i guess either people dont know the fix or these forums are too  busy for people to notice my thread!

Guess ill have to go back to Windows if nobody is able to offer assitance?

---

### Post by bodhi.zazen on 2008-05-07
This is an odd problem. So if I am understanding you , samba shares work initially , but then fail ?

If that is the case, my guess would be some kind of network problem. Hard to know without more details though.

first, try windows -> windows shares and mount a windows share on ubuntu , see if the problem is isolated to Ubuntu.

Next add set a samba password on your ubuntu server for your ubuntu user. 

```
sudo  smbpasswd -a username
``` where "username" = your Ubuntu log in user.

Log out and back in to Ubuntu. Connect to Ubuntu from Windows using your ubuntu username and samba password.

---

### Post by rtptucks on 2008-05-07
windows shares seem to be fine

tried what you suggest

still same issues with Ubuntu the share seems intermitenet at the minute its not writing at all really.  windwos come back saying make sure you have permission or folder is not in use?

Any other ideas?

Regards

Wayne

---

### Post by bodhi.zazen on 2008-05-07
On the ubuntu machine, does the ubuntu user have permission to rw the shared directory ?

On the windows machine , are you using your ubuntu user name and ubuntu samba password to mount the share ?

You could try booting your windows box with a live CD, mount the share there, and list the ownership and permissions of the mounted share. You should see the share mounted as your ubuntu server user (ie not nobody nogroup).

---

