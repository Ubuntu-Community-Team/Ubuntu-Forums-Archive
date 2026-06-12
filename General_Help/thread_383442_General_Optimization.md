---
title: "General Optimization"
date: 2007-03-13
forum: General Help
---

### Post by sgardne on 2007-03-13
Hello all,

I've been using Ubuntu for a few months and I think it's completely awesome. I'm a Windows tech for a local university and have been using windows for a long time and know a lot about how to tweak it and make it run as well as possible. I really like Ubuntu and I'm definitely sticking with it. It's tons easier to install and use. I'm wondering though how to optimize it for speed. I've got a fairly top of the line notebook, and I'd like to get the most out of it I can. I searched around a bit but didn't really find what I was looking for. Basically, what are some things I can do to make bootup and operation as fast as possible? Sometimes booting takes a long time. One of the things people always tout about linux is the lightning fast boot up time. I haven't really seen an improvement over XP in that regard, but I assume it's because I'm not doing something right. Ubuntu does run superbly on the desktop however, but there are times when I think my system seems bogged down when I'm not really doing anything super intensive. 

I've got a Dell Inspiron 6400
Core 2 Duo 2.0GHz
ATI Mobility Radeon x1400
2GB RAM

If anyone could point me toward a general tweak guide or just tell me a few things, I'd greatly appreciate it. Thanks!

-Scott
:guitar:

---

### Post by buuntuu! on 2007-03-13
do you dual boot? it usually leads to slower bootspeed.
the window manager has great influence on your system's speed, go for openbox for example, just about the fastest there is, no eyecandy... lightweight apps also do their share (eg.replace open office and firefox)
the ideal thing would be to do a server install and then start openbox from the command line
see this [howto]("http://www.ubuntuforums.org/showthread.php?t=103806")
have fun

---

### Post by sgardne on 2007-03-13
That sounds like an interesting plan. Would I still be able to use GTK apps like The Gimp if I want to?

---

### Post by tgalati4 on 2007-03-13
Windows users somehow seem focused on bootup speed.  I think it's because they are conditioned to reboot so often--for several reasons.

Under Linux or Mac OS X, you don't have to reboot often, so bootup time is not an issue.  Sure it takes 2 minutes or so on an older laptop, but then I only have to reboot once every 3 weeks or so on a laptop and once every three to 6 months on a desktop.  Most of these reboots are required for security updates.  You can choose not to reboot, but then you don't have the new code running.

I have a music server that I haven't booted for 140 days, but it is overdue for several upgrades.

There are are some tricks to shave bootup time by 10 to 15%, but unless you go to a superslim distro, then "it-is-what-it-is".  Most users will want a full distro anyway, since the slim distros tend to have older kernels and won't have as many applications available that people want to use.

I use standby mode when plugged in, overnight for example, and hibernate when traveling or if the machine is not going to be used for several days.  On a 1 Ghz G4 powerbook, waking from standby is 3 to 8 seconds; waking from hibernate-to-disk (1.25 GB memory snapshot is about 30 seconds).

On a Dell Inspiron 7500 (500 MHz, PIII), wake from suspend is ~40 seconds and wake from hibernate is about ~1:30.  Not much faster than cold boot.  I'm not sure how I could speed up wake-from-hibernate, since the kernel has to go through hardware detection and then reread the memory snapshot.  At least both standby and hibernate work, including resuming the wireless connection.

Because of the design of the Linux kernel and the vast array of hardware that needs proper detection, I don't think Linux boot times will ever really go down.

You could of course modify your kernel and take out the stuff that is not needed by your laptop.  This would be an optimized kernel just for your hardware and presumably it would be faster.  However, don't expect updates to work, because if the basic architecture is tinkered with, then things break quickly.

The bottom line:  you can have a slick, fast machine--"Linux of One" but then updates become difficult, or you can endure slow bootups.  Just don't boot up as often.

Post some specifics to see if your system is comparable to what others are experiencing.  The usual process in Linux is to get it to work first, then get it to work reliably (and with large scale), then tweak it for performance.

---

