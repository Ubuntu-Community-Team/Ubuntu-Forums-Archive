---
title: "Can't Share NTFS and FAT drives"
date: 2015-11-24
forum: General Help
---

### Post by Parrallax on 2015-11-24
Hi guys,

I've been dabbling with Ubuntu for a bit now, but I still consider myself a bit of a noob so please bear with me.
I'm setting up a new box as a file-server/Plex server. I went with Gnome because I personally prefer it and it seems to run smoother for me, although most of the time the box won't have a screen.

It currently has three drives in it, a 500GB that I installed the OS to, a 2TB and an 8TB. The 2TB is formatted to FAT32 and the 8TB to NTFS. Perhaps these weren't the best choice but it'd be difficult to change that now without losing a lot of data. I've used 

udisksctl mount -b *device_name*So that both of these disks are mounted at startup.

I really want them both accessible through standard Windows sharing. I personally don't mind SCP but I want the wife approval factor.

 I tried sharing them using the standard method, click on the drive, go to properties, click share the drive etc.

When I browse to the Linux box from a Windows machine I can see that the two drives are shared but when I click on it I get "Windows cannot access //machinename/drivename"

I tried sharing a folder that's on the Drive that Ubuntu is installed on and it shared no problem. This makes me feel that it's a permission error to do with the formatting of the hard drives? Is there a way around this without reformatting, or am I just better off formatting them to ext4 or something?

Thanks guys!

Bob

---

### Post by sandyd on 2015-11-24
Might be the drive mount UID/GIDs
Can you post the output of
```

ls -l
```
in the directory where the NTFS drive is mounted and in the directory where the FAT drive is mounted?

Side Note:
Not familiar with udisks - more familiar with mounting through fstab

---

### Post by Parrallax on 2015-11-24
Thanks for your help.
They are both mounted to the same directory, /media/bob/
here is the output of ls -l in that directory.

```

bob@Harry:/media/bob$ ls -ltotal 22
drwxrwxrwx 1 bob bob  4096 Nov 25 10:43 BigDrive
drwxr-xr-x 8 bob bob 16384 Jan  1  1970 Disk 1
dr-xr-xr-x 4 bob bob   136 Feb  5  2009 SILAS_MARNER

```

BigDrive is the name of the NTFS drive and Disk 1 is the name of the FAT32 drive.

---

### Post by sandyd on 2015-11-25
Permissions/owner seems to be fine, lets go down to see what samba has configured for your folders:
Please post the output of
```

net usershare info

```

---

### Post by Parrallax on 2015-11-25
I was unable to get any output at all using that command. Each time I entered it, in whatever directory, it produced zero output.

I also tried "net usershare list" and again got nothing.

---

### Post by mastablasta on 2015-11-25
> **Parrallax said:**
>  I went with Gnome because I personally prefer it and it seems to run smoother for me, although most of the time the box won't have a screen.

then why install a desktop. there are plenty server GUI's available that would have helped you install various services in no time. In your case something like OpenMediaVault would go. Bu ton the other hand there are also Zentyal, Ajenti, Webmin etc. etc... search the web a bit.

in your case you would need SAMBA or sFTP (if you plan to go the SCP or Filezilla way). If server is only setup on LAN then SAMBA is good enough otherwise sFTP with keys is a must. On server GUIs all you would usually do is tick a box to enable them and set a folder to be shared.

> 
It currently has three drives in it, a 500GB that I installed the OS to, a 2TB and an 8TB. The 2TB is formatted to FAT32 and the 8TB to NTFS. Perhaps these weren't the best choice but it'd be difficult to change that now without losing a lot of data. I've used 


I will say something doesn't make sense here. You did use the wrong formats. and you limited yourself for example: > The maximum possible size for a file on a FAT32 volume is 4 GB minus 1 byte since you have windows, you can change FAT32 to NTFS without data loss. and I would do that, if you plan to store media on server.

now as for sharing that or NTFS it usually works with no problem. I do not know what kind of setup you did. but NTFS volume need to be mounted first so you would need to take care that it get's mounted on boot. I use Openelec on Rpi and it does all that automatically. I also make it sharable quite easy with a few boxes ticket and folder set.

