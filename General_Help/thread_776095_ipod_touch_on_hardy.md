---
title: "ipod touch on hardy"
date: 2008-04-30
forum: General Help
---

### Post by evanct on 2008-04-30
i figured it'd be best to start a new thread on this...

i've been following this guide
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

when i type ipod-touch-mount, it asks for the ipod root password, then tells me:
```
root@[my ip]:/var/mobile/Media: No such file or directory

```

from googling i've found that i have to login to my ipod via SSH to fix this. i do that, and i get this:

```
evan@evans-computer:~$ ssh root@[ipod ip]
root@[ipod ip]'s password: 
-sh-3.2# cd 
Connection to [ipod ip] closed.
```

SSH closes immediately, i don't have a chance to do anything. SSH is enabled on my ipod. this is firmware 1.1.2.

---

### Post by evanct on 2008-04-30
bump?

---

### Post by alejaaandro on 2008-05-01
hmmm... i' m still on Gutsy and just got my ipod touch a couple of days ago and been trying to get it to work with linux... not an expert though..
i followed the same guide but as soon as i upload some music to my ipod and restart it, it gets screwed up.. it says there is no music and when i go to windows (i have dual boot just for this kind of hardware incompatibility) it won't recognize it and i have to restore it.. 
anyway, i stopped trying and i upload music through windows..

still, some files that i want to upload to a different folder (ie. pdf ) i do it trough gFTP... you might be able to create the missing directory through that.. 
type as host your ipods' ip, port 22, usr root and psswd alpine and next to the psswd choose ssh2

an alternative is through nautilus: open a file browser an go File-> Connect to Server and fill in the gaps.. (folder is for the home folder you will be logged into).. it will appear in your desktop..

not sure if i did, but i surelly hope i helped you...
let me know..

---

### Post by evanct on 2008-05-01
> **alejaaandro said:**
> hmmm... i' m still on Gutsy and just got my ipod touch a couple of days ago and been trying to get it to work with linux... not an expert though..
i followed the same guide but as soon as i upload some music to my ipod and restart it, it gets screwed up.. it says there is no music and when i go to windows (i have dual boot just for this kind of hardware incompatibility) it won't recognize it and i have to restore it.. 
anyway, i stopped trying and i upload music through windows..

still, some files that i want to upload to a different folder (ie. pdf ) i do it trough gFTP... you might be able to create the missing directory through that.. 
type as host your ipods' ip, port 22, usr root and psswd alpine and next to the psswd choose ssh2

an alternative is through nautilus: open a file browser an go File-> Connect to Server and fill in the gaps.. (folder is for the home folder you will be logged into).. it will appear in your desktop..

not sure if i did, but i surelly hope i helped you...
let me know..

the gFTP thing actually worked! thanks. 

i'm browsing the ipod's Library and there are still Ringtone and Voicemail, etc. directories from when they dumped everything from the iphone...for shame Apple

---

### Post by evanct on 2008-05-01
i created the Media directory. now when i run ipod-touch-mount i get

```
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
```

sigh...anyone know what to do?

---

### Post by alejaaandro on 2008-05-02
yeah, i got that to sometimes... just delete the file that was created (it should be /media/ipod unless you chose something else)... 
it didn't cause any damage to me, (ie i was afraid it could erase everything from my ipod) but just to be on the safe side, first run ipod-touch-umount and maybe if you wanna be extra carefull you might wanna turn the wireless on your ipod off and unplug it from your pc..

if your user belongs to the fuse group (that should be the case or else you ran ipod-touch-mount as root and you shouldn't have) you shouldn't need root access to delete the file..

as soon as you finish the tutorial your ipod will be mounted as an external device and should show on your desktop... beware though: when you open it through nautilus (doubleclick on the desktop icon) you will not be in / folder of your ipod, so if you wanna put files in other folders (as i told you for example pdf should go in /var/root/Media/PDF) you must still use ssh (either from a terminal, nautilus or gftp)

---