### Post by buuntuu! on 2007-03-13
> **sgardne said:**
> That sounds like an interesting plan. Would I still be able to use GTK apps like The Gimp if I want to?

yes you would ;)

---

### Post by sgardne on 2007-03-13
Okay I admit, bootup time is not nearly as important to me as speed on the desktop, however after looking at that Oubuntu page, I don't really think that's for me either. I like Gnome and I can deal with a slow bootup. (By the by, I would use standby mode only, but I find that my wireless randomly will not be working after waking up and I have to reboot anyway to get it working again, so I usually just shut down rather than go into standby mode.) 

I'm not really looking to break my system or do anything drastic, I'm just wondering if maybe there are some services I don't need to run or what exactly *is* needed for Gnome, so I know what to kill. How to permenantly stop those services/apps from starting up every time, etc.

Edit: also ram optimization, I've got a fair amount of ram, does Ubu use it efficiently? I have no idea. Also, core 2 duo processing? Am I taking full advantage of that? Again, I have no idea.

Thanks!

---

### Post by buuntuu! on 2007-03-13
if you dislike openbox why not try fluxbox, has more of the classic desktop feel but is still fast.
ram is MEANT to be used in linux, don't worry
about killing apps and core 2... no idea, sorry

---

### Post by Patrick K on 2007-03-13
You can go to System > Administartion > Services and turn off a few things that you don't need. If you don't need Bluetooth or Braille services you can turn those off. There are other items listed. All are optional or they wouldn't be there. It's a place to start.

---

### Post by sgardne on 2007-03-13
> **Patrick K said:**
> You can go to System > Administartion > Services and turn off a few things that you don't need. If you don't need Bluetooth or Braille services you can turn those off. There are other items listed. All are optional or they wouldn't be there. It's a place to start.
Fabulous! This is just the sort of thing I'm looking for. Thanks. Any other sort of hardware optimization techniques or tips would be greatly appreciated as well.:)

---

### Post by Patrick K on 2007-03-13
Make sure DMA is on for your drives. I don't remember the command to check/set this. There is another command to check the read/write speed of the drives, again, I don't recall it. 

Here you go I found it. Type > sudo hdparm -h in a terminal for a list of options. > sudo hdparm --iI /dev/hda shows the parameters for drive "a" (Primary/Master). > sudo hdparm -tT /dev/hdashows read timings. 

This command can set parameters, too. Read the man page before jumping in. Misuse can destroy the data on your drive > man hdparm

Here is a link to some other ideas: [http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)

Of course, turning off any eye candy helps. Just a plain desktop, for instance.

---

### Post by tgalati4 on 2007-03-13
You can turn off ipv6 (search blacklist ipv6 in the forums) and that will speed up web browsing.  

2 GB is plenty of RAM for most applications.  32-bit linux will max out at ~4 GB (3.5 GB useable because of device pointers and address space pointers).  

Putting Ubuntu on a quality, 7200 RPM (or 10,000 RPM) drive will speed both boot up and overall operation.

Go through dmesg and make note of the errors.  Some are common, others could contribute to slow downs.  Search the forum of these error messages to see what is important and what is normal.

Resetting wireless after standby can be accomplished by putting the appropriate reset script in the wakeup script.  Search the forums for wireless suspend for several suggestions.

Most of these problems can be fixed but they require some patience and research on your part.  If you bought a Dell with Linux on it, then these things would have already been fixed.  Dell doesn't exactly offer Linux preinstalled, but they are moving in that direction.

In the meantime, pretend that you are a Billionare Michael Dell, working in a garage to get all of your hardware to work properly under Ubuntu.

Or use Windows.

---

### Post by noynac on 2007-03-13
This is a somewhat dated HowTo on Ubuntu performance:

[http://tinyurl.com/yq7j7s](http://tinyurl.com/yq7j7s)

I fiddled around with these suggestions and many others, and in the end things were about as fast after as they were before. Perhaps you'll have better luck.

---

### Post by glotz on 2007-03-13
You might want to try fooling around with swappiness and disabling some virtual consoles as suggested in [http://interactive.linuxjournal.com/article/8308](http://interactive.linuxjournal.com/article/8308)

---

