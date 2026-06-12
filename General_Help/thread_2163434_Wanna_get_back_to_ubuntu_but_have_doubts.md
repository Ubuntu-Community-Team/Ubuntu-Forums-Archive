---
title: "Wanna get back to ubuntu but have doubts"
date: 2013-07-18
forum: General Help
---

### Post by kokoshmusun on 2013-07-18
Hi all,
I need some help. Let me try to be brief:
1) Used Ubuntu and other linux distros for a few years, was generally happy (saved me from Vista hell).
2) Ubuntu began to get too buggy around version 12 and I got discouraged.  Windows 7 was working better with a then-new laptop and switched to Win 7 gradually.  Win 7 also somehow looking slicker than Ubuntu on whichever machine.  
3) Have old-ish office desktop (Intel Core 2 Quad) dual-booting; it runs better on Ubuntu 12.04; want to keep using it to reduce technological waste.
4) Got new laptop (Toshiba Satellite L830-135, top specs) that came with Win 8.  I generally dislike Win 8.  Want to try to use the office desktop and laptop in parallel (not necessarily 100% synced) or supplementing each other. 
5) Colleagues rely on MS Office and .docx, etc. which are not handled well enough in LibreOffice.
6) Got a Canon Pixma printer/scanner that I definitely need to use to full capacity with at least the office desktop.  Came with Win drivers, haven't tried it with Ubuntu (last printer, I wasn't able to utilize that well with Ubuntu). 
7) Heard new Ubuntu (13.04) is a solid release, want to get back to Ubuntu.  But worried about constant switching between OSs, distros, and versions and want to create a stable computing environment across computers. 

Any thoughts and what kind of setup I can create with the desktop and laptop I have?  I really need to sort this out so I can work efficiently. 
I really appreciate all your comments and suggestions.  Thank you in advance!

---

### Post by kokoshmusun on 2013-07-18
Just an update.  I just learned about Kingsoft Office; but I'm not sure if it's 100% compatible with MS Office so I'll have absolutely no problems processing my colleagues files coming from the latter.  Also, it seems to be an MS Office knockoff, so are there gonna be legal issues for this company and will they be forced to shut down by MS?  I don't want to rely on apps that will disappear. 

And another issue came up.  I learned that the newer machines don't do dual-boot that well because of a new kind of bios (UEFI?). Is this the new bios that MS tried to push to force people to choose Windows?

---

### Post by Warren Hill on 2013-07-18
UEFI is a replacement to BIOS and it's being pushed by Microsoft on all machines with Windows 8 pre-installed together with secure boot to make it more difficult for people to install Linux.

It's not impossible however.  I have no personal experience as I don't dual boot.  

Take a look here for instructions 
**[Installing on a Pre-Installed Windows 8 System (UEFI Supported)]("http://askubuntu.com/q/221835/107450")** from[B] [URL="http://askubuntu.com/"]AskUbuntu

[/URL][/B]:guitar:[B][URL="http://askubuntu.com/"]
[/URL][/B]

---

### Post by renegadecookie on 2013-07-18
Hi kokoshmusun!

Yes, Vista could be a hellish experience. Glad you're thinking of coming to The Light. :P

I'm sure it varies from person to person, but I found Ubuntu got buggy around the same time, which I attributed to the Unity interface replacing GNOME. It was probably my hardware (underpowered netbook), but I knew a lot of people who didn't like it, and the bugginess left when I switched to GNOME. That's just my experience, though.

I'm also sure that you could find drivers for that printer. It may even do it automatically, but it's been a while since I needed a printer with my system.

As for a setup, I would say to keep the office desktop as Windows if that's what your coworkers all use, but put Ubuntu on the laptop, especially if you don't like Windows 8.

Hope this is helpful!
-RC

---

### Post by pdc on 2013-07-18
> Got a Canon Pixma printer/scanner

............tell us which model......................

---

### Post by kurt18947 on 2013-07-18
It seems like Canon might be offering more linux support.  If you're in N. America though you may not have much luck on Canon's N. America sites.  Canon-Europe or Canon-Asia might prove more fruitful.  The hardware I purchase is guided in large part by the company's support for linux.  They don't support linux, I don't support them.  I've also been known to let them know via a snail mail letter to the powers-that-be why I bought their competitor's product.

---

### Post by BBQdave on 2013-07-18
Ubuntu Unity 12.04LTS running smooth and solid on my Toshiba Satellite c655-s5503. A year and few months after 12.04's release, well hardened Linux distro :D

