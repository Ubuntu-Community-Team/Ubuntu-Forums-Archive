---
title: "Issues with mounting CIFS share permanently on Ubuntu 14.04"
date: 2015-04-29
forum: General Help
---

### Post by Harry_Shaw on 2015-04-29
[FONT=Helvetica Neue]I have a box running Freenas and I want to mount a cifs share on my ubuntu machine running desktop version 14.04[/FONT]
[FONT=Helvetica Neue]I can mount it using the following at command prompt[/FONT]
 [B]
sudo mount -t cifs //192.168.1.10/raid_media1 /media/[/B]
[FONT=Helvetica Neue]
This works just fine.[/FONT]
[FONT=Helvetica Neue]However, I want this to be done permanently (i.e. every time the machine reboots). So I followed the instructions and inserted following line item in /etc/fstab[/FONT]
[B]
//192.168.1.10/raid_media1 /media/ cifs iocharset=utf8,gid=124 0 0[/B]
[FONT=Helvetica Neue]
gid=124 corresponds to the group sambashare, of which I am a member.[/FONT]
[FONT=Helvetica Neue]
When I try to execute this using the **mount -a** command, it asks for a password (there is no password required for this share). When I hit enter, it hangs for a few seconds and spits out following:[/FONT]
[B]mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page[/B]
[FONT=Helvetica Neue]Of course, the mounting is not successful at this point. What am I missing ?[/FONT]

---

### Post by TheFu on 2015-04-29
That is a bad place to mount storage that YOU manage. That is where automaticly mounted stuff get put.
So .... 
[B]
sudo mkdir /media1[/B]
Then add```

//192.168.1.10/raid_media1 /media1 cifs iocharset=utf8,gid=124 0 0
```
to the fstab. Of course, this assumes "Everybody" is allowed to mount it form that IP. If there are only specific userids allolwed to mount it, then you'll want a "credentials file" as an option.  Oh - and I didn't carefully validate your options. Nothing jumped out as wrong to me, but I don't know if they are correct.

I use:
```
rw,iocharset=utf8,file_mode=0666,dir_mode=0777,credentials=/etc/samba/romulus-music.credential
``` but I don't mount through the fstab.

Honestly, if you are running FreeNAS, all storage shared to Unix-like OSes would be nicer as NFS.  It is faster and "feels" like native storage - permissions, ownership, etc.

---

### Post by Harry_Shaw on 2015-04-30
@TheFu

Thanks for your reply. I was going to change the mount directory but thanks for your suggestion. Your idea of creating NFS share is a good one too. I will try that out as well.

You said you don't mount through fstab. How do you mount it then?

Also, is credentials file necessary if your shares don't have any password protection?

---

### Post by TheFu on 2015-04-30
> **Harry_Shaw said:**
> @TheFu

Thanks for your reply. I was going to change the mount directory but thanks for your suggestion. Your idea of creating NFS share is a good one too. I will try that out as well.

The trick for NFS shares is matching uid/gids across all platforms. If they don't match, which ever userid has the same uid (the number) gets ownership.  NFS doesn't mount at the userid level. It mounts at the machine-to-machine trust level.

> **Harry_Shaw said:**
> You said you don't mount through fstab. How do you mount it then?
autofs there are pros/cons to doing it this way.

> **Harry_Shaw said:**
> Also, is credentials file necessary if your shares don't have any password protection?
I don't know. Don't recall having any storage that didn't require credentials, but if anyone can read the storage, just leave off that option.

---

### Post by nerdtron on 2015-04-30
I have tried this on the crontab on reboot.
sudo crontab -e

Then add the following cron entry:
@reboot mount -t cifs //192.168.1.10/raid_media1 /media/

---

### Post by Harry_Shaw on 2015-04-30
^That is a cool idea. I am going to try that right now. Thanks.

---

