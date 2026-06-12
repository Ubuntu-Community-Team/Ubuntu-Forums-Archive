---
title: "Non-root file access to entire system help"
date: 2007-03-05
forum: General Help
---

### Post by pentium on 2007-03-05
I have already complained at least once or twice to this forums about wanting to change ownerships of my files so I can move stuff around but now I am really getting annoyed.
The last two times I am given instructions for giving myself rights for a limited time and for a specific folder. If i'm going to stay long term with ubuntu I need to make some changes.
Somebody, please tell me how I can grant myself complete system control FROM A NON ROOT ACCOUNT AND WITH PRIVELAGES LASTING FOEVER.

Not timed, not just a few folders...

[SIZE="4"]EVERY FOLDER, EVERY FILE, EVERY DRIVE...[/SIZE]

And most importantly...

[SIZE="7"]FOREVER![/SIZE]

Sorry for the huge font but I want to get the picture through that if I don't get my permissions, I'm dumping linux and am returning to windows with no looking back.

---

### Post by ewankho on 2007-03-05
Try : ```
chmod -R o+rwx /
```

---

### Post by pentium on 2007-03-05
That did it.

Thanks.

---

### Post by zvacet on 2007-03-06
I find this question very interesting but I think I did not understend all of it.My question is;from security point of view what difference is between root and non root user in this case?

---

### Post by mcduck on 2007-03-06
Remember that many system files must have certain permissions for your system to work, and changing them may (and will) break your system, possibly into unbootable state.. If you need to be able to access other directories than your home it's better to just open file manager as root by running 'gksudo nautilus' :)

---

### Post by vnt87 on 2007-03-06
> **mcduck said:**
> Remember that many system files must have certain permissions for your system to work, and changing them may (and will) break your system, possibly into unbootable state.. If you need to be able to access other directories than your home it's better to just open file manager as root by running 'gksudo nautilus' :)

You're right I just attempted the "chmod -R o+rwx /" above and all sorts of weirdness are going on in my computer. How do I revert the changes made by that command?

---

### Post by vnt87 on 2007-03-06
Damn. Looks like it really broke my system. Lot of things had stopped working. I can't even reset the permission even in recovery mode now. What should I do?

---

### Post by mcduck on 2007-03-06
> **vnt87 said:**
> Damn. Looks like it really broke my system. Lot of things had start working. I can't even reset the permission even in recovery mode now. What should I do?
Honestly, easiest way is to recover your files with live-CD and then do a new install. Finding all files and permissions they need is pretty big task to do, and new install will get your system working way quicker..

---

### Post by pentium on 2007-03-06
This is a bad command?
I have not yet shgut the system down so should I revert?

---

### Post by mcduck on 2007-03-06
Yes, if you figure out how to do that. You would have to find out which files need specific permissions, and then what those permissions are for each file..

This far I haven't heard of anybody actually being able to do that..

edit: If you manage to fix that without doing a reinstall, please post list of all files with special permissions/owners and the correct permissions. That would really help other people doing the same mistake.. :)

---

### Post by srt4play on 2007-03-06
I think it would have been better to show him how to "sudo -i" or "gksudo nautilus" as someone earlier mentioned,  instead of the permissions tidal wave :lolflag: 

In any case, OP should realize it's not going to hurt anybody's feelings (except for maybe his own) if he goes back to windows after throwing his little tantrum.

---

### Post by zvacet on 2007-03-06
Thanks mcduck to confirm what i was thinking.It´s to good to be truth.

---

### Post by pentium on 2007-03-06
> In any case, OP should realize it's not going to hurt anybody's feelings (except for maybe his own) if he goes back to windows after throwing his little tantrum.
Reply With Quote
Yeah. Now I am with a crippled system. ](*,)

---

### Post by tagra123 on 2007-03-06
Once back up and running.
GOOD IDEA IS learning to work with the permissions -- they are there for a reason. 

If you have to have write access to everything all the time then login as root.

If you are just having trouble with copying files between mounted permissions then create the mountpoints this way.

