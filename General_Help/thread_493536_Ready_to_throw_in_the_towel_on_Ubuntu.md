---
title: "Ready to throw in the towel on Ubuntu"
date: 2007-07-05
forum: General Help
---

### Post by Mark Phelps on 2007-07-05
Sorry, guys, but I've about reach my limit of fustration using Ubuntu 7.04 Feisty.  I may be a "n00b" by Linux standards, but I'm not new to personal PCs, nor am I new to computers in general -- which is another way of saying I expect setbacks in trying out something new.  And, OK, I shouldn't have believed the hype about Linux being crash-free and worlds better than Windows, but I really wanted that to be true -- really!!

And, true, Linux does have a good support community in that questions posed to the various forums (Ubuntu, Kubuntu, 4Front, NTFS-3g, etc) do get answered with useful suggestions -- not useless garbage like "buy a Mac".

But for the last week, my machine has been seizing up on me every few minutes.  I've googled until I'm blue in the face on this board and others.  I've a stack of paper two inches thick with suggestions of boot options to try.  I've edited /boot/grub/menu.lst so many times I even dream about it! But NOTHING HAS WORKED.  Sorry, folks, but an expensive system that works (Vista) is better than a free system that doesn't (Ubuntu). Yeah, I know, by mentioning THAT OTHER OS in this forum, I've made myself flame bait, but I've been using Windows products exclusively for years now, and Ubuntu has crashed on me more in one week, than Windows XP and Vista have crashed in all the years that I've run them.

Two weeks ago was different -- after a lot of hunting (which I admit, was really fun!), I was able to find Linux equivalents for all but one of my Windows favorite apps and utils. The remaining app is a CD/DVD labeling program I have used for years now, and don't feel up to hand-creating hundreds of CD/DVD labels in GIMP just so I can print them in Linux.  So, I was going to "bite the bullet" and install Wine.  If that (and the app) worked, I was planning on staying away from my Vista system indefinitely.

Then, I installed kubuntu-desktop, having been impressed by screenshots I saw of it, installed Superkaramba (I'm a MAJOR Samurize fan!), installed some KDE apps, and it all started going downhill from there.  My external hard drives no longer automount (using ntfs-3g), my OSS installation (needed for my sound card because ALSA doesn't support it) fails without warning, my file systems corrupt without warning, using Firefox to view Utube videos now crashes my system, my favorite video player (SMplayer) no longer works .. and so on. Instead of having fun in Linux at night, I've spent every evening scouring this and other forums for answers to fixing my growing list of app and system failures.

So, wanting to still use Ubuntu, but having tried it and Kubuntu, I tried installing Xubuntu on another system I have, but I got the dreaded "busybox, can't access tty; job control turned off" errors.  So, I can't even install it on my other box.  And this is a machine that the vendor said couldn't run Windows XP but it runs it OK.  I just wanted to see how well it would run Linux -- and switch over to that if it worked well.

I was looking forward to having Linux -- but I'm spending all my time troubleshooting my system. This is no fun. It's already locked up on me three times tonight.

This last part is my most major disappointment.  Everything I've read on Linux is how it doesn't crash.  Worst case, I've read, is that you can control-key to a command line, enter some commands, and restart X and your desktop.  Not so!  When my machine locks up, everything locks up -- mouse and keyboard. Have to restart using the power button on the machine -- and that trashes my file systems.

BTW, I happen to be a forum moderator on another board and provide technical advice for THAT OTHER OS, so I know how desperate people can bcome  when their system no longer works, and they don't know that they've done anything wrong. I've reached that level of desperation myself.  

Don't know what I'll do now.  Maybe try a different distro (mint?). Maybe just hang it up with Linux and go back to Windows (not the choice I really want).

Anyway, for those who have read my posts and helped me -- many thanks. I'll probably just lurk for a while <G>.

---

### Post by dpar on 2007-07-05
By all means, try a few other distros. Sometimes it takes a few tries to get one that works for you. The new PCLinuxOS 2007 is nice and worked for me out of the box, but then, so did Ubuntu.:biggrin:

---

### Post by apunc1 on 2007-07-05
wow, sorry you're having such a hard time. it sounds like you are having some hardware problems. what are the specifications of your system? i assume it is a newer machine because a) it is an ex-XP machine that has specs to run Vista or b) you bought the machine with vista.
maybe your hardware is incompatible with ubuntu. i haven't read any of your other threads here, but it sounds like you've tried some troubleshooting. i'm thinking another linux distro might better suit your hardware needs. maybe Debian?
good luck.

