---
title: "User able to access Samba share through smbclient, but not through fstab mount"
date: 2019-09-17
forum: General Help
---

### Post by pastorjeremywilson on 2019-09-17
I'm having troubles mounting a Samba share for another user on this  computer. Let's call him "regularuser". He's on a client computer  running Ubuntu 16.04LTS and Ubuntu Desktop. The share is on a CentOS  machine, served through Samba. Regularuser can use smbclient to access  the share (i.e. smbclient //192.168.0.xx/share -U regularuser  [password]) with no problems. However, when I set up an fstab entry to  mount that share in his home directory, he gets a "mount error(13):  permission denied" error when he clicks on it in the file manager.
  I'll try to make this as logical as possible, but I'll be jumping around a bit. Here's what the fstab entry looks like:

  ```
//192.168.0.xx/share /home/regularuser/share cifs credentials=/home/regularuser/.smbcredentials,noauto,x-systemd.automount,uid=regularuser,gid=regularuser,users 0 0

```  and the .smbcredentials file is simply:
  ```
username=regularuser
password=password

```  This is the exact same method I use on my own account, "adminuser" on  this client computer. Works fine. But here's something that I can do to  make the mount work for "regularuser": if I change the .smbcredentials  file in his home directory to use my credentials instead - username=adminuser password=mypassword - without changing fstab, he can access the  share just fine. Which is OK for now, but I'd rather not have my  credentials sitting in a file under his userhome.
  That leads me to think that maybe there's something up with his  access in Samba on the server. But wouldn't that mean he also wouldn't  be able to log in through smbclient? I was already sure to add him as a  user on the server with the same password as on the client computer, and  added him to Samba using smbpasswd using the same password. This has  got me confused. I'll also include my smb.conf file. Well, not all of  it, but the settings and this share anyways:
  ```
[global]

 # ----------------------- Network-Related Options -------------------------
    workgroup = LBCNWORKGROUP
    server string = Samba Server Version %v
    server max protocol = SMB2
    netbios name = lbcn-server.lan

 # --------------------------- Logging Options -----------------------------
    log file = /var/log/samba/log.%m
    max log size = 50

 # ----------------------- Standalone Server Options ------------------------
    security = user
    passdb backend = tdbsam

 #----------------------------- Name Resolution -------------------------------
    wins support = yes
    name resolve order = wins lmhosts

 # --------------------------- Printing Options -----------------------------
    load printers = yes
    cups options = raw
    rpc_server:spoolss = external
    rpc_daemon:spoolssd = fork

 # --------------------------- File System Options ---------------------------
    access based share enum = yes
    browseable = yes
    acl allow execute always = yes
 #============================ Share Definitions ==============================
[Share]
    comment = Share
    path = "/home/adminuser/shares/Share"
    valid users = adminuser, regularuser
    writable = yes
    read only = no
    guest ok = no
    create mask = 0777
    directory mask = 0777
    force user = adminuser

```  Some things I've tried so far: I've already tried adding the osec= option in fstab. No good. I've tried adjusting the fstab entry to read uid=adminuser,gid=adminuser  instead. No good. I've changed .smbcredentials to my credentials  instead. That worked, but I don't like it. Removed and recreated the  user on Samba. No Change. I've also made sure that regularuser is part  of the "shareusers" group on both machines as well (which is the group I  use to set permissions on the server). There's got to be something I'm  missing. Is it because his account was created as a "Regular User" in  Ubuntu, maybe? Any other ideas?

---

### Post by Morbius1 on 2019-09-18
It will take me a bit to try to see why what you are doing doesn't work. I would need to try to reproduce it on a test system.

But I have a suggestion in the mean time if you are interested. Reverse the responsibility of who can access the share - at least from your client box - to the client.

You posted that you have a group ( shareusers ) on the client that both users are members of and that the share on the server specified a "force user" to adminuser so as far as the server is concerned everything is done as that user.

If you were to change your mount expression in fstab to something like this:

```
//192.168.0.xx/share [COLOR=#0000cd]**/mnt/share**[/COLOR] cifs [COLOR=#0000cd]**credentials=/etc/samba/.smbcredentials**[/COLOR][COLOR=#0000cd]**,gid=shareusers,dir_mode=0770,file_mode=0660,nounix**[/COLOR],noauto,x-systemd.automount,users 0 0
```

/etc/samba/.credentials = would contain adminusers credentials.
You would chmod the file to 600 so only root could gain access.

/mnt/share = would exist outside of either users home directory - you can create a bookmark so it shows up in the file manager.

The permissions of the mounted share would be 770 with group = shareusers so you would be able to control who has access to the server - from your client - by controlling who is a member of the shareusers group on the client.

---

### Post by pastorjeremywilson on 2019-09-18
Thank-you for the idea! I'll give that a shot and see how it goes.

---

### Post by pastorjeremywilson on 2019-09-18
Worked like a charm, thanks! Plus, it locked up the .smbcredentials file from being read by the user. I wasn't sure if changing the permissions on that file to be so restrictive would prevent fstab from reading it correctly, so I'm really glad you mentioned it. Still curious as to why it's inaccessible the other way, but if this is the way I keep it from here on out, I'm happy as a clam!

---