sudo mkdir /mnt/drive1
sudo chmod 777 /mnt/drive1
sudo mount /dev/hda1 /mnt/drive1

If /mnt or /media will work as mount points.





Now if you want to change the permissions of an entire mounted partition then this command will work.

sudo chmod 777 -f -R /mnt/drive1

to change ownership

sudo chown username.username /mnt/drive1

or everything 

sudo chown username.username /mnt/drive1 -f -R


the actual syntax for chown 

chown user.group /path/to/change


you can also start nautilus with full read/write this way

sudo nautilus

better way 

gksudo nautilus

---

### Post by pentium on 2007-03-06
Thanks for those tips.
I restarted the system and it did completely reboot with quite a few permission problems:

> Mar  6 11:05:41 localhost gconfd (pentium-4171): starting (version 2.14.0), pid 4171 user 'pentium'
Mar  6 11:05:41 localhost gconfd (pentium-4171): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:41 localhost gconfd (pentium-4171): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:41 localhost gconfd (pentium-4171): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:42 localhost gconfd (pentium-4173): starting (version 2.14.0), pid 4173 user 'pentium'
Mar  6 11:05:42 localhost gconfd (pentium-4173): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:42 localhost gconfd (pentium-4173): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:42 localhost gconfd (pentium-4175): starting (version 2.14.0), pid 4175 user 'pentium'
Mar  6 11:05:42 localhost gconfd (pentium-4175): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:42 localhost gconfd (pentium-4175): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:42 localhost gconfd (pentium-4175): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:42 localhost gconfd (pentium-4177): starting (version 2.14.0), pid 4177 user 'pentium'
Mar  6 11:05:42 localhost gconfd (pentium-4173): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:42 localhost gconfd (pentium-4177): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:42 localhost gconfd (pentium-4177): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:42 localhost gconfd (pentium-4177): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:42 localhost gconfd (pentium-4179): starting (version 2.14.0), pid 4179 user 'pentium'
Mar  6 11:05:42 localhost gconfd (pentium-4179): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:42 localhost gconfd (pentium-4179): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:42 localhost gconfd (pentium-4179): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:42 localhost gconfd (pentium-4183): starting (version 2.14.0), pid 4183 user 'pentium'
Mar  6 11:05:42 localhost gconfd (pentium-4183): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:42 localhost gconfd (pentium-4183): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:42 localhost gconfd (pentium-4185): starting (version 2.14.0), pid 4185 user 'pentium'
Mar  6 11:05:42 localhost gconfd (pentium-4185): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:42 localhost gconfd (pentium-4185): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:42 localhost gconfd (pentium-4185): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:42 localhost gconfd (pentium-4183): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:42 localhost gconfd (pentium-4187): starting (version 2.14.0), pid 4187 user 'pentium'
Mar  6 11:05:42 localhost gconfd (pentium-4187): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:42 localhost gconfd (pentium-4187): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:42 localhost gconfd (pentium-4187): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:42 localhost gconfd (pentium-4189): starting (version 2.14.0), pid 4189 user 'pentium'
Mar  6 11:05:42 localhost gconfd (pentium-4189): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:42 localhost gconfd (pentium-4189): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:42 localhost gconfd (pentium-4189): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:42 localhost gconfd (pentium-4191): starting (version 2.14.0), pid 4191 user 'pentium'
Mar  6 11:05:42 localhost gconfd (pentium-4191): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:42 localhost gconfd (pentium-4191): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:42 localhost gconfd (pentium-4191): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:44 localhost gconfd (pentium-4197): starting (version 2.14.0), pid 4197 user 'pentium'
Mar  6 11:05:44 localhost gconfd (pentium-4197): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:44 localhost gconfd (pentium-4197): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:44 localhost gconfd (pentium-4197): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:44 localhost gconfd (pentium-4199): starting (version 2.14.0), pid 4199 user 'pentium'
Mar  6 11:05:44 localhost gconfd (pentium-4199): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:44 localhost gconfd (pentium-4199): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:44 localhost gconfd (pentium-4199): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:44 localhost gconfd (pentium-4201): starting (version 2.14.0), pid 4201 user 'pentium'
Mar  6 11:05:44 localhost gconfd (pentium-4201): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:44 localhost gconfd (pentium-4201): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:44 localhost gconfd (pentium-4201): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:44 localhost gconfd (pentium-4203): starting (version 2.14.0), pid 4203 user 'pentium'
Mar  6 11:05:44 localhost gconfd (pentium-4203): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:44 localhost gconfd (pentium-4203): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:44 localhost gconfd (pentium-4203): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it
Mar  6 11:05:44 localhost gconfd (pentium-4207): starting (version 2.14.0), pid 4207 user 'pentium'
Mar  6 11:05:44 localhost gconfd (pentium-4207): Wrong permissions for /tmp/orbit-pentium 
Mar  6 11:05:44 localhost gconfd (pentium-4207): Bad permissions 707 on directory /tmp/gconfd-pentium
Mar  6 11:05:44 localhost gconfd (pentium-4207): Failed to get lock for daemon; exiting: Directory /tmp/gconfd-pentium has a problem. gconfd cannot use it

