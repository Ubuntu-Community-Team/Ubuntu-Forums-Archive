---
title: "systemd xinit service status failed when stopping"
date: 2015-05-13
forum: General Help
---

### Post by yann7 on 2015-05-13
Hi all,
i upgrade my ubuntu htpc/server machine to 15.04. So i'm playing with systemd now it replace upstart.
I've several "services" i've added in the past with upstart to start Kodi media center and others things like a virtual (frame buffer) desktop with kde for example. With upstart i never encounter issues, my services started and stopped well.

So, with ubuntu 15.04 i had to change my upstart scripts to systemd to work. All my services start well at boot, but if i want to stop a service that use "xinit" or something from X it always end up with a "failed" status.
[B]
Example of the kodi service :[/B]```

[Unit]
Description = kodi-standalone using xinit
#After = remote-fs.target systemd-user-sessions.service
After = remote-fs.target multi-user.target graphical.target

[Service]
User = xbmc
Group = xbmc
PAMName = login
Type = simple
ExecStart = /usr/bin/xinit /usr/bin/kodi-standalone -- :0 -nolisten tcp
Restart = on-abort

[Install]
WantedBy=multi-user.target
```

1) This service start at boot => OK
2) if in console i do "sudo systemctl stop kodi" => KO, the service stop but it's in state "failed" instead of "dead" or something else. so if i want to start again this service, i must "reset-failed" (sudo systemctl reset-failed) before doing "sudo systemctl start kodi"

When i stop the service manually, in system logs xinit complain about "unexpected signal 15". I never had this message and problem with upstart.

So what's wrong with my service in systemd and is there any way to exit "cleanly" an xinit process ?

Thanks !

---

### Post by dino99 on 2015-05-13
there is a request made on lp:1451797 , maybe it can help

---

### Post by yann7 on 2015-05-13
Hello, thanks for your reply, but your link dorsn't work. What is lp ?

---

### Post by yann7 on 2015-05-13
Okay, Launchpad [COLOR=#000000]1451797 is not about my problem.[/COLOR]
[COLOR=#000000]My problem is about a service written with systemd that launch an xinit with client application (kodi media-center). I can start it at boot and then the service is alive, but when i stop it with command line "sudo [/COLOR][COLOR=#000000]systemctl stop koi.service", then the service appear as "failed". I think that when i stop a service it should not be in "failed" state but in "stopped" state.

Am I wrong ?[/COLOR]

---

### Post by graysky on 2016-03-28
@yann7 - I too have the same question.  Have you found a useful solution?  Link to my post on kodi forums: [http://forum.kodi.tv/showthread.php?tid=266318](http://forum.kodi.tv/showthread.php?tid=266318)

I also have a github repo with a kodi.service that is more or less what you have if you are interested: [https://github.com/graysky2/kodi-standalone-service/blob/master/init/kodi.service](https://github.com/graysky2/kodi-standalone-service/blob/master/init/kodi.service)

---

### Post by yann7 on 2016-03-28
Hi graysky. No usefull solution, it appears that when you stop a service with systemd, the service always appear as "failed". To start again the service you must use "systemctl restart xxxx.service".

---

### Post by graysky on 2016-03-28
Not true... I still haven't found a solution that doesn't create another problem... please see and contribute if you wish to this thread: [https://bbs.archlinux.org/viewtopic.php?id=210674](https://bbs.archlinux.org/viewtopic.php?id=210674)

---

### Post by yann7 on 2016-03-28
you're right. So since my first post, i finally launch kodi within a desktop (xfce4). So actually, my service launch XFCE and not kodi anymore. But when i stop the XFCE service, i still see a "failed" status. Think i should find a way to cleanly exit my XFCE service with ExecStop...

---

### Post by graysky on 2016-03-28
Not true... I still haven't found a solution that doesn't create another problem... please see and contribute if you wish to this thread: [https://bbs.archlinux.org/viewtopic.php?id=210674](https://bbs.archlinux.org/viewtopic.php?id=210674)

---

