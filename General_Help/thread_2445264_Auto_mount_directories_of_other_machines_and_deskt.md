---
title: "Auto mount directories of other machines and desktop layout stopped after upgrade"
date: 2020-06-11
forum: General Help
---

### Post by Jonners59 on 2020-06-11
OK, so I recently upgraded my OS to 20.04, and all went fine, but since I have noticed two nagging problems, which seem to be intermittent, at least the 2nd one is.

The first, I have in my fstab an auto mount of a directory on another PC on the LAN which is always left on - I treat it like a server.  It has worked for years, but now when I boot up, the directories are not mounted on my PC and I get the following.

  	 	 	 	   Sorry, does not allow me to copy and paste, so have to type from memory, but it says something like this.

 
 
 ```
Failed to mount “Server”

 mount:/media/Server: operation permitted by root only.


``` 
 
 Or when selecting from favourites in a file manager, I get, again typed.
 
 
 ```
“Failed to open “documents/ on server.local”.

 Failed to mount Windows share: Invalid argument.


``` 
 
 I have this in fastab (Note I have xxx out the IP address, but it is the correct one and valid)
 ```
//xxx.xxx.xxx.xxx/Documents	/media/Server	cifs	guest,uid=1000,iocharset=utf8	0	0
```
which has worked for years

 
 
 If I type ```
sudo mount -a
``` then all mounts correctly.  SO what is wrong, please, anyone?

 
 
 Also, one last and not so important, but annoying thing.  When I start my PC and it loads up, all the icons on the desktop rearrange and I need to sort them out.  Tends to be, I think when certain items launch maybe in a different order they end up starting top left and then put everything else out as icons load in the first alternative space available.

 
 
 How do I fix this too, please?

---

### Post by TheFu on 2020-06-11
The default settings for samba and Windows10 have changed in the last 6 months or so.  If the CIFS storage is NOT from Win10, then the answer is different.  So ... what is the CIFS storage provider?

Want to access a Windows Share from Linux? In short, seems that Win10 disables NetBIOS and using a manual CIFS is necessary.
Morbius1's instructions: [https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468](https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468)

For Old CIFS storage devices, more from Morbius1:
[https://ubuntuforums.org/showthread.php?t=2444358&p=13961480#post13961480](https://ubuntuforums.org/showthread.php?t=2444358&p=13961480#post13961480)
New Ubuntu lost access to old samba device.  Ubuntu has more secure settings now. Those old devices are running really, really, old samba full of performance and security issues.  Don't care?  Just want access?

Add this to the [global] section of the /etc/samba/smb.conf file:
```
  client min protocol = NT1
```

Just yesterday I found that VLC on Android only supports SMB1, so my tablet cannot access a Samba share anymore with the better, faster, SMB2 or 3 protocols. Booo.

Of course, I'm guessing about the issues. Could be something else completely.  Normally, there are log files showing connection problems which should be checked.

---

### Post by Jonners59 on 2020-06-11
> **TheFu said:**
> .

Hello, back again, TheFu.  Thank you.

I don't know because when I mount with the cmd ```
sudo mount -a
``` AFTER launch it works.  It seems to be just during boot.  FYI both machines are running Linux, but for historical and also as my kids and wife now use Windows machines the storage is NTFS.  So do not think it is that and TBH it worked before I upgraded.  I.e. within hours.

---

### Post by TheFu on 2020-06-11
These forums are full of people trying to do something similar. Just need to find the 
[LIST]
[*]same client OS
[*]same server OS
[*]same type of storage
[/LIST]
and the solution should be there. Posting that data here would help someone to help you. The *Description:* line from **lsb_release -a** command.

If the mount tool is trying to mount that storage BEFORE networking is up, that could fail. There's a mount option, _netdev, which really shouldn't be needed, but if the fstab mount tool gets confused, it might help.

For Currently supported Linux systems, NFS is easier and faster than CIFS. The storage would appear like it is local and you can setup the mounts to only happen on-demand and to umount after 5 minutes of unuse.  This is good for laptops. The same can be configured for CIFS mounts, BTW.

I haven't used NTFS on Linux with CIFS shares beyond testing, but others have and as long as the NTFS mounts on the other machine have the correct permissions, usually a "force user" samba is used, I think, then it should work. I've NEVER used guest.

Have you checked the log files on the samba server yet?  They are in /var/log/samba/ ... usually by the IP address of the client.

---

### Post by Morbius1 on 2020-06-11
The stock answer to the fstab issue is an automounter which will mount "on access" not at boot. But there is a unique problem with this and Xubuntu users.

I would recommend something different:

[1] Unmount the share if it's mounted:
```
sudo umount /media/Server
```
[2] Edit fstab and change your declaration to this:
> //xxx.xxx.xxx.xxx/Documents    /media/Server    cifs    guest,uid=1000,iocharset=utf8[COLOR=#0000ff]**,noauto,user**[/COLOR]    0    0
[3] Refresh systemd:
```
sudo systemctl daemon-reload
```

You should notice a link on the side panel of Thunar labeled "Server" under Devices. It's actionable. Click on it and it will mount the share. Click on it again or right click it and it allows you to unmount it.

---

### Post by Jonners59 on 2020-06-11
Morbius1
How are you, my dear friend.  Must be 7years?

Thank you, yes, that worked.  And I noted the icons went back to as they should be too.  See if that continues.  I had to change a couple of the desktop URLs to launch via the mounted directory, but all minor stuff.

Thank you.

Take care and keep safe.

---

