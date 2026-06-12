---
title: "Installing Adobe AIR"
date: 2014-11-06
forum: General Help
---

### Post by Edward_Nigma on 2014-11-06
Hi everyone, I'm trying to install Adobe AIR, I know it's no longer supported, but I need it so I can run Scratch 2.0. First I had to find the libgnome keyring file, so I set that path as an environment variable and the executed the binary```

root@enygma-Inspiron-5721:/home/enygma# LD_LIBRARY_PATH=/usr/lib/i386-linux-gnu ./Downloads/AdobeAIRInstaller.bin

```
 but after that, while the install progress bar is running, I get: Sorry, an error has occured Adobe AIR could not be installed because another application is already being installed. Complete the first installation before proceeding with this one. I know I'm not running another AIR install in the background, so what is it, what do you guys think?

---

### Post by Bucky Ball on 2014-11-06
Have you got Software Centre of Synaptics open?

---

### Post by ringstaart on 2014-11-06
> **Bucky Ball said:**
> Have you got Software Centre of Synaptics open?
This is probably the answer. If you can't figure out what's installing, restart your computer. This will make sure that you exit whatever it is that's giving you trouble.

---

### Post by il lupo on 2014-11-19
I can get AIR to install, thanks to the script and instructions on [this page]("http://www.noobslab.com/2014/09/install-adobe-air-in-ubuntu.html").  My problem is running it.  It won't start from the applications menu.  When i use "Adobe AIR Application Installer" from /usr/bin, i get the following error:

Adobe AIR Application Installer: symbol lookup error: /usr/lib/i386-linux-gnu/libnssutil3.so: undefined symbol: PL_ClearArenaPool

running ls -lh /usr/lib/i386-linux-gnu obtains this result for the file in question:

libnssutil3.so.1d -> libnssutil3.so

Would i be correct in concluding that AIR needs libnssutil3.so to point to something?  If anybody knows what this would be, i'd greatly appreciate the help.  Perhaps the symlink should be reversed?  i'm not sure how to do this.  i want to print some sheet i bought that can be printed digitally.  Sheetmusicplus.com uses flash to display the music.  AIR is needed to download the printing application, so without it....

Thanks for the help!

---

### Post by dragonfly41 on 2014-11-20
There is a prebuilt deb installer (version 2.6) available here ... [http://askubuntu.com/questions/87447/how-can-i-install-adobe-air](http://askubuntu.com/questions/87447/how-can-i-install-adobe-air)

I've just installed it on ubuntu 14.04 (32bit) through GDebi Package Installer.

---

### Post by il lupo on 2014-11-20
Thanks, dragonfly.  i've been to that page.  The installation worked, but i ran into the same problems.  i'm running 64bit, but have enough libraries to use the 32bit.  The 64bit file needs ia32-libs, which is now completely deprecated.  i still have the original 32bit, and perhaps i'll give it another whirl.  i've lost enough work over the past two days trying to solve this, though, so i'll probably wait until the weekend.

---

### Post by dragonfly41 on 2014-11-20
Depending on how important this is for you .. one option *might* be to install VirtualBox on your 64 bit Ubuntu and then install a dedicated but minimum 32bit ubuntu distro as VM which could be used for installing Adobe AIR (32bit).  But it is a long workaround just to crack this.

I just don't know if Adobe AIR (windows version) works on wine.  Check Wine HQ to see if it is on list.


[p.s.]

for 64 bit Ubuntu read here ... [http://www.thepowerbase.com/2013/06/how-to-install-adobe-air-in-ubuntu-13-04/](http://www.thepowerbase.com/2013/06/how-to-install-adobe-air-in-ubuntu-13-04/)

---

### Post by il lupo on 2014-11-22
It's not that important, Dragonfly.  It's just that i spent 5$ to print something digitally, and i can't load the required software to justify the money spent.  So, i applied the nuclear solution and went to the local music store where i teach and bought a digital print from them.  It was actually cheaper, so i may continue doing so, anyway.  i would like the convenience of being able to print from home.  Thus, i may still try to crack this nut from time to time.  Thanks, again, and take care.

---

