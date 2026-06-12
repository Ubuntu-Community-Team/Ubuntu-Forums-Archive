---
title: "32 bit vs. 64 bit - which to install?"
date: 2006-10-06
forum: General Help
---

### Post by cronholio on 2006-10-06
My new PC should arrive later today and I am planning to install Dapper on it. CPU will be an Athlon 64. So far my experience is limited to the 32 bit kernels and I am wondering if it's worth the potential trouble to run Dapper 64 bit. I keep hearing about certain software not being available for the 64 bit version, as well as 64 bit related bugs and other software issues.

On the other hand, performance of some applications will probably be better with the 64 bit kernel and also I just found [this thread]("http://ubuntuforums.org/showthread.php?t=270968") which shows that there may be problems running 32 bit Ubuntu on an Athlon 64.

So, what would you suggest? The main uses of the PC will be development (no hardware-specific stuff), surfing and gaming.

---

### Post by Haegin on 2006-10-06
I would recommend 64bit if:
a) You don't need flash, java, wine and maybe some other programs or you can afford to spend time getting them working
b) You want to learn
c) You want the best from your hardware no matter what

I would recommend 32bit if:
a) You just want a working computer and dont care if its not utilising your hardware to the full.

---

### Post by Echo35 on 2006-10-06
I've been attepmting a 64-Bit on my PC and it is kinda hard to get stuff working. Some completely random programs don't work well with 64-Bit and it takes a bit to get working, but it is a good learning experience if that's what you're looking for. It's also much more powerful if you're looking for maximum hardware potential.
 
EDIT: I did install 32-Bit on it in the first palce, and I did not run into any of those listed problems. Not saying they don't exist, but I didn't have much trouble.

---

### Post by mgmiller on 2006-10-06
I have been running 32 bit k7 kernels on my AMD 64 3200+ Since Breezy and then updated to Dapper and have no problems at all.  2 gig ram and geforce 6800 (AGP)  on Asus A8V deluxe mobo.  Using nvidia driver from repo's.

---

### Post by cronholio on 2006-10-06
Thanks for the replies. I installed the 32 bit version and everything seems fine. I will probably try 64 bit on a separate HD when I find the time.

---

### Post by Cronjob on 2006-10-09
I don't see any reason not to use the AMD64 arch. The biggest difference that I've encountered between i386/AMD64 is that it's much harder to get themes and other pretty desktop interface stuff installed and getting FireFox with Flash and audio to work is more of a hassle.

I found that the quickest way to get things working was just to do an install, then get Automatix and use it to setup my nvidia card, Swiftfox/flash/mplayer working and then selected the AUD/DVD/32bit codecs/64bit codecs packages via Automatix.

It would be a bit of a pain to do it all manually, I suppose. I'm just fine dealing with Automatix, though. Anyway, getting swiftfox (firefox, compiled for performance) with flash and mplayer takes all of two mouse clicks in Automatix and then waiting a few minutes while it downloads and installs various packages. It couldn't be easier. And really, the firefox/flash thing is the biggest gripe I can see in moving to AMD64.

---

### Post by Haegin on 2006-10-09
Which other programs have people found that don't work well or are "odd" under 64bit other than firefox, flash, java, mplayer and codecs?
I am considering changing if automatix makes it so easy.

---

### Post by Cronjob on 2006-10-09
> **Human Prototype said:**
> Which other programs have people found that don't work well or are "odd" under 64bit other than firefox, flash, java, mplayer and codecs?

I've been using linux a majority of the time for close to eight years, but only a couple months on the desktop (at least, as far as using a window manager), so my pre AMD64 experience in such an environment is rather limited.

I have various software crashes on any given day, but I don't know that I wouldn't experience those on i386, too. And nothing so serious that simply re-launching whatever app it was doesn't continue just fine.

I use swiftfox with flash and mplayer. I use amarok, thunderbird, mp3tunes' Oboe, BasKet, azureus, kopete, krusader, postgresql 8-1, apache, RadRails, k3b, kaffeine, totem, vnc, gtktalog, pgadmin and a gazillion other apps.

