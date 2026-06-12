---
title: "umask isnt working"
date: 2007-08-07
forum: General Help
---

### Post by lightnb on 2007-08-07
I have two machines, one is running Samba and this one I'm using as a workstation.

I have a remote share mounted to the local file system using fstab. I have write permission and can create files an folders. I can also delete files from within konqueror. When I try to open and then save modifications from within my editor, i get a permissions error. This is because the permissions for new files keep setting themselves to 755, and I'm not the owner, just in the group.

I've tried going to the directory and running "umask 002", but it seems to be ignoring me, since there's no change in behavior.

any ideas? Or am I using umask wrong?

---

### Post by pmg on 2007-08-08
Running **umask 002** in your shell sets it's umask, which will affect the mode bits of any files you then create from that shell or any child processes started from that shell after setting it's umask.  It doesn't affect any files that have already been created.  To change the mode bits on existing files you need to use the **chmod** command.

---

### Post by lightnb on 2007-08-08
I can use chmod to change the files once they've been created, but it's annoying to have to SSH in to modify the file every time you create one.

Isn't there a way to make it so that all new files just have write access for the group?

---

### Post by pmg on 2007-08-09
I don't know much about setting up samba, but I think there is a "create mode" attribute you can set in the smb.conf file that affects this.  (Maybe someone with some experience setting up samba can comment.)

---

