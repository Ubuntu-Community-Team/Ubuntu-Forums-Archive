---
title: "Desktop doesn't start after updates - hangs after 'running local boot scripts'"
date: 2007-12-24
forum: General Help
---

### Post by NotYourSenorita on 2007-12-24
I'm new to Ubuntu (I installed Gutsy 7.10 about a month ago).  My laptop is a Compaq Presario v2000, and it has an ATI Radeon Xpress 200M video card. Everything was working pretty well until Synaptec told me I needed to install updates today. Since installing the updates, the desktop won't load. After logging in, the mouse pointer shows up on a black screen and then hangs. 

I looked through other threads on the forum, and people with similar problems were told to try "sudo dpkg-reconfigure xserver-xorg" and to use the default settings.
Unfortunately, doing this hasn't solved the problem, and now the system hangs after "running local boot scripts (/etc/rc.local)." 

If there isn't a way to fix this, would reinstalling Ubuntu work? I'm not worried about saving anything since I have nothing to save, really. My laptop is set up for dual booting (Windows XP is on the primary partition) so I'm not sure how I would do a reinstall. 

If anyone has any suggestions, they would be very much appreciated.

---

### Post by rexxxlo on 2007-12-25
i dont knowwhat to do i think from reading its the xorg problems that i have been having but not sure how to fix them 

it hangs at the point where it says 

*running local boot scripts (/etc/re.local)

i removes this file as i read somewhere on google and re booted ....no luck i fiddled around with bios....no luck 

i dont know what to do besides reformat

---

### Post by Phonan on 2008-03-08
Hey all,

Just deleted my Fedora partition so Ubuntu can eat up all the space on my 160 gig HD. Fedora had my GRUB settings on it, so I used the old menu.lst from my Ubuntu. Unfortunately, now, my box hangs on "loading local boot scripts" and I'm stumped. I tried reinstalling GRUB, as everything was fine literally a couple hours before the repartitioning and new GRUB menu. I'll try a few things, and I'm sorry for reviving a 3-month-old thread, but I hope we can get some help for what's now three of us. Anyone?

Phonan

EDIT: Just thought I'd let you know I'm trying it by copying the /etc/rc.local from the livecd over. Hope it works- rebooting now!

---

### Post by Phonan on 2008-03-09
Well I tried the new /etc/rc.local and it didn't work, so the problem must be something else. Help anyone? I can't access my Ubuntu and this is really very annoying.

Thanks,
Phonan

---

### Post by dcstar on 2008-03-10
> **NotYourSenorita said:**
> I'm new to Ubuntu (I installed Gutsy 7.10 about a month ago).  My laptop is a Compaq Presario v2000, and it has an ATI Radeon Xpress 200M video card. Everything was working pretty well until Synaptec told me I needed to install updates today. Since installing the updates, the desktop won't load. After logging in, the mouse pointer shows up on a black screen and then hangs. 

I looked through other threads on the forum, and people with similar problems were told to try **"sudo dpkg-reconfigure xserver-xorg**" and to use the default settings.
Unfortunately, doing this hasn't solved the problem, and now the system hangs after "running local boot scripts (/etc/rc.local)." 

If there isn't a way to fix this, would reinstalling Ubuntu work? I'm not worried about saving anything since I have nothing to save, really. My laptop is set up for dual booting (Windows XP is on the primary partition) so I'm not sure how I would do a reinstall. 

If anyone has any suggestions, they would be very much appreciated.

Do the above and select the VESA driver - then do:
```
sudo /etc/init.d/gdm restart
```

The rc.local is just the last part loaded by the system - it is **not** "hanging" at that point.

---

### Post by Phonan on 2008-03-10
Well here's my problem at least- Ubuntu won't start, which leaves me with little way to try dpkg-reconfigure xserver-xorg. Booting into recovery mode, I get a message that it's not a Python script or an application. Basically, I guess, I'd have to do a full boot into Ubuntu to fix the problem, but obviously I can't do that. I guess basically my question is: how can I get to the point where I can run that command?

---

### Post by Phonan on 2008-03-13
This is pretty strange. I can boot in recovery mode fine, or I can switch to terminals 2-6 after boot, and I can hit ctrl-c, switch terminals, and go back to the tty1 screen. But in none of these screens can I run sudo dpkg-reconfigure xserver-xorg.

For "sudo" or "dpkg-reconfigure" I get a message saying that the command was not found. Trying to run some of my old installed programs like Midnight Commander and links2 on the commandline, I get the same response. This is really strange. Any help?

---

### Post by Rodhill on 2008-03-15
Hi Phonan,
I have what appears to be the same problem and remains unsolved. I have just had a reply from another member who said he noticed I was at the tty1 level (whatever that means) He said to hit CTRL/ALT/F7 and it will drop a level to access the desktop. I haven't tried this yet as I'm at work. Will you PM me if it works?

Cheers

Rod

---

### Post by Phonan on 2008-03-15
Well I'm giving that a shot. Here goes...

---

### Post by pagan5 on 2008-03-16
I had the same problem too
'running local boot scripts'

My way around it was to boot/start from the ubuntu livecd to get a working linux eviroment.
Then i mounted the non booting hdd.
The Live CD already saw the hdd, just right clicked the hdd and mounted.

I just replaced the config.xorg with the backup version

Then went to a terminal, and sudo gedit /media/disk/etc/X11/conf.xorg.original and replaced conf.xorg 

The system boots and works again

Still need/want to install the restricted ATI drivers yet.

---

### Post by Phonan on 2008-03-16
Thanks very much! I'll give that a try soon!

---

### Post by Phonan on 2008-03-16
Sorry, but could you specify exactly which files you replaced and what you replaced them with (paths) so I can do the same thing and see if it works? Sorry, and thanks very much. I hope this works!

---

