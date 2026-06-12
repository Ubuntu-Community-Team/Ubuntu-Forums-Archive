---
title: "my entire computer locks up, with a gray screen"
date: 2008-06-15
forum: General Help
---

### Post by Majin_Buu on 2008-06-15
First of all im new to the whole linux world. I started about a week ago. 

I'm running kubuntu (KDE) with compiz-fusion, using envy (nvidia drivers). To be honest I can't say the system runs exactly "smooth" compared to windows.

My system specs:

amd athlon 64 4400+
2GB RAM
8600GT 256 GDR3 Nvidia

Clearly something isn't when my system can't run the distro "smootly". It's kinda hard to explain, but booting ubuntu takes longer then compared to windows xp, and when im browsing through various windows/tabs the system doesnt respond as fast as im used to.

Now here's the worst issue: at some point when im using a few windows or using opera to google/watching a video etc my entire screen will freeze, leaving me with a gray fading screen. Sometimes I can kill x and reboot into the system, and sometimes the system will unfreese it self after a time, but in most cases I have to reboot my computer.

Can anyone tell me what the .... is going on here?

I know im suppose to post a few logs of my system, could anyone please tell me what exactly you want so I can get some support?

Picture of the "gray"

[http://img.photobucket.com/albums/v32/Skynet/snapshot1.png](http://img.photobucket.com/albums/v32/Skynet/snapshot1.png)

Thank you

---

### Post by ajgreeny on 2008-06-15
Just to test things out try running the system without desktop effects.  Go to System>>Preferences>>Appearance and on the Visual Effects tab set None to see if things improve.  I think your system should run compiz-fusion OK with that graphics card, but occasionally strange things happen and cause problems.

Also worth looking in nautilus for the .xsession-errors file which may have all sorts of errors showing.  To see that file open nautilus, hit Ctrl+H to see hidden files (anything starting with a . is hidden.)

Sorry I started writing this an hour ago and got dragged away.  If it's too late, apologies.

---

### Post by Majin_Buu on 2008-06-15
> **ajgreeny said:**
> Just to test things out try running the system without desktop effects.  Go to System>>Preferences>>Appearance and on the Visual Effects tab set None to see if things improve.  I think your system should run compiz-fusion OK with that graphics card, but occasionally strange things happen and cause problems.

Also worth looking in nautilus for the .xsession-errors file which may have all sorts of errors showing.  To see that file open nautilus, hit Ctrl+H to see hidden files (anything starting with a . is hidden.)

Sorry I started writing this an hour ago and got dragged away.  If it's too late, apologies.

Hey man thanks I'll try disabling compiz and see how long the system remain stable.

No need to apologize sir, thanks for helping me :)

---

