---
title: "mount windows share after delay"
date: 2012-11-22
forum: General Help
---

### Post by bilboubu on 2012-11-22
Hello
 
Is it possible to mount a windows network share after a resume from suspend and after a delay?
 
My client wakes up the server with a wakeon lan, I then want to wait say 10 seconds before the mount.
 
I have the appropriate setting in my fstab noauto,users and am trying to do it from a net device up conf file which calls the script 
 
wakonlan ed:33:dd:e3:33:4r
sleep 10
mount -t cifs -o username=name,password=password,uid=1000 //share /mnt
sleep 10

---

### Post by bilboubu on 2012-11-22
I think my problem is the windows password.
 
If I do "mount //myshare" 
 
it prompts me for my windows password and mounts fine, the problem is I want to run drom a script and when I try
 
"mount //myshare" username=blah,password=blah"
 
it says mount: only root can do that.  The username and password is in the fstab already.

---