---

### Post by trevm999 on 2013-07-18
I have an older Canon Pixma that I could get installed in 32bit Ubuntu, but I couldn't get it installed in 64bit. I bought TurboPrint and it works well, but it won't help with the scanning if Simple Scan doesn't work for you, But maybe it is more worthwhile to put the $30 towards a new printer that is compatible.  Turboprint does have some nice features, like cleaning and maintenance tools that I find are often absent from linux drivers. 

For Office, you could try buying CrossOver. Word 2007 is rated Silver. Or you could probably get the same result using PlayOnLinux, if you don't mind playing around with that kind of thing. I'm hoping that Office on demand will be available on Ubuntu in the future.

---

### Post by kokoshmusun on 2013-07-19
My printer is a Pixma MG3250.  I haven't tried making it work with Ubuntu.  Gonna google that now.  That is actually the least of my worries as I don't print/scan that often and I can just boot into Win 7 to do that.  After working with this desktop PC again, I see how much faster Ubuntu 12.04 is than Win 7; so I decided to stick with 12.04 here.

As for the laptop, I considered Mint for something different, but being a long time Ubuntu user, I really wanna try 13.04 first.  I'm downloading the .iso now.  I hope it works and if so, I'm back to full-time Ubuntu.  I'll just keep that Win 7 on the desktop if I really need extra sensitive MS Office processing. 

Thanks for the help.

---

### Post by kokoshmusun on 2013-07-19
Well so far, failure:
1) Downloaded Pixma drive from canon website and ran the install.sh = Nothing happens, can't print.
2) Tried live 13.04 USB on toshiba laptop, screen flickered like crazy.  Blaaaah.

---

### Post by pdc on 2013-07-19
here is a how-to on installing the driver for your Canon MG3200 series printer: the driver covers the 3220, the 3250 ...........the 3270...... you get the idea...........

please see post #2

[http://ubuntuforums.org/showthread.php?t=2162764&highlight=Canon+printer](http://ubuntuforums.org/showthread.php?t=2162764&highlight=Canon+printer)

if you copy and paste the commands, it should all work for you; best wishes

---

### Post by kokoshmusun on 2013-07-20
Thanks, I will try the Canon solution.  I just wanna drop the screen flicker solution here if anyone stumbles upon this thread in search of a solution:
1) Enter BIOS, disable secure boot, change boot mode from UEFI to CSM.  This solved the initial flicker.
2) When I installed Ubuntu (yes, I couldn't stand Win 8 and wiped it out); I had black screen with occassional flicker at log-in (though I would hear the log-in sound and knew that installation had gone well).  I couldn't see anything and do anything.  I solved that using the instructions here: ubuntuforums.org/showthread.php?t=1613132

---

### Post by kokoshmusun on 2013-07-20
So, I've been on Ubuntu 13.04 on this new laptop for a day.  Here are some observations relating to my doubts:
1) However bad Ubuntu gets, it'll never be worse than Win 8.  I JUST could not stand that thing. 
2) 13.04 is a whole lot better than 12.10, which was unusable because of how buggy it was.  Dash really seems to have become that could save you time. 
3) My biggest problems with 13.04 so far are:
a) Toshiba function keys not working except for volume. Not being able to adjust screen brightness is a big problem right now and also I often take my laptops to lectures where I connect to projector and I need that function key which handles those connections to really work. 
b) gtk-redshift is not doing anything (this is also really important for me, eye protection for those long hours)
c) DVD playing was choppy with VLC even though I installed codecs, etc. 
d) This machine is brand new, has a core i5 processor and very good specs, but I found Ubuntu to be not as fast and snappy.  I was thinking about putting a virtual machine Win 7 but now I have doubts about how fast that will run
e) The laptop fan seems to be always running and the laptop is a bit hot
f) Small glitches are still there: E.g., Auto-hide launcher is graphically useless, app icons sometimes disappear in dash

The list will probably expand a little as I go along, which means hours of trying to fix these problems.  I'm with Ubuntu for now but I've also started thinking for the long-term that I might pick up Debian or Arch, and create a very stable rolling system that I tweak once and for all and use for years to come.

---

### Post by gadnorton on 2013-07-31
I'm using a Canon Pixma 4600 with 13.04 and don't have any issues with it. It was automatically recognized by the OS.

---

