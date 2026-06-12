---
title: "no video on LiveCD?"
date: 2004-11-24
forum: General Help
---

### Post by kahping on 2004-11-24
i tried the ubuntu live cd but after the loading screen all i get is a blank screen. tried failsafe mode but with same results. 

i'm using geforce fx 5200, monitor is dell e770s. according to the ubuntu wiki, fx5200 is supported so i doubt this is the problem here. only thing i can think of right now is the monitor detection has a problem coz ubuntu detects my monitor as dell 300a? 

i'm a linux noob, just testing out ubuntu live cd before formatting and installing the real thing.  could somebody help?

---

### Post by Allen S on 2004-11-24
Had the same problem with some other distros using a VS LCD monitor. I was using the digital cable from the monitor to the PC. Switched to the analog cable and most of the distros that I had problems with disappeared. Xandros still wouldn't work. Can't remeber if I had that probelm with Ubuntu Live CD or if I even have it. The install cd worked fine either way.

---

### Post by kahping on 2004-11-24
would this mean that the install would detect (at least) a useable res + refresh for my monitor where the live cd has failed?

also, the wiki has a livecd page that mentions various versions of the warty live cd. i downloaded the livecd using the torrent **this week** so i'm asuming it's the latest version? when i started it up, it loaded kernel 2.6.7 but warty release is supposed to use 2.6.8.x IIRC. is the torrent updated or is it still an old copy of the live cd?

---

### Post by BWF89 on 2004-11-25
I have the same prolbem. I can't watch my *cough* girly movies *cough* that I would have no prolbem viewing with Quicktime for Windows...

---

### Post by Magneto on 2004-11-25
[QUOTE=BWF89]I have the same prolbem. I can't watch my *cough* girly movies *cough* that I would have no prolbem viewing with Quicktime for Windows...[/QUOTE]
 I dont know much about the LiveCD but if its like the real distro it won't have the codecs for wmv wma divx dvdcss or quicktime in any version - you need to install codecs to view that content - since the OS is on a CD I dont know if you can make it play nice with codecs located on your hard drive

---

### Post by abcdme on 2004-11-25
I got the same problem too,

Messge from console : CTRL + ALT + F1 ->

** (gome-session: 4596): warning **: Esound failed to start
/dev/dsp: No such device.

What is the meaning for the about message? any one knows?

My system has been testing with knoppix 3.2 to 3.6 while having no problem before. 

Sound Card: Creative Vibra 128.
Video Card: NV MX400.

 :confused:

---

### Post by kahping on 2004-11-26
i more recently found out that during shutdown (CTRL+ALT+BACKSPACE), i can see a "display connection lost" or similar message posted by gnome. maybe this is the problem? 

is there a way to manually specify the monitor model i'm using before full boot up?

---

### Post by snipes420 on 2004-12-01
I am also seeing this on my machine. there is another thread that might be similar.
[http://www.ubuntuforums.org/showthread.php?t=6357](http://www.ubuntuforums.org/showthread.php?t=6357)
 i only tried the default option tho so maybe the nv option will work better.
but on a positive note, the install cd worked perfectly for me.

Edit: The nv option works for me.
Edit: The propriatary nv driver option reboots after the loading screen is finished.

---

### Post by nbliang on 2005-01-04
[QUOTE=kahping]i tried the ubuntu live cd but after the loading screen all i get is a blank screen. tried failsafe mode but with same results.[/QUOTE]

kahping, I also facing the same problem when running the LiveCD but it' is solved when I change the boot options by using "1280x1024, VESA driver" options on the GRUB.

Maybe you can try this out, but I don't know whether it works for you or not:

1.  From the GRUB menu, scroll down to "Submenu -> More boot options"

2.  Try using any one of the options available in there.

-----

"humanity towards others"

Linux & Open Source Supporter
Kuching, Sarawak, Malaysia

---

### Post by jobdrb on 2005-01-17
I found that the scripts, even if you choose a driver (NV), put "Use Frame Buffer" option in xorg.conf, but, this dont work. Why ?? I dont know, may scripts dont setup FrameBuffer correctly??.

Well, in any way, after crash, login as root (no password need),
edit xorg.conf use: pico /etc/X11/xorg.conf,  remove the line in Device section
where you found
[       Option          "UseFBDev"              "true"     ]

save {ctrl-x}

and type startx

---

### Post by mirtux on 2005-01-20
[QUOTE=nbliang]kahping, I also facing the same problem when running the LiveCD but it' is solved when I change the boot options by using "1280x1024, VESA driver" options on the GRUB.

Maybe you can try this out, but I don't know whether it works for you or not:

1.  From the GRUB menu, scroll down to "Submenu -> More boot options"

2.  Try using any one of the options available in there.

-----

"humanity towards others"

Linux & Open Source Supporter
Kuching, Sarawak, Malaysia[/QUOTE]

Hi everybody,
  i've got the very same problem of kahping, but following instructions of nbliang now the live CD is working! Damn, i like this distribution, i think i'll install it. I'm coming from Fedora Core 3, not very happy about that....

Regards,
MC

---

### Post by s0ldier93 on 2005-01-20
Hello All-

I'm new to Linux. I desided to try Ubuntu first after reading the praise several users gave it on Justlinux.com. I downloaded the live CD and I'm having the same problems you guys are speaking of. I'm trying to use it on a P4 1.3Ghx. Machine with a GeForce 2 MX video card if that help. I could see the Ubuntu "stating bar" then nothing. After pausing it the next time and changing the resolution to 800x640 I saw multi colored boot up looking words I don't understand after (maybe before) the starting bar page, then nothing. Any ideas? 

Edit: I'll try the above instructions when I return home 

At any rate, I plan on installing the OS on another machine later. We'll see how that goes.

---

### Post by s0ldier93 on 2005-01-20
Got it. This post is the machine running the live CD. I used the Framebuffer option.

---

