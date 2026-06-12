---
title: "[SOLVED] networking"
date: 2008-06-21
forum: General Help
---

### Post by poliltimmy on 2008-06-21
I have been using ubuntu for a while. As a single machine OS it's great, love it but, networking to my kids windows computer has been a nightmare. i get as far as the mshome icon then it will not show the shared folders. I have a wired network through a linksys befsr41-vn v.2 and a motorola cable modem. At one time i could see and get into my ubuntu machine from the windows but not into windows from ubuntu. I have downloaded samba, tried numerous theads and command walk throughs. Nothing works. I need help bad! All I want is to be able to share files with them. Is there a good thread or walk through that can solve my problem? If so I would really appreciate a link or two. 
                                      thanks, timmy

---

### Post by geirha on 2008-06-21
I stay away from smb as much as possible, but when I occationally need to access a windows share, I've noticed that browsing to it using nautilus or smbclient doesn't always work very well. Mounting it manually, seems to work better. 

So try the following in a terminal.
```

sudo aptitude install smbfs  # in case that package isn't installed allready
sudo mount -t cifs //10.0.0.1/share /mnt
ls -l /mnt/

```

Change 10.0.0.1 with the actual ip-address of the windows machine, and "share" with the actual name of a shared folder (That was probably obvious already :) )
If you need to specify a username and password, add "-o username=the_user_name" to the mount command. i.e. ```
sudo mount -t cifs -o username=the_user_name //host/share /mnt
```

---

### Post by poliltimmy on 2008-07-03
Either I keep doing something wrong or just am not up to the task. rouer is broke now so I will try again when I get a new one...like I really care if the kids are disconnected..LOL.   Thanks, Timmy

---

