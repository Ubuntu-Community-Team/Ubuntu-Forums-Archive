---
title: "LiveCD Fails To Start EVMS?"
date: 2005-04-29
forum: General Help
---

### Post by BeBoxer on 2005-04-29
I've been trying to get the LiveCD going on my laptop (a Sharp UM30W, Intel i810-based I believe). I need to specify vga=771. It chugs along fine until it starts into actually booting the new system it built. It almost always fails trying to start EVMS. Sometimes I get a shell prompt (so I can "repair" the system), but once I'm in that shell there doesn't appear to be working filesystem mounted. I can't do much at this point, except look at various files in /proc. I've done that looking for an obvious problem but can't find any. The machine has 128MB of RAM, which should be enough, correct? I'm totally stumped as to what to try next, or what logs files to check. Any ideas?

---

### Post by ubuntu noob on 2005-05-03
I am also facing similar problem. If I press Ctrl-C and continue, the desktop opens but my hda as well as other CD drive are not detected. So I am not able to view the contents of my C drive.

However, It detects any USB thumbdrive inserted at boot time.

I am also looking forward for a response on this.

---

### Post by BeBoxer on 2005-05-03
I actually went ahead and took the plunge, installing Ubuntu HH on my laptop. But I would still like to figure out why the LiveCD fails if for no other reason than to help improve Ubuntu. I'm fairly Linux saavy, but I'm not even sure where to start looking in this particular case. I know there are some debugging boot options, but I don't know which are likely to be productive. I'm willing to spend a little time trying to figure this out if anybody can point me in the right direction.

---

### Post by ubuntu noob on 2005-05-04
[QUOTE=BeBoxer]I actually went ahead and took the plunge, installing Ubuntu HH on my laptop. But I would still like to figure out why the LiveCD fails if for no other reason than to help improve Ubuntu. I'm fairly Linux saavy, but I'm not even sure where to start looking in this particular case. I know there are some debugging boot options, but I don't know which are likely to be productive. I'm willing to spend a little time trying to figure this out if anybody can point me in the right direction.[/QUOTE]

You had no issues with HD install ? Do you think mine is similar and I could also take the plunge ?

Regards

---

### Post by BeBoxer on 2005-05-05
[QUOTE=ubuntu noob]You had no issues with HD install ? Do you think mine is similar and I could also take the plunge ?

Regards[/QUOTE]

I don't think the failure I saw is the same as yours. In my case, the ramdisk didn't even appear to be working so I couldn't even try to mount /dev/hda. If you have a fairly standard IDE controller, I would say the chances are good that it will work fine for you. If you run the installer and it can find your drive I would say your chances are excellent. BUT, do you have a plan to restore things if it doesn't work? If you are just installing on a spare partition, go for it. If you are installing over anything important have a backup of it. I used 'dd' and 'nc' (netcat) to image the partition I was going to install on to another computer first, so I could always undo everything.

---

