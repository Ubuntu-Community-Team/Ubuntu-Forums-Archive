---
title: "Mapping A Network Drive?"
date: 2008-01-07
forum: General Help
---

### Post by matey3 on 2008-01-07
I need some missing files for my backup server from the main server which is connected to eth2 but invisible to me? I want to cp from the server that has the files. Can someone tell me how I could do that?

Do I map first or can I just use cp command? the IP is 10.0.1.5 (the server with the needed files).
Or should I do a map first?
I tried mount //10.0.1.5:dev/vg1/  but to no avail... it complains about no mention in fstab etc..? (the files are in vg1 directory)  . no telnet or ftp available on neither...
thanks...

---

### Post by danwood76 on 2008-01-07
Mounting the share will be like mapping it as mounting it makes it act like another file on your system, although you are using the mount command wrong.

it goes like: mount -t 'type' 'source' 'destination' 'options'

so if I wanted to mount an smb share from //danwood76/share to /media/share I would do:

sudo mount -t smbfs //danwood76/share /media/share

that command is not quite complete as the smbfs requires some other options also.

what sort of filesystem are your files located on?

regards,
Danny

---

### Post by twistedtwig on 2008-01-07
can you ssh onto that box?  I would do the cp over ssh personally.  I use rsync over ssh to backup files from my server onto Ubuntu another computer

---

### Post by notwen on 2008-01-07
Haven't tried this before, but reading over what you're wanting to do reminded me of [this]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#SSH_Filesystem"). =]  Hope it helps and good luck.

---

### Post by kavoura on 2008-01-08
I have a Network Attached Storage device on my LAN. I would like to mount the drives on that to Ubuntu, so that they can easily be accessed from any program.
I have done it previously using Xandros, but as I am now using Ubuntu, it is quite different for things like that.

