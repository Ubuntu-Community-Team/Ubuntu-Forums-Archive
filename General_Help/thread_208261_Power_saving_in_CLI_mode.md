---
title: "Power saving in CLI mode??"
date: 2006-07-03
forum: General Help
---

### Post by AlliumPorrum on 2006-07-03
Hi!

I'm running 6.0.6 on my laptop as a server without any desktops. 

Is it anyhow possible to enable power saving in CLI mode?? I mean, the harddrive is running all the time even if really doesn't need to, so I would like to shut it down after a 10 minutes or something like that. Ideas?

---

### Post by slackern on 2006-07-03
[QUOTE=AlliumPorrum]Hi!

I'm running 6.0.6 on my laptop as a server without any desktops. 

Is it anyhow possible to enable power saving in CLI mode?? I mean, the harddrive is running all the time even if really doesn't need to, so I would like to shut it down after a 10 minutes or something like that. Ideas?[/QUOTE]

You could try using:
sudo hdparm -Y /dev/hda
sudo hdparm -y /dev/hda
(/dev/hda might have to be changed to correspond to your harddrive)
Syntax means
 -y   put IDE drive in standby mode
 -Y   put IDE drive to sleep

You could use this command in a crontab that runs every 10th minute or something.

---

### Post by AlliumPorrum on 2006-07-03
Hmmm... interesting idea... But wouldn't that command try to put my harddrive to sleep even if I'm currently doing something?? Might slowdown the computer at that point, but I don't know if it matters anyway. Have you really tried this "trick" yourself?? ;)

---

### Post by AlliumPorrum on 2006-07-04
Does this silence mean that it really is not possible to use power saving options in the CLI mode...?

---

### Post by AlliumPorrum on 2006-07-04
> You could try using:
sudo hdparm -Y /dev/hda
sudo hdparm -y /dev/hda
(/dev/hda might have to be changed to correspond to your harddrive)
Syntax means
-y put IDE drive in standby mode
-Y put IDE drive to sleep

You could use this command in a crontab that runs every 10th minute or something.

I tried this, but it does not help; -y won't really stop the HD, -Y stops it so well that I have to reboot to make it running again...;)  For some reason if I run with that -Y option, what ever I try to do after that, system just says something like "mkdir: cannot create directory `test': Read-only file system". After reboot everything is ok.

---

### Post by slackern on 2006-07-04
Ahh sorry for the lack of response, Im not so familiar with powersaving myself i know that i used to use this on a old fileserver i had running in a closet for years with a big load of old harddrives and it worked fine there, maybe something is different. Main reason for me was to lower heat and noise, i just had to access the discs in it and they spun up properly by them selfs for me.

---

### Post by AlliumPorrum on 2006-07-04
I just noticed that there is a package called 'laptop-mode-tools', and it seems to be currently enabled on my ubuntu, but could some one tell me where can I change the time-out for the HD sleep?? Or can I...?

---