---

### Post by szf on 2007-07-05
From the posting, I suspect that your Vista-compatible hardware is not Ubuntu-compatible hardware... Can you list the specs - not that I can tell (my latest PC is a plain-jane P4 2.4) but maybe another ubuntuforumite (word?) can.

Btw, if it is hardware I can assure you that it's not just Ubuntu (or GNU/Linux) - I recently tried adding a PCI card to another computer and the video freaked out - under XP SP2.

---

### Post by tagra123 on 2007-07-05
Try dapper, It does work well.  Feisty is working fine on one of our machines, but I wouldn't use it on a machine I needed to count on for everyday use.

If you don't want to try dapper check the error logs. They may at least be able to tell you what is crashing the system. I know when you first start using ubuntu you want to install everything from every repository. This is not the best idea. 

In 2 years I've never experience a crash that required a reboot.

---

### Post by Mark Phelps on 2007-07-05
Apunc1:

Since you asked ...

My machine is a (now ancient, 2-year old) ASUS A8N32-SLI running an AMD 64 4000+ with 2GB of 400MHz DDR RAM, ATI X1600 pro video card, bluegears CMI8788 sound card, 320 GB SATA drive (running XP, Vista, and Kubuntu).

Machine has served me well for XP. Had to be "upgraded" for Vista to 2GB of memory. 

When it didn't lock up every few minutes, it really "screamed" in Linux.  Was hard pushed to get the CPU utilization over 10%!

Perhaps the fact that the AMD chip is a dual-core is part of the problem, but what I read is that Linux is supposed to perform especially well on SMP platforms. 

Perhaps I should have installed the AMD 64-bit version of Ubuntu, but I've stayed away from 64-bit versions primarily because that has been a nightmare in Vista (oops, I said it ... sorry).

I was going to download and install Debian Etch --but then I went to the distro site and found out it was umpteen CDs, or three DVDs. My machine won't stay up long enough to download all that stuff.

I did load Mint 3.0 from its live CD -- but I still like KDE a lot better.

Anyway ... thanks for asking.

---

### Post by NeoLithium on 2007-07-05
I'm on the same route.  Where windows caused hundreds of problems and reboots; I've had very few problems with Ubuntu.  There could have been methods that were suggested that caused more problems than good. While not intentional, it can happen between Ubuntu Version to Ubuntu Version; etc.  Basically a fresh install and following a guide such as something from [http://help.ubuntu.com](http://help.ubuntu.com) or [http://www.ubuntuguide.org](http://www.ubuntuguide.org) is usually a safe bet. Then when problems occur, bring them up.  However, for those of us who are on the forums a great deal to help newer users, we kind of wish we could just help.  I wouldn't worry about being flamed. These forums look down on that a great deal; along with many users that frequent here.

---

### Post by Mark Phelps on 2007-07-05
tagra123:

You're right about the temptation to install everything.  The Apt manager app in KDE lists over 12,000 packages -- almost feel like a kid in a candy store but with all of Bill Gates' money!!

However, I did resist the temptation and only installed a handful of stuff -- OSS for my sound card, NTFS-3G for reading my Windows partitions, and then a few utilities that I missed from Windows.

You make a good point about Dapper.  A lot of what I've read in the forums is about how well stuff worked in Dapper, or in Edgy, and now suddenly, no longer works in Feisty.  Also, somewhere along the line, I've upgraded kernels from 20.15 to 20.16, and now I remember complaints about 20.16 being buggy.

So, I'll see about booting in 20.15 for a few times and see what that does.

---

### Post by apunc1 on 2007-07-05
> **Mark Phelps said:**
> Apunc1:

Since you asked ...

My machine is a (now ancient, 2-year old) ASUS A8N32-SLI running an AMD 64 4000+ with 2GB of 400MHz DDR RAM, ATI X1600 pro video card, bluegears CMI8788 sound card, 320 GB SATA drive (running XP, Vista, and Kubuntu).

Machine has served me well for XP. Had to be "upgraded" for Vista to 2GB of memory. 

When it didn't lock up every few minutes, it really "screamed" in Linux.  Was hard pushed to get the CPU utilization over 10%!

Perhaps the fact that the AMD chip is a dual-core is part of the problem, but what I read is that Linux is supposed to perform especially well on SMP platforms. 

Perhaps I should have installed the AMD 64-bit version of Ubuntu, but I've stayed away from 64-bit versions primarily because that has been a nightmare in Vista (oops, I said it ... sorry).

I was going to download and install Debian Etch --but then I went to the distro site and found out it was umpteen CDs, or three DVDs. My machine won't stay up long enough to download all that stuff.

I did load Mint 3.0 from its live CD -- but I still like KDE a lot better.

Anyway ... thanks for asking.

is feisty the only Ubuntu version you have tried? I concur with tagra123: try Dapper. Its incredibly stable. You can't get as many up to date software, but it sounds like stability is what you're after.  I think you're wise to not try the 64bit version, but i don't know about dual core performance first hand as i don't have one.

---

### Post by NeoLithium on 2007-07-05
> **Mark Phelps said:**
> tagra123:

You're right about the temptation to install everything.  The Apt manager app in KDE lists over 12,000 packages -- almost feel like a kid in a candy store but with all of Bill Gates' money!!

However, I did resist the temptation and only installed a handful of stuff -- OSS for my sound card, NTFS-3G for reading my Windows partitions, and then a few utilities that I missed from Windows.

You make a good point about Dapper.  A lot of what I've read in the forums is about how well stuff worked in Dapper, or in Edgy, and now suddenly, no longer works in Feisty.  Also, somewhere along the line, I've upgraded kernels from 20.15 to 20.16, and now I remember complaints about 20.16 being buggy.

So, I'll see about booting in 20.15 for a few times and see what that does.

Dapper 64 bit might be a good solution for you, in all honesty. sure, it can be a pain in the @$$ for Java and Flash playing, though users on here have made a few simple scripts to help that out.  Check out the Ubuntu guide listed above. Enabling all the repos as per the guide gives you around 20,000+ apps ;)

