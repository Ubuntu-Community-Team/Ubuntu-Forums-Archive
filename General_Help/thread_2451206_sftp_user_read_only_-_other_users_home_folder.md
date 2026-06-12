---
title: "sftp user read only - other users home folder"
date: 2020-09-29
forum: General Help
---

### Post by ronbaechle on 2020-09-29
I have openssh running for sftp.  Following online guides I have this working with the user chrooted to their home directory.  What I like is to have a second user (user2-download-only) to be chrooted to user1 home directory for read only access.  Typical scenario would be user uploads file and sends read-only credentials to client.  I would normally  "usermod -d /home/user1 user2".

Current procedure:
sudo adduser bob
sudo usermod -G sftpusers bob
sudo chown root /home/bob
sudo chmod go-w /home/bob
sudo mkdir /home/bob/public
sudo chown bob:sftpusers /home/bob/public
sudo chmod ug+rwX /home/bob/public
usermod -s /sbin/nologin bob

sshd_config 
Match Group_ sftpusers -->Edit corrected typo_
   ChrootDirectory %h
   ForceCommand internal-sftp

---

### Post by TheFu on 2020-09-29
I wouldn't do it that way.

Whenever files need to be shared, especially in a chroot, then a 3rd directory is needed.  Then use normal file permissions to control access.
It has been awhile since I setup a chroot, but aren't passwd and group files required to be accessed for those to work? Don't really want to copy those into a user's HOME.  That would be a huge security fail.

BTW, 
```
sudo usermod -G [COLOR="#FF0000"]sftpusers[/COLOR] bob
sudo chown bob:[COLOR="#FF0000"]sftpusers[/COLOR] /home/bob/public
#   and
Match Group [COLOR="#FF0000"]sftponly[/COLOR]
```
Don't appear to be what you intend.

---

