---
title: "Samba not letting me sign in"
date: 2016-05-21
forum: General Help
---

### Post by mitch24 on 2016-05-21
Hey guys, 

I've just downloaded Samba for my Ubuntu machine currently running 15.10 and i've set it up, done the configuration file and I can pick it up from my Windows 7 machine but when I click on the shard folder it asks me for a username and password. I try the username and password for both computers and nothing works.... i've turned off needing a password for folder sharing (but that doesn't work because the shared file is on my Ubuntu machine). Is there some kind of default username and password for this or is there something I can add or remove from the smb.conf file so I can access the shared folder? 

Thanks in advance!

---

### Post by Linuxisfast on 2016-05-21
sudo pdbedit -a -u username which should be yours here. Then it will ask for sudo password and then finally new password for samba user thats different than root password. After that sudo systemctl start smbd.service nmbd.service and it should work using the newly created password.

---

### Post by mitch24 on 2016-05-21
you're a legend mate! it worked!

---

### Post by Linuxisfast on 2016-05-21
> **mitch24 said:**
> you're a legend mate! it worked!


Welcome :)

---

