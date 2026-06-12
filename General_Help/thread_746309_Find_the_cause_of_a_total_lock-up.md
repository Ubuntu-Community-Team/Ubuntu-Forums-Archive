---
title: "Find the cause of a total lock-up?"
date: 2008-04-05
forum: General Help
---

### Post by RobbanC on 2008-04-05
Greetings

I'm a little curious (It's almost always a good thing. ;) )

A few days ago, I reinstalled my home server. This morning, for some reason the server was completely locked up.
I was brushing my teeth this morning. I usually wonder around in the house while doing this and I noticed my network switch was blinking like a Christmas tree on my server's port - no other port showed activity. I turned on the screen but there was no life. I tried to push the on/off switch to shut the box down but it ended up in pulling the cord. 
The box started fairly nice again with some errors from fsck on my data-disk (not the system disk). 

**Does anyone have an idéa where to look for errors?**
I've browsed through the following logs but according to them, nothing at all seem to have happened at the time the server froze
- messages
- kernel
- apache error
- dmesg

(And what could the mysterious traffic-to-nowhere from my box have been??)

Regards
// Robban

---

### Post by SOULRiDER on 2008-04-05
What applications are you running?

I used to have problems with some applications leaking memory and killing my computer. You can use the **free** command to see memory usage, but I prefer to run **htop** to see information in a nicer way :)

---

### Post by RobbanC on 2008-04-05
Thanks for the reply and the tip. :)

I wasn't running any special applications at all, since no-one were logged in on the box.

I have a few deamons running though. 
I didn't have htop installed, but the most memory consuming processes according to the "normal" top, sorted after memory usage is right now:

gdmgreeter 2%
xorg 1%
xorg 1%
miniserv.pl 0.6%
hald 0.4%
bash 0.3%
apache2 0.3%
apache2 0.3%
gdm 0.3%
smbd 0.3%
...

I have about 444000k used memory right now (about 40% of the 1GB RAM), it's jumping a bit up and down.
The box have a silly low uptime of about 3hrs so I'll give it some time and see what happens with the numbers. 
I guess the uptime when it hung last night was about 50hrs.

The lock-up might not even come back at all. I was just curious were to look if something like this happens. I had a hardware failure in an older computer, that also locked up now and then. Then I could usually see some last entry in kernel about some /dev/hde error. A valuable information when fault tracing!

---

### Post by RobbanC on 2008-04-06
OK... Something's bad! :(

Memory usage is OK, but my system HDD is not well.

I just saw that fancy indexing didn't work as it used to in Apache, no icons, just text.
I SSH.ed into my box and tried to "cat"  some files, like access.log for apache. I just get a statement "I/O error".
I then tried to run "fsck /dev/sda1". It doesn't even start, I just get a message "Bus error (Core dumped)"
Trying to type "reboot" in the terminal also gives me "I/O error".

I'm sad! :(

---

### Post by canthus13 on 2008-04-06
Sounds like you might want to run SMART utilities to check your drive health. Install smartmontools from synaptic and refer to [The Smartmontools website]("http://smartmontools.sourceforge.net/") for help running and interpreting the results.  I'd also do backups asap just to be safe.

--Me

Err... At least, follow that advice if you can get it to boot. [This]("https://help.ubuntu.com/community/Smartmontools") page should help you set up a script to keep an eye on your drives so that you'll get an early warning about any impending failures.

---

### Post by RobbanC on 2008-04-07
Thanks Canthus!

I've always been running smartmontools, but it didn't show anything special on this hdd. All tests passed etc.

A few minutes ago the drive started to spin up and down and made a lot of interesting noise. Bye bye, drive!
This drive was used about 10 days since new and it replaced my old system hdd that crashed last week. 

Really, tell me the odds of that? :guitar:

---

### Post by canthus13 on 2008-04-07
Wow. That's impressive.  If it happens to a third drive, you might look into other causes... Like maybe a bad power supply or drive controller.

--Me

---

### Post by RobbanC on 2008-04-07
NO! Please... not a third drive! ;)

The first drive was a SATA, this second was a IDE, so they are on different controllers.
While replacing the first drive I also changed the powersupply (and some other things), so the odds were _really_ neat. 

My box is up and running again and I hope it will do so for at least a year or so.

I will look into the smartmon script you linked to. It looked quite interesting.

Rock on! :)

---

