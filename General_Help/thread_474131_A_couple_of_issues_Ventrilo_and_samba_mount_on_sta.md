---
title: "A couple of issues: Ventrilo and samba mount on startup"
date: 2007-06-14
forum: General Help
---

### Post by crispy_chunks on 2007-06-14
So, ive been trying to get my ventrilo server to start up automatically when i log in. I have tried to do this by adding ventrilo to System -> Preferences -> Sessions with the command /home/media/.ventrilo/ventrilo_srv

This does not seem to work as the server is not running when i log in, however i can read the /home/media/.ventrilo_srv.log that my ventrilo have tried to start when i logged in but gave Unable to open configuration file 'ventrilo_srv.ini' and then exits. I can start the server manually by running the command in terminal or by simply doubleclicking the ventrilo_srv file.

Why cant it read the ventrilo_srv.ini file when i try to start it from sessions?

Is there way to make it work? Or is there a workaround you can help me with?

ive seen [_this_]("http://ubuntuforums.org/showthread.php?t=156514") thread, but it wasnt really helpfull :D

---

My second problem is with fstab and samba. I'm trying to get fstab to mount a share on a windows computer but for some reason it doesnt get mounted on startup. I can do mount -a manually and get the shares mounted but then i have to do it every time i log on and also i have to type in the password. I have been told that it may be because samba havent been initialized before the fstab mounts are run. A problem around this would be to run mount -a a couple of seconds after i log on, but how do i make this happen?

Is there way to make it work? Or is there a workaround you can help me with?

---

### Post by crispy_chunks on 2007-06-14
Well i got the smb shares to work now actually, i used cifs as filesystem instead of smbfs...

So now i only have a problem with ventrilo :D

---

### Post by crispy_chunks on 2007-06-15
Bumpage!

---

