---
title: "[SOLVED] Cannot Login to New 8.04 Kubuntu Install"
date: 2008-06-22
forum: General Help
---

### Post by Anlace on 2008-06-22
Greetings,

I just did a clean install of Kubuntu 8.04 from the "live" CD.  Everything seemed to go well with the installation except that I am unable to log into KDE.

After rebooting, kdm launches and I get the log in prompt, I type in my user name and password, and push Enter, the screen flickers and I am back at the log in screen.  I cannot get out of this loop, I cannot log in.

I tried to log in by going to the console login and typing sudo kdm, I was asked for my password but still no KDE, it just went back to a command prompt.  I also tried the recovery mode login with the same thing happening.

So, what's up?

Can anyone shed some light on what might be going on?

Any and all help would be much appreciated!

Peace,
Gail

I managed to get past kdm by commenting out all of my partition auto mounts in fstab. I was thinking that maybe there was a problem there, I wanted to see if I could boot only from root and home without the windows and shared partitions.

Now I am looking at a prompt that came up right after kdm that says "Could not start kstartupconfig. Check your installation."

So what does that mean?  At this point should I just reinstall?

Update:  I tried to mount a FAT16 drive at /home/share and it simply didn't work.  After a reinstall and mounting the drive at its own mount point all went very well with no issues.

---

### Post by Anlace on 2008-06-22
I should have posted this in the installation Category.  Ah well, if no reply then I will repost there.

---

### Post by spiderbatdad on 2008-06-22
from the command  prompt try:```
sudo dpkg-reconfigure kdm
```

---

### Post by Anlace on 2008-06-22
I'd love to do that but I can't, now I am getting a Grub error:


GRUB loading, please wait . . .
Error 15

Now what?

Update:  Reinstalling right now.  I tried something with mount points that I think caused the problem.  I will elaborate more if I'm right.  I will also post what happens with this all once I actually get to log into KDE.

---

### Post by Anlace on 2008-06-22
Ok here is what I did that hosed by Kubuntu installation.  Hopefully this information will help others to troubleshoot.

I am using a 250GB SATA HD with the following partitions:
sda1 Windows XP Home mounted at /windows
sda2 Kubuntu mounted at /
sda3 linux swap
sda4 a FAT32 partition to share info between Kubuntu and Windows XP mounted at /share

Where I ran into trouble is that I tried to mount sda4 at /home/gail/ and during my installation I created a user name gail.  I believe that KDE could not start because it could not open my home folder with this mounting scheme.

The second time around involved not automatically mounting sda4 but that only resulted in a kdestartup error.

The second reinstall of Kubuntu I did not format the root partition (doh) and Grub gave me error 15.

Now I've reinstalled once again and all is well except Grub is not offering Windows.  I have seen this before and it is easily repaired with a little bit of hand editing.

Hope this info helps others.

Peace,
Gail

---

### Post by ellgor on 2008-06-23
Hi,

Had a similar problem with KDM, found a post which explained about a bug it has in logging in and be dammed if I can find it again, it made sense but it didn't work for me, however, I did try this that got me back up and running without having to do a re-install.
As you say the login just keeps denying you access and you can't go any further so, enter the recovery mode until you come to the black desktop screen, type kpackage and let it set it self up, type in kdm and when it shows, mark it (you might have to use the options along the top of kpackage to get it to un-install) if you dont have another manager (GDM) now would be a good time to install it, after all thats done reboot and that should be it, hope this is of help.

Regards, Ellgor.

---