Also, root terminal seems to be dead,

---

### Post by tagra123 on 2007-03-06
HOW TO PARTIALLY RECOVER FROM THIS 

I'd put in the live cd and

USING GPARTED 
--Shrink the existing partition.
--Make a new partition for HOME

mount both partitions and copy everything from the original  home to the new partition

```
sudo mkdir /mnt/myubuntu
sudo mkdir /mnt/mynewhome
sudo chmod 777 /mnt/myubuntu
sudo chmod 777 /mnt/mynewhome
sudo mount /dev/hdaX /mnt/myubuntu
sudo mount /dev/hdaX /mnt/mynewhome

sudo cp /mnt/myubuntu/home /mnt/mynewhome
```

maybe also tar the contents of the /mnt/myubuntu/etc directory just in case there's a setting in there you want to check against your new setup.

```
sudo tar  -cvpzf /mnt/mynewhome/etc-backup-todaysdate.tgz /mnt/myubuntu/etc

```
then reinstall ubuntu selecting the root partition and the existing home partition manually during the install.  Several places on google tell how to do this.

---

### Post by pentium on 2007-03-06
My hard drive is too small. What about moving the files?

---

### Post by tagra123 on 2007-03-06
if you have network

mount them on a network using samba or nfs (recommend nfs if you have another ubuntu machine)

if you have a usb drive you can mount it and tar the file to it to save space

```
sudo mkdir /mnt/myubuntu
sudo mkdir /mnt/myusbdrive
sudo chmod 777 /mnt/myubuntu
sudo chmod 777 /mnt/myusbdrive
sudo mount /dev/hdaX /mnt/myubuntu
sudo mount /dev/sdaX /mnt/myusbdrive
```

or something similar to the above.


Backup the etc folder.
```
sudo tar  -cvpzf /mnt/myusbdrive/etc-backup-todaysdate.tgz /mnt/myubuntu/etc

```
Backup the home folder

```
sudo tar  -cvpzf /mnt/myusbdrive/home-backup-todaysdate.tgz /mnt/myubuntu/home
```

If the usb is automounted in /media

you can use it or unmount it like this

```
sudo umount /media/usbX
```

(where x is the number you see when browsing the /media folder)

now I wouldn't restore the /etc folder but just use it to change settings if you cannot remember how something was setup.

Archive Manage can be used to tar and untar the files if you'd rather use a gui

---

### Post by pentium on 2007-03-07
Not necessary.
I just did a fresh install and restored a backup of my cookies, favourites and I am now downloading the few packages I used.
One thing of concern is that my new 20 gig hard drive is appearing twice in the computer window even though there is no second partition.
Is it safe to delete one and spare the one that's labeled "filesystem"?
The name of the other one is "John C" from when the drive ran xp. Funny, deleting the fat partition woulf of gotten rid of it.

---

