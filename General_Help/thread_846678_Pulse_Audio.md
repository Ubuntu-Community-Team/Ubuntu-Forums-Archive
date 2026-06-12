---
title: "Pulse Audio"
date: 2008-07-01
forum: General Help
---

### Post by carl_pr on 2008-07-01
I had this issue that only 1 program had sound at a time. I follow this Instructions 

[https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")

and


[http://ubuntuforums.org/showthread.php?t=776739]("http://ubuntuforums.org/showthread.php?t=776739")


now i selected PulseAudio in sound settings and all works fine (so far)

i followed mostly the procedure in the first link. My question is in the second link it say that i need to edit the  /etc/libao.conf to

```
default_driver=pulse
```

mine currently say 

```
default_driver=alsa
```

is it ok to leave it like that or should i change it to pulse? and If i have to edit it how?

---

### Post by CameO73 on 2008-07-01
I don't know if it's really necessary (I didn't have it set to pulse and everything works OK). But if you want to edit that file, you'll need (temporary) super user rights.

Try the following steps:

[LIST]
[*]Type [Alt]-[F2] (the Alt-key + F2 simultaneously)
[*]Type **gksu gedit /etc/libao.conf**
[*]This will ask for your password and start gedit (text editor) with elevated rights
[*]Make your modification and save the file
[*]Close gedit
[/LIST]
This will work for any graphical program (e.g. **gksu nautilus** will open the file manager with super user rights). Be careful, since you can do (possibly) a lot of damage!

---

### Post by carl_pr on 2008-07-01
> **CameO73 said:**
> I don't know if it's really necessary (I didn't have it set to pulse and everything works OK). But if you want to edit that file, you'll need (temporary) super user rights.

Try the following steps:

[LIST]
[*]Type [Alt]-[F2] (the Alt-key + F2 simultaneously)
[*]Type **gksu gedit /etc/libao.conf**
[*]This will ask for your password and start gedit (text editor) with elevated rights
[*]Make your modification and save the file
[*]Close gedit
[/LIST]
This will work for any graphical program (e.g. **gksu nautilus** will open the file manager with super user rights). Be careful, since you can do (possibly) a lot of damage!

yea mine works great so far no need to edit that, i thought maybe if i leave it like alsa might cause problems or something, so i asked in case. Thanks

---