---

### Post by ramjet_1953 on 2007-07-06
I suspect that your problem is video card related.

I noticed that you have an ATI card.

Unfortunately, ATI in the past was about as Linux unfriendly as you can get. 

They refused to release open source drivers, or even hardware and firmware details, to allow others to write drivers.

Some people find that the current drivers for ATI cards are a bit flakey

I believe that is changing, as they have been bought-out by another manufacturer who has said that they will be working on open source drivers.

I realise that this doesn't help you now, but there is hope in the future.

Regards,
Roger :cool:

---

### Post by MrCheese on 2007-07-06
I just reverted back to Dapper (6.06LTS) on my main pc because Feisty was just too much of a pain. Before you jump ship entirely, give 6.06 a run - it installs way quicker than Feisty, and if you use Automatix to install the bells & whistles can be got up to speed in an hour or so. 

Note - dvd playing - I had to obtain libdvdcss2 from a non-repository source as it seems to have been pulled from the mediubuntu repos used by Automatix.

---

### Post by jespdj on 2007-07-06
> **Mark Phelps said:**
> Apunc1:
Perhaps I should have installed the AMD 64-bit version of Ubuntu, but I've stayed away from 64-bit versions primarily because that has been a nightmare in Vista (oops, I said it ... sorry).

You can't directly compare 64-bit Windows and 64-bit Linux. With 64-bit Windows, people often have problems finding drivers, because manufacturers think the 64-bit Windows market is so small that it's not worth the effort to build drivers for 64-bit Windows.

This is different with Linux; since almost everything is open source, you'll have no trouble finding drivers for 64-bit Linux.

Anyway, are you sure it is not a hardware problem?

Try running memtest86+ for a few hours. It is one of the programs available on the Ubuntu CD. Just boot from the CD and choose "memtest86+" from the menu. This will rigorously test the RAM in your machine for errors. If it reports any errors then your RAM is bad and you should replace it. Bad RAM can cause random crashes and lock-ups.

Does Vista also lockup sometimes, especially when you load a lot of programs at the same time?

---

### Post by Mark Phelps on 2007-07-06
Regarding the possible hardware problem ...

I've run memtest several times and it doesn't generate any errors.  I was running four sticks on this board but it didn't like it and memtest generated errors.  Since I've reverted to two sticks, I've not had any memory errors.

I have read where others with dual-core processors (Intel, not AMD) have had problems and solved them by installing the low-latency kernel.  Since I have very low latency memory (2-2-2-5), I was thinking about installing the low-latency kernel, but when I read up on it, I learned that's not the purpose of the kernel -- low-latency memory.  The advice was not to use it on a general purpose, multi-processor box (which mine is).

