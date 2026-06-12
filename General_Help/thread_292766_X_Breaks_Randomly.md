---
title: "X Breaks Randomly?"
date: 2006-11-04
forum: General Help
---

### Post by Orbit45244 on 2006-11-04
So today I log onto my Ubuntu Dapper installation.  I just look at a few webpages with Firefox, and then I shut down my computer.  So I get back on later, only to see a blue screen with a message that my X is broken.  Why did it break?  How can I get it working?  I am using an NVIDIA graphics card, and it's working fine in Windows.

---

### Post by lawina on 2006-11-04
What was the message in the blue screen? 
Are you sure its a blue screen :)

---

### Post by mega on 2006-11-04
dist-upgrade just removed nvidia-glx on me

that'll break x when I restart

---

### Post by Orbitr8 on 2006-11-04
Yeah, me too.  Especially frustrating for this noob, I gotta tell you.

From another post:
   comment out the amaranth dist. line in /etc/apt/sources.list

sudo apt-get update
sudo apt-get install nvidia-glx

I got errors, so I then followed the prompts asking me to run the -f install, and then ran

sudo apt-get install nvidia-glx 

again, and it worked.  BUT. no more compiz at the moment.
Grrrr.  Just when I was bragging to my acquaintences how nice Linux is coming along, a simple innocuous upgrade wipes out the desktop.

---

### Post by mega on 2006-11-04
you need the beta nvidia driver

download it and install it, that fixes compiz/beryl

---

### Post by Orbitr8 on 2006-11-04
cool, thnx.   Off to nVidia.

There was once a time when losing X meant a complete reinstallation of whatever distro I was trying out.  It's nice to see (with the help of another drive/os) I can actually fix it.  Way way too much time cusomizing and tweaking to start over now.

;)

--------------------------------------------

Well, dependancy hell trying to update to nVid's 9625 beta.  Says I'm missing headers, etc.  LIBC (which is one of the 'upgrades' that slipped in today).

At least X works again.  That was enough of a thrill for this morning.

---

### Post by Orbit45244 on 2006-11-04
> **mega said:**
> dist-upgrade just removed nvidia-glx on me

that'll break x when I restart

I didn't do a dist-upgrade though.  But I'll try reinstalling nvidia-glx.

---

### Post by Orbitr8 on 2006-11-04
Wow.  Just spent the last few hours trying to get things back to a semblance of normalcy after attempting to upgrade to the 1.0.9625 Beta nVids.

From a windows user p.o.v., this was a ball buster for anyone who thinks the transistion from Windows to Linux will be swift and in droves,  that initially started with an 'update' in the system tray this morning.  It uninstalled nvidia-glx, thereby breaking X and compiz.

I cannot begin to explain how I got it all back, I tried about everything I could find on Google, the forums, error messages until it worked.  I still don't have the proper monitor refresh rate available, regardless of how many times I look in xorg.conf.  It's set to mfg, and should yield from 60 to 75 refresh rates, but offers only 50 and 54.  ?

 The final 'fix' I did was to comment out the Load DRI line in xorg.conf and leave the Load GLX line enabled, and X finally started.

 Unless I'm foggy after that blitz, what I'm thinking is that the new nVidia's contain their own nvidia-glx module.  I tried installing the separate nvidia-kernel-source and the nvidia-glx-1.0.9625+2 glx files, but kept getting errors about needing source files still.

 So, for you folks who have been in Linux awhile..... is it ALWAYS like this ?  I mean, it's kind of fun, and all in a morbid sense, to spend hours looking for a fix to something, but I rarely have to deal with this in XP.   At least for something as major as a gui for most non-geeks, you'd think there would be something like Safe-Mode  with a default set of vids ?  If there is, I sure don't know how to access it.

 Now, Compiz even works, it appears, just a low refresh rate.

 Always something with Linux... and I'll be more careful to look at what's about to be 'upgraded' from now on.

---

### Post by mega on 2006-11-04
it's not ubuntu's fault

the problem is your probably getting nvidia-glx beta drivers from another repo, unofficial, and it's not been updated with the latest kernel drivers

if you were on standard ubuntu X would not have broken

---

### Post by Orbitr8 on 2006-11-04
got them from nVidia

And fixed the refresh rate issue with nVidia's Control Panel, once glx got loaded correctly.

---

