---
title: "mounting problems"
date: 2008-04-11
forum: General Help
---

### Post by rondin on 2008-04-11
When I do

mount -o loop -t iso9660 image.iso /media/iso

It will change the permissions and totally mess up everything for example:

All folders and subfolders in /media/iso will change permissions to root:root

All files will have uid and gid 503. I don't understand how it picks up 503 and from where. There are no users/groups with that id. My user id is 1000. This is really annoying because most programs like G-mount iso use the defaults. Is there any way I can change that?

Also when I have a "noauto" entry in /etc/fstab to mount a cifs windows share. I have specified my uid,gid,umask etc, do I always have to mount with sudo? Because if I try to mount as a user it gives me an error saying that only root can do that. It would be very helpful to do that because I could have a global credentials=~/.mycredentials for all the users and each user will have its own credentials in his home folder and they will be able to use the same entry from /etc/fstab.

---

### Post by fsmithred on 2008-04-11
Mount the iso read-only,  if that won't interfere with anyone's work.

mount -o ro,loop

---

