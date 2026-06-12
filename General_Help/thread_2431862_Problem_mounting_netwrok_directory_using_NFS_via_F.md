---
title: "Problem mounting netwrok directory using NFS via FSTAB"
date: 2019-11-23
forum: General Help
---

### Post by twosquared on 2019-11-23
I should probably start by mentioning that I am running Ubuntu 18.04.3 LTS 64 bit.
 
 
 I’ve been trying to mount a network-drive using NFS in FSTAB.
 
 
 My home network has two NAS devices.  One is an old Western Digital My Book Live hard drive on which I have music, which mounts successfully via FSTAB as a SAMBA share.  The newer device is a Synology DS418play, which I recently added to my home network.
 
 
 I can manually mount the NFS directory, which is physically located on the DS418 using ```
 sudo mount 192.168.100.146:/volume1/MyNFSFolder /home/bill/NetworkDrive/MyNFSFolder 
```:

[ATTACH=CONFIG]284464[/ATTACH]

 
 
 If I include ```
 192.168.100.146:/volume1/MyNFSFolder /home/bill/NetworkDrive/MyNFSFolder nfs rw,hard,intr 0 0 
``` in my FSTAB file, upon rebooting it appears as though the NFSFolder has successfully mounted and it is listed with an eject button, but when I click on the folder, there’s no folder/file structure:

[ATTACH=CONFIG]284465[/ATTACH]

 
 
 
 
 If I run ```
 sudo mount 192.168.100.146:/volume1/MyNFSFolder /home/bill/NetworkDrive/MyNFSFolder 
``` again, then my file browser shows two instances of MyNFSFolder, both which display the correct folder/file structure as follows:

[ATTACH=CONFIG]284466[/ATTACH]

 
 
 
 
 I’m also having similar issues with two iSCSI drives, (NetworkDrive1 and NetworkDrive2) but for now I’d like to focus on the NFS mount and hopefully that may solve the iSCSI issues along the way.  iSCSI mounts are a lower priority for me for now and can wait.  
 
 
 Any insights would be most welcome.  Thanks in advance.

---

### Post by HermanAB on 2019-11-23
I usually put network mounts in 'rc.local', with a 'sleep 10' in front of it.

---

### Post by CatKiller on 2019-11-23
In case it helps, this is the kind of line that I have in my fstab for NFS mounts (the IP address of my NAS is in my hosts file as "diskstation")

```
diskstation:/volume1/downloads  /mnt/nfs/downloads      nfs     auto,noatime,nfsvers=4       0       0
```

---

### Post by twosquared on 2019-11-30
Firstly, thanks to both you you who replied.  Having mulled this over a bit, I think I'll give Herman's idea a go.  As I understand it, rc.local runs a script at some point during the boot routine.  So, instead of adding the mounts in Fstab, I'd add commands into the rc.local file which would then run as if I had manually mounted the NFS drive.  That seems like a solution that also ought to fix my iSCSI issues too.  So, now the question is 'how to set-up the rc.local script.  

> **HermanAB said:**
> I usually put network mounts in 'rc.local', with a 'sleep 10' in front of it.

