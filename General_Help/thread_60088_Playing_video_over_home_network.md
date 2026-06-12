---
title: "Playing video over home network"
date: 2005-08-26
forum: General Help
---

### Post by ubuntovec on 2005-08-26
Hi to everybody!  :) 

i love ubuntu (my first linux distro), but i have a problem i can not solve. (newbie situation)

situation: home network, two computers, both with shared folders. everything is working fine, except....
problem: i can not play movies, stored on one computer, on another computer. playing music works fine, but movies not... for example: vlc starts but nothing happens. 

what is the problem? 

thanx

---

### Post by Tass on 2006-10-29
Hey

I've got the exact same problem, running 6.10.  Did you ever find a solution to this?

Thanks,

Tass

---

### Post by Jason_25 on 2006-10-29
How is the remote folder mounted?  It must be mounted as a normal folder for mplayer to see it.  I don't use VLC.

---

### Post by coastdweller on 2006-10-29
Jason: I had it working on Kubuntu Dapper, but I don't remember how. I've just decided to get rid of all of my windows boxes and do everything with NFS to solve the "I cant stream over the network stuff".

---

### Post by Tass on 2006-10-30
> **Jason_25 said:**
> How is the remote folder mounted?  It must be mounted as a normal folder for mplayer to see it.  I don't use VLC.

Well, I just used the Connect To Server option, chose a window share, types in the machine name, and there was a shortcut on my desktop.  I then tried dragging files into the VLC playlist.

VLC then decided to hang.

---

### Post by meng on 2006-10-30
Of all the media players I tried: Totem, Xine, MPlayer and VLC, only VLC would play movies through the standard network browse (Connect to server ...), the others would not playback these files.

If, however, you do a:
sudo mount -t smbfs -o username=[user],password=[pass] //name/of/share /mount/point

then all players should be able to play back the files. Of course, you need to have smbfs installed.

---

### Post by Tass on 2006-11-02
Hey

Thanks - that seems to work.  I've got the drive mounted (sudo mount //machinename/windowsshare /media/windowsshare).  I tried to put something similar into my fstab file (//machinename/windowsshare /media/windowsshare smbfs), and the shares mount when running 'sudo mount -a' from the terminal, but don't automatically remount when I reboot.  

when using 'sudo mount -a', I get asked for my root password for each share mounted - not sure if this has something to do with it?

Thanks,

Tass

---

### Post by Breeegz on 2006-11-22
> **Tass said:**
> Hey

Thanks - that seems to work.  I've got the drive mounted (sudo mount //machinename/windowsshare /media/windowsshare).  I tried to put something similar into my fstab file (//machinename/windowsshare /media/windowsshare smbfs), and the shares mount when running 'sudo mount -a' from the terminal, but don't automatically remount when I reboot.  

when using 'sudo mount -a', I get asked for my root password for each share mounted - not sure if this has something to do with it?

Thanks,

Tass

I = total newb
with that in mind, I was reading the manual on "mount" ("man mount" on command line)  I stumbled across the option -F to fork the mounts so they do it at the same time.  Maybe you would only have to enter password once.

I would try it but I'm a little gunshy after crashing my two systems a combined total of 8 times since I started in Jun (all because I "play" with settings I shouldn't play with)...

---

