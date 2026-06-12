---
title: "Samba denied Subfolders"
date: 2016-01-21
forum: General Help
---

### Post by ptmuldoon on 2016-01-21
I recently ran apt-get update and apt-get upgrade on my Ubuntu 14 Server.

Now for some strange reason, I can no longer access the subfolders on a mapped share from my windows machine.  I know its a risk using Anonymous but there is nothing really on this particular VM.  Below is part of the smb.conf settings.

And I can map to the folder/root just fine.  But I get access denied when trying any subfolder?

```

security = share

[Anonymous]
path = /
browseable = yes
writable = yes
guest ok = yes
read only = no

```

Can anyone help identify why I would be locked in the root folder?

---

### Post by QDR06VV9 on 2016-01-21
Sometimes this happens I don't know why..But have you tried this yet
Type
```
gksudo nautilus
```
navigate to the shared folder and share it again. Share the folder but do not give guest access. Close nautilus.
Go to your Windows box and access the share and provide the Ubuntu username and password.


Ensure your Ubuntu firewall allows incoming access to Samba ports. Ensure Windows firewall allows outgoing access for the same ports.
Hope that helps

---

### Post by bab1 on 2016-01-21
> **ptmuldoon said:**
> I recently ran apt-get update and apt-get upgrade on my Ubuntu 14 Server.

Now for some strange reason, I can no longer access the subfolders on a mapped share from my windows machine.  I know its a risk using Anonymous but there is nothing really on this particular VM.  Below is part of the smb.conf settings.

And I can map to the folder/root just fine.  But I get access denied when trying any subfolder?

```

security = share

[Anonymous]
path = /
browseable = yes
writable = yes
guest ok = yes
read only = no

```

Can anyone help identify why I would be locked in the root folder?
Samba updated the security via the update.  

Why share the root of the file system anyway?  The SMB resource is always //server/shared-directory.  You should be able to browse the network and see the individual share and click on that.  There is no need to share a folder inside another shared folder (nested shares).

Can you browse for Samba (SMB/CIFS) shares?

---

### Post by ptmuldoon on 2016-01-21
> **runrickus said:**
> Sometimes this happens I don't know why..But have you tried this yet
Type
```
gksudo nautilus
```
navigate to the shared folder and share it again. Share the folder but do not give guest access. Close nautilus.
Go to your Windows box and access the share and provide the Ubuntu username and password.

Ensure your Ubuntu firewall allows incoming access to Samba ports. Ensure Windows firewall allows outgoing access for the same ports.
Hope that helps

Since I'm using Ubuntu Server,  I don't have a GUI and can't seem to get any of the above to work.  

> **bab1 said:**
> Samba updated the security via the update.  

Why share the root of the file system anyway?  The SMB resource is always //server/shared-directory.  You should be able to browse the network and see the individual share and click on that.  There is no need to share a folder inside another shared folder (nested shares).

Can you browse for Samba (SMB/CIFS) shares?

I am mapping the share to the root folder on a Windows machine. This way i can use a text editor and navigate to places like /etc/init.d to update any startup scripts, as well to some other places to modify some config files that are being use for OpenHab and some Home Automation Scripts.

Currently, i'm still sruggling to get the mapped share to the root directory to navigate to the subfolders.  Yet if I do set smb.conf to look at something like '/myshare/' I can nagivate subfolders.  Seems strange, but i'm by far not a linux/ubuntu guy and learn most by googling and searching.

I'll keep trying to figure out, but any other suggessions and help is appreciated.

Thanks
PT

---

### Post by bab1 on 2016-01-21
> **ptmuldoon said:**
> Since I'm using Ubuntu Server,  I don't have a GUI and can't seem to get any of the above to work.  

I am mapping the share to the root folder on a Windows machine. This way i can use a text editor and navigate to places like /etc/init.d to update any startup scripts, as well to some other places to modify some config files that are being use for OpenHab and some Home Automation Scripts.

This is really an inefficient way of doing business.  You are much safer and stable to use SSH to connect and then navigate by the terminal to the proper directory.  You can then use **sudo** to switch to the root user account to edit the files.  Root is the only user that can edit these files but a normal user can be part of the sudoers group.  Folks call that user an administrator.  
> 

Currently, i'm still sruggling to get the mapped share to the root directory to navigate to the subfolders.  Yet if I do set smb.conf to look at something like '/myshare/' I can nagivate subfolders.  Seems strange, but i'm by far not a linux/ubuntu guy and learn most by googling and searching.

I'll keep trying to figure out, but any other suggessions and help is appreciated.

Thanks
PT
I can see why you would think that it would be nice to use a GUI to manage the non-GUI server, but Samba is not good for that purpose.  If you must use a GUI then use WinSCP to connect.  This uses SSH in the form of SFTP.  You can connect and browse the folders.  I believe you can edit the live files.

---