but on desktop it's another matter and I found it that with samba often I would still need to fiddle with config files anyway. even on desktop. all computers need to be in same group for example and some other things. anyway while it does work it works (at least for me) in a strange way. so instead of samba I would install ssh server and use sFTP to upload files to server. 

for file sharing and filesync and such I would suggest you look at owncloud or seafile. owncloud has clients and it quite easy to setup. clients make it  easy to use for your wife as well.

---

### Post by Parrallax on 2015-11-25
I can reformat the FAT32 to NTFS, that's not a big problem. That still leaves me trying to figure out why I can't access the NTFS drive. 

I wanted to stick with Ubuntu because I already had the hardware lying around and I am familiar with Ubuntu and comfortable with it. I also want the option to plug the box directly into a TV and run Kodi off it, so I'm not sure if a server distribution would meet those needs.

sFTP or SCP may be fine for some but as I mentioned it's important that my wife find it easy to access from her own laptop. Specifically I would like to be able to put all our holiday photos on it and then just map a network drive for her so as long as she's on the LAN she can browse the photos easily.

My setup, as I mentioned before, was to use 
```
[COLOR=#000000]udisksctl mount -b [/COLOR]*device_name*
```

So that the drives are automatically mounted at startup. Then using Nautilus, I left clicked on the drive, clicked on Properties, then Network Share, then clicked on the various tick boxes there to allow guest access, read/write access. etc.

I also just then tried to go directly into /etc/samba/smb.conf and adding these lines to the bottom:

```

[BigDrive]comment = Big Drive
path = /media/bob/BigDrive
read only = no
guest only = yes
guest ok = yes

```

I got the same result. When I browse to the Linux box through the network from my Windows machine, I can see the Big Drive shared directory, but when I click on it I get the "Windows cannot access \\HARRY\BigDrive" error message that does not happen when I try and access the folder in the \home folder.

---

### Post by mastablasta on 2015-11-25
I think maybe the issue is the file system have a look and see if it helps: [http://askubuntu.com/questions/105473/samba-network-sharing-ntfs-drives-and-root-permissions-from-local-drives](http://askubuntu.com/questions/105473/samba-network-sharing-ntfs-drives-and-root-permissions-from-local-drives)

similar issue with a more complicated scheme: [http://ubuntuforums.org/showthread.php?t=2256466](http://ubuntuforums.org/showthread.php?t=2256466)

by the way Kodi has it's own desktop interface and themes (OpenElec is stripped down Kodi basically). Still no need for Ubuntu.

---

### Post by Morbius1 on 2015-11-25
> path = /media/bob/BigDrive
Only "bob" will gain access to "BigDrive" regardless of what permissions are on "BigDrive" itself and regardless of how it's formatted. Run this command and you will see that only "bob" can get past the folder:
```
 getfacl /media/bob
```

You've got multiple ways out of this:

Edit /etc/samba/smb.conf and:

** Add the following line to the [global] section - right under the "workgroup = workgroup" line:
```
force user = bob
```
Then restart smbd:
```
sudo service smbd restart
```
You should probably remove the share definition you have in smb.conf if you also created the share in Nautilus.

*OR* Remove the share you created in Nautilus and change the share definition to include the force user line like this:
> [BigDrive]comment = Big Drive
path = /media/bob/BigDrive
read only = no
guest only = yes
guest ok = yes
[COLOR=#0000cd]**force user = bob**[/COLOR]

Then restart smbd.

*OR* Change the mount point from /media/bob/BigDrive to /media/BigDrive so that /media/bob is not an impediment.

**[COLOR=#0000cd]* Side note:*[/COLOR]**
> [QUOTE]Then using Nautilus, I left clicked on the drive, clicked on Properties,  then Network Share, then clicked on the various tick boxes there to  allow guest access, read/write access. etc.
Please post the output of
```
net usershare info 

```
> I was unable to get any output at all using that command. Each time I  entered it, in whatever directory, it produced zero output.[/QUOTE]
On the surface that doesn't make any sense. Did you share it as root? Does this produce output:
```
net usershare info --long
```

---

### Post by Parrallax on 2015-11-26
> ```
force user = bob
```

That did the trick. Thanks so much for that!

---