I tried entering 
```
sudo mount -t smbfs "//lkgd71990/DISK 1" /media/nas1
```
but it failed, with the error message as follows:
```
mount: wrong fs type, bad option, bad superblock on //lkgd71990/DISK 1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

When I enter   ```
dmesg | tail
```   I get
```
[21658.738688] : Add. Sense: Medium not present
[21658.738691] end_request: I/O error, dev sr1, sector 0
[21658.739257] sr 1:0:1:0: [sr1] Device not ready: <6>: Sense Key : Not Ready [current]
[21658.739261] : Add. Sense: Medium not present
[21658.739265] end_request: I/O error, dev sr1, sector 4
[21658.744831] floppy0: disk absent or changed during operation
[21658.744841] end_request: I/O error, dev fd0, sector 0
[21658.745011] floppy0: disk absent or changed during operation
[21658.745014] end_request: I/O error, dev fd0, sector 0
[22022.092779] smb_fill_super: missing data argument
```

So how can I mount the NAS drive into Ubuntu?

---

### Post by matey3 on 2008-01-10
Thank you guys very much for replies.
it was a great help!

---

### Post by deejross on 2008-01-10
Kovoura,

I don't know if you have done this or not, but make sure you have installed smbfs by:
```
sudo apt-get install smbfs
```

---

### Post by kavoura on 2008-01-10
I did not think of that, I just assumed that smbfs would have been installed when I installed samba.

Well, I installed smbfs and now mounting the network drives works.

Thanks for your help.

---

### Post by kavoura on 2008-01-13
I still have a problem mapping network drives. I can enter the command in the console
```
sudo mount -t smbfs "//lkgd71990/DISK 1" /media/nas1
```
but I would like to have Ubuntu mount these drives at startup. At present I have to manually use the console to mount the drives. Fortunately, the previous commands are remembered when I press the Arrow Up key.
I tried adding entries to fstab:
```
"//lkgd71990/DISK 1" /media/nas1 smbfs defaults 0 0
"//lkgd71990/DISK 2" /media/nas2 smbfs defaults 0 0
```
but that does not mount them.
I expect there is a script or something that would do it, but where can I find that script or does anyone know how to do that?

---

### Post by deejross on 2008-01-13
I can give you a line of my fstab that I use to mount my Windows shares. First, smbfs is dead, and cifs is the best way to go. For whatever reason, you still have to install smbfs to use cifs. The other important thing is that you have to specify login credentials in the fstab or the login will fail. Even if you have the Guest account enabled in Windows, that won't work. You need to create a user in Windows and give it a password. Linux cannot connect to a share with a username that has a blank password for security reasons. So here's what I did.

[LIST=1]
[*]Create a user in Windows called Linux
[*]Set the Linux user's password to something other than blank
[*]Create the file "/root/.smbcredentials"
[*]In this file, you only need two lines
```
username=linux
password=your_password
```
[*]Change permissions so that no one can get your credentials: chmod 600 /root/.smbcredentials
[*]In the fstab file, enter the following line:
```
//Server/Share/Folder /media/sharename     cifs     credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777     0     0
```
[*]Make sure you create the folder "/media/sharename" and leave it empty
[*]Type ```
sudo mount -a
``` to see if it works without having to reboot your machine
[/LIST]

Just a couple of notes that I figured out with my own trial and error:
[LIST]
[*]The "Folder" in the share path is optional
[*]However, you cannot go deeper than one folder in the share
[*]EDIT: Also, I noticed you have a space in the share name "DISK 1". I remember having problems with spaces at one time, so if this doesn't work, I would test to see if a share without spaces in the name works.
[/LIST]

So, for example, you cannot use "//WINXP/DATA-DRIVE/Media/Music". You would have to omit the "Music" folder from the line or it will not work.

Hope this helps,

Ross

---

### Post by kavoura on 2008-01-13
I should have said that the network drive to be mounted is not on a Windows PC, it is on a Linksys Network Attached Storage device, which runs Linux. As for the space in DISK 1, I know that could be a problem, but blame Linksys for that, because they set it up to work that way. 
I think I set up a user on the Linksys NAS, cannot recall now what the login details are. Anyway, I have never had a problem connecting to it from Linux or Windows from any PC on my network. I mostly use the same username and password for each login, but in Ubuntu I have two accounts with different names and passwords, and can still connect to the Linksys NAS with either without being prompted at any time for a password.
Anyway, I followed your instructions as best I could and set up the .smbcredentials file with current username and pw and changed fstab with the following:
```
//lkgd71990/DISK%201 /media/nas1  cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777     0     0
//lkgd71990/DISK%202 /media/nas2 cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777     0     0
```
I altered the DISK 1 bit to DISK%201 where I believe that the %20 is unix code for a space, which did not work though.
When I entered sudo mount -a it told me that there were bad lines where that was, and it seems as if putting the quote marks around something in fstab means nothing. Although I read that CIFS is what is used in Windows, so should I still use smbfs as the NAS is running Linux?
I tried again the sudo mount -a and this time got the following message:
```
mount.cifs failed: password in credentials file too long
```
I tried it without credentials and using smbfs, and putting in _ for the space as thus:
```
//lkgd71990/DISK_1 /media/nas1 smbfs iocharset=utf8,file_mode=0777,dir_mode=0777     0     0
//lkgd71990/DISK_2 /media/nas2 smbfs iocharset=utf8,file_mode=0777,dir_mode=0777     0     0
```
then did a sudo mount -a and this time got no errors.
So I will reboot and try it with these settings.

Thanks for your help so far, I hope it will all work now.

---

### Post by kavoura on 2008-01-13
I rebooted and it still did not work.
So far the best I can do for now is to remark those lines with # and just mount them manually when I log in.

---

### Post by kavoura on 2008-01-13
As for changing the DRIVE 1 on the NAS to something without spaces, I cannot log into the administration part of the NAS as I have mislaid the login details for it.

---

### Post by kavoura on 2008-01-21
I have solved this problem at last.

The answer came from Mandriva 2008. On another PC I installed that and somehow set up the NAS drives to mount at boot time, so I looked at its fstab file and copied the entries from that to my Ubuntu fstab and adjusted the mount points to what I wanted in Ubuntu, as follows:
```
//lkgd71990/DISK\0401 /media/nas1 smbfs username=% 0 0
//lkgd71990/DISK\0402 /media/nas2 smbfs username=% 0 0
```

In Mandriva 2008 this gives me read only access to the NAS drives, but I can also access the drives there through the network in Konqueror. In Ubuntu, this loads the NAS drives rw and fully accessible.

---

