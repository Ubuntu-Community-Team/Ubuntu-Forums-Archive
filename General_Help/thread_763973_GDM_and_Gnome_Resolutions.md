---
title: "GDM and Gnome Resolutions"
date: 2008-04-23
forum: General Help
---

### Post by dmakfan on 2008-04-23
Hello,

I've seen a few related posts on this, but was hoping someone could actually explain this to me:

Does GDM and Gnome (i.e. when you're logged in...) use different .conf files for the resolution?  I've got my PC hooked up to an LCD TV via VGA input.  My xorg.conf is using 1360x768 for the resolution, which is what GDM comes up as.  However, once I log in, the resolution changes back to 1024x768 ( I think that's what it is.. it's 4:3 eitherway..).  After logging in, I can use nvidia-settings to change the resolution back to 1360x768, but everytime I restart gnome and log back in, the resolution is back to 1024x768.

So I was just wondering if there's a different conf file for each user.  Some threads indicated that there was one for kde.

Thanks.

---

### Post by yaknowwat on 2008-04-24
They sort of do

Go and find "Virtual" in your Xorg.conf in ordr to change the resolution used in your Login Manager to the correct one.

---

### Post by jsundqui on 2008-04-24
I've got the same problem.  I have posted looking for answers elsewhere (e.g. [http://ubuntuforums.org/showthread.php?t=752710](http://ubuntuforums.org/showthread.php?t=752710)) but no avail.

GDM boots into 1920x1200 but logging in goes to 1024x768 (the resolution I used when I installed and before I hooked up the big monitor).  My xorg.conf is posted over at [http://www.gossamer-threads.com/lists/mythtv/users/329094](http://www.gossamer-threads.com/lists/mythtv/users/329094) and as you can see there is no virtual mode.  Besides, the login manager gives the right resolution.  It's when I go into my account that it switches.

I'm at wits end with this problem!!

---

### Post by Kryten107 on 2008-07-08
I've noticed this too.

There are a ton of nVidia+Hardy threads around here, but most of them are for making the nvidia driver work. Mine works, but like others have said, GDM gets it right but once I log in Gnome reverts back to craptastic. I just can't get the settings to stick...

---

### Post by jgjg on 2008-07-11
Here's how I changed the gdm resolution on my system (running ubuntu 8.04 32-bit desktop).

In a shell...

1) xrandr -q

This showed the device name used for my monitor (VGA-0) and available resolution modes. The one I wanted (1280x1024) was included in the list.

2) I edited /etc/gdm/Init/Default to add the line shown below:

 xrandr --output VGA-0 --mode 1280x1024

I put the line near the top of the file, just below the OLD_IFS=$IFS$ statement.

3) When I restarted X, gdm came up with 1280x1024 resolution, as did my subsequent fluxbox session.

---

