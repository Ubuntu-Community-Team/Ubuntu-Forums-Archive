---
title: "Messed up xorg.conf TV-out can't start gdm"
date: 2007-01-27
forum: General Help
---

### Post by tenjin1 on 2007-01-27
Hi Everyone!

I have a problem trying to get back into my Ubuntu Desktop. First let me start of by listing my hardware an such. I have a ATI 9250 Card and my xorg.conf file has always been configured with TV-Out, everything has always worked great. The outputs I am using on my ATI card are  DVI and S-Video out. 
I had an update for the flgrx driver (which is what my card uses) after the update, it must have wiped my xorg.conf file...for some strange reason my DVI monitor was no longer working but my TV-out was. Well I had a backup of my xorg.conf...so I just used that. After a restart of my computer...no difference. I only had TV-out. I went to Resolution Settings in 'System' tab and none of my resolutions or monitor refresh rates were there. It was almost like it was just the resolutions and refresh rates for my TV. Which was 1024x768 65Hz as the highest and on my monitor I use alot higer than that, I think 1900x1024 @ 75hz. Anyways, obviously I dont think that backup xorg.conf file was current unfortunately. So I used my TV as my monitor so I could open a terminal and run "sudo dpkg-reconfigure xserver-xorg" and tried to get my monitor back. I didn't use any autodetect options because I didn't want it to think my TV was my primary monitor, which is what it seems like is happening. Anyways, it didn't work, so after a couple more "sudo dpkg-reconfigure xserver-xorg" ... now it doesn't work on my monitor or tv!!! No errors, no login screen, no nothing! ](*,) 
I booted into Live CD as a rescue, but I don't know where to start. What do I do to get this going again??? I was just gonna do a clean install...but I haven't backed up any of my important data yet. I wish I could boot into a terminal so I can try to figure it out...I'm lost ...can someone please help or point me to a thread??:confused:

---

### Post by tenjin1 on 2007-01-27
Can someone just tell me the steps on how to use the live cd as a rescue cd to access a terminal so I can reconfigure xserver??

---

### Post by tenjin1 on 2007-01-27
Ok..I think I'm getting somewhere..for some reason it is trying to load my internal Intel video card...it has the wrong BusID basically...

Trying to find the command to list my ATI card's BusID??????

---

### Post by tenjin1 on 2007-01-27
ok...lspci -X

im starting to think my card died...when configuring xserver..when I choose autodetection it keeps bringing up my internal Intel card and after I write config files and start x i get the error : 
> (WW)  fglrx(0): No matching device section for instance (BusID PCI:1:5:1) found
FAILED
FAILED

My BusID for my ATI card is 1:5:1:(

---

### Post by igknighted on 2007-01-27
How did you update the driver?  After you are done you need to issue the command 'aticonfig --initial' to update your system.  Also, since you are locked out of the GUI for now, boot into recovery mode from the grub menu to get to a command line only system to fix it.  I would try the aticonfig one first, and if that doesnt work use 'dpkg-reconfigure xserver-xorg' (if you didnt log in recovery mode you need sudo for those commands, but in recovery mode you are root so you dont need it).

---

### Post by tenjin1 on 2007-01-27
Hi..thanks for your reply.

This all started when I updted the driver from the update manager. I remember seeing 'fglrx-xorg' in the list of updates.
Anyways I have finally got to a command prompt..luckily. I reinstalled fglrx using []("http://ubuntuforums.org/showthread.php?t=75378&highlight=how+to+ati+fglrx+dapper")
but no luck. When I run sudo dpkg-reconfigure xserver-xorg and choose fglrx or ati it gives me the error I mentioned above. The only driver that gets me to GUI my desktop is 'vesa'. 

How would I get back to my working fglrx driver? or do I need another one? Of all the threads I ve seen for my card (3d acceleration and openGL) it seems I need fglrx and I've always used this one with no problems until now! :confused:

---

### Post by tenjin1 on 2007-01-27
> **igknighted said:**
> After you are done you need to issue the command 'aticonfig --initial' to update your system.

Isnt that for the 'ati' driver?... I want to use fglrx. Anyways I ran aticonfig --initial and it came back:
```
Found fglrx primary device section
Nothing to do, terminating.
```

...And I have been running dpkg-reconfigure xserver-xorg this whole time!

Thank you for your suggestions. Do you know anything else or does anyone know what else I can do...I'm going to check out some more on ATI, fglrx and the such.

---