Searching on Google I have found this: [https://askubuntu.com/questions/886620/how-can-i-execute-command-on-startup-rc-local-alternative-on-ubuntu-16-10. ]("https://askubuntu.com/questions/886620/how-can-i-execute-command-on-startup-rc-local-alternative-on-ubuntu-16-10")

Within that post I have found this: [URL="https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd"]https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd
[/URL]
I'm going to work through this and hopefully I should be able to get this to work.  If there are any other resources that you think may be helpful, I'd happily consider them.

Thanks again.

Okay, so I found this post which was even clearer: [URL="https://www.blakepell.com/etcrc-local-in-ubuntu-18-04"]https://www.blakepell.com/etcrc-local-in-ubuntu-18-04

[/URL]During the boot process I noticed that rc.local was called and there was a message that flashed across the screen that said something like 'network unreachable'.

The content of my rc.local file is:

```
#!/bin/sh -e

mount 192.168.100.146:/volume1/MyNFSFolder /home/bill/NetworkDrive/MyNFSFolder &

sleep 10

# Always leave this line here
exit 0

```

Any suggestions?

Okay, ```

&#9679; rc-local.service - /etc/rc.local Compatibility
   Loaded: loaded (/lib/systemd/system/rc-local.service; enabled-runtime; vendor preset: enabled)
  Drop-In: /lib/systemd/system/rc-local.service.d
           &#9492;&#9472;debian.conf
   Active: active (exited) since Sat 2019-11-30 15:12:19 +07; 12min ago
     Docs: man:systemd-rc-local-generator(8)
  Process: 1427 ExecStart=/etc/rc.local start (code=exited, status=0/SUCCESS)

Nov 30 15:12:08 bill-OptiPlex-7020 systemd[1]: Starting /etc/rc.local Compatibility...
Nov 30 15:12:10 bill-OptiPlex-7020 rc.local[1427]: mount.nfs: Network is unreachable
Nov 30 15:12:19 bill-OptiPlex-7020 systemd[1]: Started /etc/rc.local Compatibility.

```

is the output from ```
sudo systemctl status rc-local
```

---

### Post by SeijiSensei on 2019-11-30
Ubuntu does not start the network until the user logs in.* So putting the mount in rc.local will result in the "network unreachable" error you see.  There are ways around this, but it would take some work on your part.

I've been experimenting with systemd automounts. One of my NFS shares has this entry in /etc/fstab:
```
server:/media/raid     /media/raid      nfs    defaults,noauto,x-systemd.automount  0 0
```

That mounts the share when first accessed.

*[SIZE=1]This results from the need to support wifi. Wifi connection parameters are stored on a per-user basis, so the connection is made when the user logs in.  There are ways to get around this, but I suggest trying x-systemd.automount first.[/SIZE]

---

### Post by Morbius1 on 2019-11-30
Just a minor note - and it's based on my use of a systemd automounter and cifs not nfs:

There are differences in how an automount displays in different desktop environments. 

In Gnome, Xubuntu, etc.. ( but not the server or KDE ) two icons will appear on the desktop for an automount mounted under /media  or $HOME.

One is there because an actionable icon is always created when something is defined in fstab under /media or $HOME.

Another one - in this case - is there because it's mounted - not when accessed but automatically at login ( not boot ). I suspect udisks2 is making the automounter think it's active so it mounts as soon as the user logs in.

You might consider moving the mount point someplace else - under /mnt perhaps.

---

### Post by twosquared on 2019-12-01
> **SeijiSensei said:**
> Ubuntu does not start the network until the user logs in.* So putting the mount in rc.local will result in the "network unreachable" error you see.  There are ways around this, but it would take some work on your part.

I've been experimenting with systemd automounts. One of my NFS shares has this entry in /etc/fstab:
```
server:/media/raid     /media/raid      nfs    defaults,noauto,x-systemd.automount  0 0
```

That mounts the share when first accessed.

*[SIZE=1]This results from the need to support wifi. Wifi connection parameters are stored on a per-user basis, so the connection is made when the user logs in.  There are ways to get around this, but I suggest trying x-systemd.automount first.[/SIZE]

Thanks for this suggestion.  I have added the same command string modified for my system of course to my Fstab.  When I do, the nfs folder is created on boot, but when I click on it it is empty, whereas in fact there is a directory structure and files in it.  If mount it manually via Samba, I am able to see the content.  Any thoughts?

[ATTACH=CONFIG]284525[/ATTACH]

Thanks for any suggestions.

---

### Post by Morbius1 on 2019-12-01
> When I do, the nfs folder is created on boot
That's one of the points I was trying to make in my post although in retrospect it may have been somewhat incoherent. Having the mount point under your home directory - because you are using Ubuntu ( gnome ) - forces the mount to occur immediately at login. It may still be happening too early in the network process.

If you now have something like this:
> 192.168.100.146:/volume1/MyNFSFolder /home/bill/NetworkDrive/MyNFSFolder nfs rw,hard,intr,noauto,x-systemd.automount 0 0

I would change the mount point to /mnt/NetworkDrive/MyNFSFolder. Then I would verify that it all works before you reboot:

[1] Unmount the share:
```
sudo umount /home/bill/NetworkDrive/MyNFSFolder
```
[2] Change the mountpoint to /mnt/NetworkDrive/MyNFSFolder in fstab

[3] Re-Initiate the systemd daemons:
```
sudo systemctl daemon-reload
```
[4] Restart the network dependency:
```
sudo systemctl restart remote-fs.target
```

Now go to /mnt/MetworkDrive/MyNFSFolder and see if everything is there.

---

### Post by SeijiSensei on 2019-12-01
It's always best to mount NFS shares to a location owned by root. Then access will be controlled by the ownerships on the NFS server.  I mount the /home share from my NFS server to a root-owned directory on the client. The various directories under /home are owned by their respective users.

---

### Post by Tadaen_Sylvermane on 2019-12-01
is there a reason not to use autofs rather than fstab for this? i had regular issues with fstab mounting for network drives, in particular occasional hanging on shutdowns and so forth. autofs has solved every issue I ever had. 30 second timeout for umount works wonders.

---

### Post by Morbius1 on 2019-12-01
x-systemd.automount was written to replace the old autofs procedure. Perhaps a better way to phrase that is it was written to have an automounter better conform to the systemd architecture.

It does pretty much everything the old one does but simpler to implement since it's all done by adding options to fstab. Nothing else to install and no files to configure.

An example of a cifs automount:
//server/share /mnt/Share cifs username=XXX,password=YYY,uid=1000,_netdev,noauto,x-systemd.automount,x-systemd.idle-timeout=10 0 0

The **noauto,x-systemd.automount** combination recreates the automount and the **x-systemd.idle-timeout=10** recreates the **--timeout=10** option in auto.master.

When it's not activated by access I can run [highlight]mount | grep Share[/highlight] and it will show me that the systemd automount unit has been created:
> systemd-1 on /mnt/Share [COLOR=#0000cd]**type autofs**[/COLOR]

---

### Post by twosquared on 2019-12-05
> **Morbius1 said:**
> That's one of the points I was trying to make in my post although in retrospect it may have been somewhat incoherent. Having the mount point under your home directory - because you are using Ubuntu ( gnome ) - forces the mount to occur immediately at login. It may still be happening too early in the network process.

If you now have something like this:


I would change the mount point to /mnt/NetworkDrive/MyNFSFolder. Then I would verify that it all works before you reboot:

[1] Unmount the share:
```
sudo umount /home/bill/NetworkDrive/MyNFSFolder
```
[2] Change the mountpoint to /mnt/NetworkDrive/MyNFSFolder in fstab

[3] Re-Initiate the systemd daemons:
```
sudo systemctl daemon-reload
```
[4] Restart the network dependency:
```
sudo systemctl restart remote-fs.target
```

Now go to /mnt/MetworkDrive/MyNFSFolder and see if everything is there.

Okay, that's resolved it!  Thank you all kindly for your constructive and helpful input.

When I executed ```
                         sudo umount /home/bill/NetworkDrive/MyNFSFolder
  
```

I obtained an unexpected response:

```
                         Could not unlink the key(s) from your keying. Please use `keyctl unlink` if you wish to remove the key(s). Proceeding with umount.
 umount: /home/bill/NetworkDrive/MyNFSFolder: not mounted.

  
```

So that was really unexpected in view of:

[ATTACH=CONFIG]284566[/ATTACH]

So, I changed fstab by commenting out the old mount instructions and adding:

```
192.168.100.146:/volume1/MyNFSFolder    /mnt/NetworkDrive/MyNFSFolder nfs   rw,hard,intr,noauto,x-systemd.automount 0 0
```

I then created the respective directories and rebooted.  I am delighted to report that the nfs folder mounted as it ought and, after creating a bookmark for it, I am now able to access it, see its content, create directories and save files, which was my objective at the outset of this enterprise.

My sincere gratitude to all that have contributed to this solution.

---