So far, the only real problem I have encountered has been with things like trying to get desktop themes to work under amd64, but I can live with that for now. Also, getting sound to work has been painful (after installing the codecs via automatix, I can play pretty much anything, but mp3 won't play through rhythmbox, listen up and similar players due to gstreamer error messages -- even though I have all the gstreamer stuff installed -- but amarok and xmms and beep are more than enough for my needs).

I also found that upon installing pure kubuntu, I couldn't get the audio to work AT ALL. The only way I can get audio to work is to install ubuntu and then after I'm in the gnome desktop, pulling up a terminal and doing an "aptitude install kubuntu-desktop". Then, launching kde suddenly makes the audio work. So if you're a GNOME guy, no worries. If you're a kde guy, it's a minor inconvenience. For all I know, I might be the only person who experiences this.

After getting frustrated with not being able to use themes and other desktop modifications easily and the audio troubles, I switched to i386. After a couple days, I went back to AMD64. Frankly, I can't see the point in wasting all the extra processing power I've paid for even if there are some minor inconveniences. Plus, I'd rather use AMD64 and help by reporting any errors and participating in discussions online about it to help encourage and refine x64 development for the future.

You might find that you have to install things in a particular order with Automatix, too. I'm not sure. I think that the first couple times I installed kde and automatix stuff, I had flash and everything working... and then after applying a few more things, suddenly they worked no more. The solution I found to this was to keep a text file or notepad where I wrote down each thing I installed via automatix, then run an audio test on ogg and mp3 files. Then if it worked, install the next set of codecs or applications and test all over again. That way I had a roadmap to remember what worked and what didnn't and in what order. However, my last install worked like a breeze.

One thing I would suggest to reduce the amount of time involved should you have any problems is to do a full system backup once you have your system installed and a few minor things working (make sure your networking is functional, video card is setup, resolution is fine, etc). Then do a backup with the methods described in the following thread (you'll want to read through the whole thing to make sure you understand what is going on and any possible caveats or extra steps):

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

That way, if you do something that munges up your system and you decide you just want to reinstall, you can revert to the working system state prior to all the codec installations without going through the entire OS install process which can take awhile.

Frankly, I can't really recall anything other than themes that I couldn't use in AMD64 because I was on AMD64. There was a really amazing screensaver I wanted to use that rocked my world the two days I was on i386 that doesn't have a *.deb for AMD64 (it was something with cool fireworks and a cube where the walls were screenshots of your desktop), but that's it. And I'm sure I could have just compiled from source if I really cared enough.

So my opinion is that people should go for AMD64 and resort to forums and gurus to finesse any wrinkles they come across. Any difficulties are far outweighed by being able to actually use the whole CPU you paid for. And if there is something you *really* have to use that simply doesn't exist on AMD64 (like WINE), you can always run an i386 chroot. I haven't found a need for this yet, though.

As far as firefox/flash/java/mplayer being "odd" under AMD64 -- it's not a matter of them being odd. It's a matter of them only existing in 32bit form. I don't know what's involved in manually setting things up (there are tutorials here in the forums and Ubuntu wiki), because I took the easy way out with Automatix. I literally set Automatix up (which involves making sure you have universe, security and multiverse repositories setup in your /etc/apt/sources.list, adding an automatix repository and then running automatix from the command line (just type 'sudo automatix'). Then select "Swiftfox Browser (32-bit)" and "Swiftfox Plugins (32bit)". Then clicking "OK". That's it. In five minutes, it will have Firefox (well, swiftfox) 1.5.0.7 with java, flash, realplayer and MS fonts working. I think it also sets mplayer up for you. If not, one of the other packages will do it for you.

It's seriously that simple. Some people don't like automatix. Some people don't like swiftfox. I know there are some politics involved, but I have to tell you that even as a seasoned tech geek, I find both to be great for me and they make my life easier.

My system is a AMD64 Athlon 3800+ dual core with 2gb RAM, 512mb 7800gt Nvidia Geforce card on a 30" Apple Cinema Display with an Audigy 2 sound card and four SATA2 drives (3x320gb Samsungs and 1x74gb Raptor). I have wifi installed, but for local speed transfer reasons, I just have the regular NIC configured.

Anyway, with that in mind, here is what I currently have installed from automatix via my automatix.log file. Each line indicates a set of installs conducted at the same time (ie, swiftfox browser and plugins were done in one instance): 

nVidia Driver|Thunderbird 1.5
Swiftfox Browser|Swiftfox Plugins
Multimedia Codecs
32-bit Codecs
AUD-DVD codecs|Extra Fonts|Media Players
Azureus

Hope this helps you out. AMD64 hasn't been out for all that long (even Windows support of it is really iffy - especially when it comes to games) and it can seem daunting, but it really isn't. There's very little that won't work on the architecture either out of the box (ie, apt-get) or without being compiled from scratch (I haven't had to do this for anything on AMD64 yet). I'd say it's totally worth it. And hey, as long as you burn a CD of both, you can always switch back if you don't like it for some reason. :)

---

### Post by Kilz on 2006-10-09
> **cronholio said:**
> My new PC should arrive later today and I am planning to install Dapper on it. CPU will be an Athlon 64. So far my experience is limited to the 32 bit kernels and I am wondering if it's worth the potential trouble to run Dapper 64 bit. I keep hearing about certain software not being available for the 64 bit version, as well as 64 bit related bugs and other software issues.

On the other hand, performance of some applications will probably be better with the 64 bit kernel and also I just found [this thread]("http://ubuntuforums.org/showthread.php?t=270968") which shows that there may be problems running 32 bit Ubuntu on an Athlon 64.

So, what would you suggest? The main uses of the PC will be development (no hardware-specific stuff), surfing and gaming.
The link you are giving it to a hardware issue with an ATI graphics card. If you search the forums for problems with ATI graphics you will find they dont just happen in the 64bit version. But yes there can be problems running the 32bit version on a 64bitt system. In my case, the cdrom is not seen after install.
> **Cronjob said:**
> I've been using linux a majority of the time for close to eight years, but only a couple months on the desktop (at least, as far as using a window manager), so my pre AMD64 experience in such an environment is rather limited.

I have various software crashes on any given day, but I don't know that I wouldn't experience those on i386, too. And nothing so serious that simply re-launching whatever app it was doesn't continue just fine.

I use swiftfox with flash and mplayer. I use amarok, thunderbird, mp3tunes' Oboe, BasKet, azureus, kopete, krusader, postgresql 8-1, apache, RadRails, k3b, kaffeine, totem, vnc, gtktalog, pgadmin and a gazillion other apps.

So far, the only real problem I have encountered has been with things like trying to get desktop themes to work under amd64, but I can live with that for now. Also, getting sound to work has been painful (after installing the codecs via automatix, I can play pretty much anything, but mp3 won't play through rhythmbox, listen up and similar players due to gstreamer error messages -- even though I have all the gstreamer stuff installed -- but amarok and xmms and beep are more than enough for my needs).

I also found that upon installing pure kubuntu, I couldn't get the audio to work AT ALL. The only way I can get audio to work is to install ubuntu and then after I'm in the gnome desktop, pulling up a terminal and doing an "aptitude install kubuntu-desktop". Then, launching kde suddenly makes the audio work. So if you're a GNOME guy, no worries. If you're a kde guy, it's a minor inconvenience. For all I know, I might be the only person who experiences this.

After getting frustrated with not being able to use themes and other desktop modifications easily and the audio troubles, I switched to i386. After a couple days, I went back to AMD64. Frankly, I can't see the point in wasting all the extra processing power I've paid for even if there are some minor inconveniences. Plus, I'd rather use AMD64 and help by reporting any errors and participating in discussions online about it to help encourage and refine x64 development for the future.

You might find that you have to install things in a particular order with Automatix, too. I'm not sure. I think that the first couple times I installed kde and automatix stuff, I had flash and everything working... and then after applying a few more things, suddenly they worked no more. The solution I found to this was to keep a text file or notepad where I wrote down each thing I installed via automatix, then run an audio test on ogg and mp3 files. Then if it worked, install the next set of codecs or applications and test all over again. That way I had a roadmap to remember what worked and what didnn't and in what order. However, my last install worked like a breeze.

One thing I would suggest to reduce the amount of time involved should you have any problems is to do a full system backup once you have your system installed and a few minor things working (make sure your networking is functional, video card is setup, resolution is fine, etc). Then do a backup with the methods described in the following thread (you'll want to read through the whole thing to make sure you understand what is going on and any possible caveats or extra steps):

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

That way, if you do something that munges up your system and you decide you just want to reinstall, you can revert to the working system state prior to all the codec installations without going through the entire OS install process which can take awhile.

Frankly, I can't really recall anything other than themes that I couldn't use in AMD64 because I was on AMD64. There was a really amazing screensaver I wanted to use that rocked my world the two days I was on i386 that doesn't have a *.deb for AMD64 (it was something with cool fireworks and a cube where the walls were screenshots of your desktop), but that's it. And I'm sure I could have just compiled from source if I really cared enough.

So my opinion is that people should go for AMD64 and resort to forums and gurus to finesse any wrinkles they come across. Any difficulties are far outweighed by being able to actually use the whole CPU you paid for. And if there is something you *really* have to use that simply doesn't exist on AMD64 (like WINE), you can always run an i386 chroot. I haven't found a need for this yet, though.

As far as firefox/flash/java/mplayer being "odd" under AMD64 -- it's not a matter of them being odd. It's a matter of them only existing in 32bit form. I don't know what's involved in manually setting things up (there are tutorials here in the forums and Ubuntu wiki), because I took the easy way out with Automatix. I literally set Automatix up (which involves making sure you have universe, security and multiverse repositories setup in your /etc/apt/sources.list, adding an automatix repository and then running automatix from the command line (just type 'sudo automatix'). Then select "Swiftfox Browser (32-bit)" and "Swiftfox Plugins (32bit)". Then clicking "OK". That's it. In five minutes, it will have Firefox (well, swiftfox) 1.5.0.7 with java, flash, realplayer and MS fonts working. I think it also sets mplayer up for you. If not, one of the other packages will do it for you.

It's seriously that simple. Some people don't like automatix. Some people don't like swiftfox. I know there are some politics involved, but I have to tell you that even as a seasoned tech geek, I find both to be great for me and they make my life easier.

My system is a AMD64 Athlon 3800+ dual core with 2gb RAM, 512mb 7800gt Nvidia Geforce card on a 30" Apple Cinema Display with an Audigy 2 sound card and four SATA2 drives (3x320gb Samsungs and 1x74gb Raptor). I have wifi installed, but for local speed transfer reasons, I just have the regular NIC configured.

Anyway, with that in mind, here is what I currently have installed from automatix via my automatix.log file. Each line indicates a set of installs conducted at the same time (ie, swiftfox browser and plugins were done in one instance): 

nVidia Driver|Thunderbird 1.5
Swiftfox Browser|Swiftfox Plugins
Multimedia Codecs
32-bit Codecs
AUD-DVD codecs|Extra Fonts|Media Players
Azureus

Hope this helps you out. AMD64 hasn't been out for all that long (even Windows support of it is really iffy - especially when it comes to games) and it can seem daunting, but it really isn't. There's very little that won't work on the architecture either out of the box (ie, apt-get) or without being compiled from scratch (I haven't had to do this for anything on AMD64 yet). I'd say it's totally worth it. And hey, as long as you burn a CD of both, you can always switch back if you don't like it for some reason. :)

Swiftfox is ok if you dont mind using non free (as in freedom) software for the sake of 1/10 of a second in rendering a page. I would not recommend it if you prefer free and open source software though.
The link in my signature will setup 32bit firefox with plugins, or even IceWeasel(totally free and fast version of firefox) on amd64. No need to use software that changes the licenses on its compiled binaries and restricts the freedoms that even Firefox allows. 
You dont even need to install other applications (automatrix) to install it. There is a setup script that takes all of 2 commands you can copy and paste in to install Firefox and working plugins.

---