I did switch back to Gnome last night, and my machine was a lot more stable.  OSS works again, as do the media player apps.  So, the instability has something directly to do with KDE.

---

### Post by djchandler on 2007-07-08
That's some nice memory specs you have there.

My question has to do with power. What is the output capacity of your power supply? I've had problems as you described in your first post, and your last post is making me think you are needing more power from the power supply than it can keep up with. That may be why the memory problems went away after pulling out two sticks of your memory. You also decreased the power drain on your system. Also, it is possible that Linux will take greater advantage of your cpu's power by running background applications a bit faster than you are used to in Windows. That will also drain more power.

The problems with ATI video cards is well documented. There are workarounds.

Be patient. Even though you didn't have to pay money for Ubuntu, there is no free lunch

One last thought. I would a have a hard time resisting the urge to overclock the cpu with memory specs like that. 

Good Luck,
DJ

---

### Post by southernman on 2007-07-08
I didn't read the entire thread... your OP was enough. ;)

If it's not been suggested yet, why not give the Gusty Gibbon a try. I know, it's in pre-release. I installed it myself and ran it for about two weeks without a hitch, then again I've had only slight hang issues that were caused by firefox/flash/java in Feisty.

I don't have the link to dl Gusty, but here is the link to the release info. You can take it from there...

[http://www.ubuntu.com/testing/tribe1]("http://www.ubuntu.com/testing/tribe1")

Which ever direction you decide to go in, it'll certainly be the best option for you. Either way, good luck.

---

### Post by AmyRose on 2007-07-11
Wow, I'm sorry you're having so much trouble with this. But as people have have been hinting at, Linux is less tolerant of hardware flaws, misconfiguration, or power problems.

Also, while I do not have a 64-bit machine, I am with whoever said to try the 64-bit version. As mentioned, 64-bit Linux is better than 64-bit Windows because the drivers can be ported by anyone who is willing to do it, rather than begging companies to start writing 64-bit drivers. ;)

Well, I wish you the best of luck.

---

### Post by travist120 on 2007-07-11
yeah, I really find that Kubuntu has always given me problems and errors. Just something about it makes my computers shudder. It doesn't matter to me anyway, because I stick to Ubuntu and Xubuntu(on a thrown together old windows ME computer) I'd say the Kubuntu just might not be ready for 64 bit processors. Though then again, I'm a fairly new linux user my self. But I have learned alot from Ubuntu

---

### Post by southernman on 2007-07-11
> **travist120 said:**
> yeah, I really find that Kubuntu has always given me problems and errors. Just something about it makes my computers shudder. It doesn't matter to me anyway, because I stick to Ubuntu and Xubuntu(on a thrown together old windows ME computer) I'd say the Kubuntu just might not be ready for 64 bit processors. Though then again, I'm a fairly new linux user my self. But I have learned alot from Ubuntu

To the contrary, it is probably the other way around whereas - your computer is making Kubuntu shudder. It's generally more about hardware, than about the software. That's not to say there will not be bugs in software code, hence the development/testing/bug reporting process.

Congrats for sticking to it. It's the only way to fly.

---

### Post by AmyRose on 2007-07-11
> **travist120 said:**
> yeah, I really find that Kubuntu has always given me problems and errors. Just something about it makes my computers shudder. It doesn't matter to me anyway, because I stick to Ubuntu and Xubuntu(on a thrown together old windows ME computer) I'd say the Kubuntu just might not be ready for 64 bit processors. Though then again, I'm a fairly new linux user my self. But I have learned alot from UbuntuIt's good that you've decided to stick around.

But if that's an old Windows ME computer, wouldn't it be 32-bit?

---

### Post by djchandler on 2007-07-12
> **AmyRose said:**
> It's good that you've decided to stick around.

But if that's an old Windows ME computer, wouldn't it be 32-bit?

I think he was talking about the dual-core Athlon 64 4000 with the 64-bit OS. This is getting a little tricky, as we are talking about 2 or 3 computers in the thread. I think the Windows ME box is the one running 32-bit Xubuntu.

Now we are talking about my computers.

By the way, I had Ubuntu Feisty running acceptably on a PIII 550, Asus P2B MB, and 512 MB ram. The same basic platform ran with two different Nvidia video cards, first a Riva TNT2 with 16 mb, then I found a GeForce 2 MX 200 with 32 mb in the community surplus exchange, and had no problems with it either. The only funny thing was that the old Riva would support 1360x768 and I can only get the GeForce 2 up to 1280x768, which is okay. I was satisfied with the 2d graphics, but 3D was a no go on the PIII.

