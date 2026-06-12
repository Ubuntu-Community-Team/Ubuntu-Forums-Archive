---
title: "Unable to open NAS folders on LG-NAS"
date: 2020-11-13
forum: General Help
---

### Post by ajbarefoot on 2020-11-13
I am using Ubuntu 20.04.1 LTS 64 bit. I have a Network Attached Storage device made by LG (LG-NAS) and though I can get in to where I can see the main folders, I cannot get them to open. I get "Unable To Access Location. Failed To Mount Windows Share: Software Caused Connection Abort". I have tried setting permissions and adding users and a new user group in the LG-NAS settings (through its HTML interface) but nothing I've done has helped. I triple boot Ubuntu 20.04.1 with Windows 7 and Ubuntu 18.xx (a customized version for ham radio operators) and Ubuntu 18.xx can open the NAS folders with no problem. Why 18.xx can and 20.04.1 cannot, I don't know. Can you tell me what to do? Thanks.

---

### Post by CelticWarrior on 2020-11-13
Welcome.

The differences are likely due to to the NAS using an old samba version which isn't currently supported in newer Ubuntu or Windows 10.

---

### Post by Morbius1 on 2020-11-13
> Unable To Access Location. Failed To Mount Windows Share: Software Caused Connection Abort.

As suggested above you will in fact get that error message if the server ( NAS in this case ) can only be accessed using the SMB1 dialect of samba.

You pretty much have two options:

[1] Override the default setting of the samba client on your Ubuntu box and force it to use SMB1 ( samba calls it NT1 just to be obscure ) as a minimum instead of SMB2.

Edit /etc/samba/smb.conf and right under the workgroup = WORKGROUP line add this one:
```
client min protocol = NT1
```
THen reboot your Ubuntu box.

Note: depending on how old the version of samba is on the NAS you may need to add another line under the first:
```
client lanman auth = yes
```
Reboot again.

Also note: You may not have a smb.conf file on your system if you have not installed the samba server package. If you don't want your Ubuntu system to act as a samba server you can get a smb.conf file by installing the samba client package:
```
sudo apt install smbclient
```

[2] Access the share on the NAS using mount.cifs and specify the earlier smb dialect there. 

Something like this for a temporary mount - you would have to add an equivalent declaration in fstab:
```
 sudo mount -t cifs //server/share /media/mountpoint -o guest,uid=1000,vers=1.0,sec=ntlm
```

I prefer this method myself since it is more reliable, doesn't need smb.conf, and bypasses any gvfs bugs present on your file manager. But it takes a bit to set up.

---

### Post by ajbarefoot on 2020-11-15
Editing samba.conf worked. I also changed WORKGROUP to my own workgroup name. Now I can access my NAS.
Thanks!

---

