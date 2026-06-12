---
title: "Samba Share Permissions - Can't access any password protected shares."
date: 2014-10-14
forum: General Help
---

### Post by trip5 on 2014-10-14
I'm having a tough time grasping how the file permissions work in ubuntu, especially with shared folders.  I have managed to configure a few shared folders within samba and I can connect from windows, mac, and other linux machines.  However I can only connect when I leave the permissions all the way "open".  What I want to be able to do is configure shared folders that require a username and password.  Eventually I want to integrate with windows AD, but for now I just want to have a few secured folders.  Any help is much appreciated.  Here is how I have configured my open shares:

[Share]
    comment = Ubuntu File Share
    path = /home/user/share/public
    browseable = yes
    guest ok = yes
    read only = no
    create mask 0755

---

### Post by TheFu on 2014-10-14
Samba shared folders don't really have much to do at all with normal Linux file/directory permissions.  

If you use the GUI to share stuff via samba, don't expect much control.
If you use the /etc/samba/smb.conf file to share stuff via samba, expect nearly complete control.

I use the **valid users =** setting and you can use netgroups if using NIS.  Don't know anything about AD integration, but suspect sharing HOME directories on a per-user basis would be relatively easy.  It is under normal Samba ... but that sort of sharing is only for 1 user to 1 directory, not so much for multiple users.

Here's my HOME directory sharing stanza:

```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.0/24 
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S

```
Is it good for data, not programs/scripts. "homes" is a special case. For other directories, change the stanza name, add the **path =** and force a specific group with 0664 create-mask.

Oh - and don't share a directory with multiple users under /home/joe/. That is a bad idea.  Make that storage outside /home to prevent one user from screwing with access to everyone else. Don't allow guests.

Hope this all makes sense.

---

### Post by trip5 on 2014-10-14
Thanks for the response!  I'm using the smb.conf file to configure.  I pasted in the code that you shared just to test, I get the windows username and password window now but no combination of usernames or passwords works.

---

### Post by TheFu on 2014-10-14
You must initialize the smbpasswd db - use **smbpasswd {insert-user-id-into-this-and-remove-curly-brackets}**  Depending on the [Global] section, passwords will sync AFTER an account is added the first time.

If you didn't add the userid to the smbpasswd db already - it doesn't know which userids to allow via samba and which userids NOT to allow via samba.  Make sense?

---

### Post by jamesisin on 2014-10-14
It is also important to note (since no one mentioned it explicitly) you must have both permissions to access the share via SMB (presumably through the smb.conf file) as well as having Linux permissions for the files and folders (though the OS on the server).

---