I saved my home folder settings via Samba to my XP box I do my work I get paid for on (don't forget the hidden folders), and put in a bargain bin socket 754 motherboard,  had a hand-me-down Athlon 64 2800 available, and re-installed 32-bit Feisty on a 160 gb HDD. Then I copied my .evolution and .mozilla settings over. 3D is OK with the GeForce 2 and 512 mb ram. Everything runs. I'm not messing with 64-bit. The Athlon 64 doesn't penalize you for not running a 64-bit OS as far as I know, where it's my understanding an Intel 64-bit cpu will. I'm happy with it hooked to our Viewsonic 27" LCD HDTV in our living room. I can mount DVD ISOs (install gISOmount) and play them in VLC, and VLC is running absolutely anything else I can throw at it, including DivX files recorded with BeyondTV in XP.

I've never run KDE, and don't see any reason to change from Gnome and Metacity to manage the GUI for me. I haven't a clue why the OP is having the problems he is, but I'm waiting for things to settle down at AMD after acquiring ATI. The have given us enough problems just with all the cpu socket changes they have made in the past couple of years.

Done talking about my computers.

Hang in there OP. Keep it simple. I think I better stop. Can you tell I just had my pain medication and it's kicking in?

Sorry for rambling. But I still think the power supply could be your problem. Just one more word of advice. If things freeze again, instead of using the front power switch, use either the one in the back on the power supply, or unplug it. Hard drives can't write junk in the MBR or some other inconvenient place without any power.

DJ :popcorn:

---

### Post by airtonix on 2007-07-14
cd labeler is available from gnome-files or freshmeat.

---

### Post by ed67 on 2007-07-23
I'm also a fairly new Ubuntu user.  I later installed Kubuntu which I liked but it's not very stable.  Once I nuked the partition and did a fresh install of Ubuntu it's been pretty good.

I've found that I really don't need windows except for filemaker and itunes, which I use on my desktop pc.  I use vnc on ubuntu to access my windows box when needed and I like it a lot.  I recently installed wine and then filemaker in ubuntu, so far so good on that except I can't print.

Firefox, interestingly, will freeze ubuntu hard sometimes though.  Mainly if I'm viewing videos on youtube.  Like hold down the power button to shut off type freeze.

For now I recommend using Ubuntu rather than Kubuntu.  It seems better supported and the forum is better, although you can ask kubuntu questions here too.

It's not completely ready for the mainstream but it's getting there.  I'll keep using ubuntu because it fits my view of the world.  But I have to use windows sometimes and that's perfectly fine too.  It's not an all or nothing decision.

---

### Post by technotika on 2008-02-28
Well for what its worth I'd like to add a few pointers here. I also like the idea of alternative free resources as good as if not better than the expensive. Thats why I have always tinkered about with LINUX distros.

On and off I have battled with mostly fedora and ubuntu to try and get up and running and leave windows behind. Why?

Windows is dull, and since I saw AERO on vista and then COMPIZ on buntz I realised that there is more REAL energy put into linux things rather than windows STEALING ideas , simplifying them for the general public and charging a fortune to then have a virus vortex sat in your living room that  eats memory for breakfast supper and TEA! Bing Bing!

Anyway I have finally got ubuntu up and running and after a hard slog I have learnt a fair bit  - gained some understanding and finally started running with Ubuntu rather than windows. I think there has to be a certain ammount of dedication put in to getting this going and before choosing ubunut or what ever distro I would do some research first as to what is going to give you less of a headache to start with.

I totally familiarize with the plles of print outs for tips and fixes but I (and maybe others)  think I would have benefited from researching what computer equipment  would work with what distro rather than picking a distro and mangling it to work with my computer. I am lucky and have ironed most my glitches but I was close to THROWING the towel in. However ,I wouldnt, I would have  had a break , then come back froma different angle. I think what I am trying to say is you have had a rough deal but learnt alot really by default and maybe can use that to get up and running with linux in a different way. Different distro? You mentioned printing CD/DVD's - I had that issue - dont forget VIRTUALISATION. I went gung ho looking for a cd printing app and then the answer was staring me in the face. Get VMWARE or Virtual Box on there and use that for printing CD's. I now just fire up xp in a virtual box and print through the NAT connection to the printer shared in CUPS.

Hang in there dude  - If I can get it going  - ANYONE can. Good luck!!!!!!!

---

