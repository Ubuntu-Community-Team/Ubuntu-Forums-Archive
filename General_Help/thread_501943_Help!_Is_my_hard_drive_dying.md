---
title: "Help! Is my hard drive dying?"
date: 2007-07-16
forum: General Help
---

### Post by allspiritseve on 2007-07-16
I keep getting fsck errors almost every time I boot up, and once in a while have to manually run fsck to clear all the errors before I can start up. Every couple weeks or so things disappear as well, most of the time my firefox and thunderbird profiles... does this mean my hard drive is dying? Are there apps I can download that can analyze the drive? I'm headed to spain soon, I need my laptop in top shape before I head out.

Cory

---

### Post by ramjet_1953 on 2007-07-16
Something does sound amiss.

You can try downloading one of the stand-alone recovery iso disks like SpinRite and see what it says.

Unfortunately, most recovery software is not free, but if you have valuable data to recover, it is well worth a few dollars.

Regards,
Roger :cool:

---

### Post by allspiritseve on 2007-07-16
Well I can use ubuntu (and windows, I have a dual-boot system) just fine... I don't think I'm at the point of data recovery just yet, I just want some sort of app to diagnose my HDD and see if it's near dying.

---

### Post by Immolatus on 2007-07-16
Grab Speedfan from download.com. I know it will run in windoz and it works great. It will give you a % drive health and show the sensor output too.

---

### Post by allspiritseve on 2007-07-16
Fitness 83%, performance 99%... I think I'm ok?

---

### Post by H3g3m0n on 2007-07-16
Try looking at smartmontools, they can diagnose drive problems.

Also might be worth doing a full fsck ie with badblocks, yes to all and such. Can take a while.

---

### Post by allspiritseve on 2007-07-16
what would the command be for a full fsck?

Cory

---

### Post by distroman on 2007-07-16
Might be worth checking your ram as well, in my experience bad ram are able to produce very funny errors.

---

### Post by jespdj on 2007-07-16
Find a program that can monitor the temperature of your harddisk(s).

I have had problems with one of my harddisks in my old computer and found out it was getting too hot (over 50 degrees Celsius). I got random read and write errors. After installing a harddisk cooler (a fan that can be mounted on top of the harddisk) the problems went away.

If your harddisk starts making strange noises (ticks, for example) then you can be quite sure it is dying.

---

### Post by stchman on 2007-07-16
> **allspiritseve said:**
> I keep getting fsck errors almost every time I boot up, and once in a while have to manually run fsck to clear all the errors before I can start up. Every couple weeks or so things disappear as well, most of the time my firefox and thunderbird profiles... does this mean my hard drive is dying? Are there apps I can download that can analyze the drive? I'm headed to spain soon, I need my laptop in top shape before I head out.

Cory

Hard drives for laptop are not that expensive.  If you suspect that the hdd is being problematic then back up your important data.  I have seen laptop hdds on newegg for about $60 for a 120GB model.

I don't know if there is a tell all test to 100% know if the hdd is failing.  How old is the laptop?

---

### Post by Herman on 2007-07-16
Hello allspiritseve, 
Try running the commands in the following link (from a Ubuntu Live CD). especially the third one, [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")

Here's another link about how to run the bad blocks command (also from a Live CD), [Bad Blocks]("http://www.brunolinux.com/04-The_File_System/Bad_Blocks.html"). In Ubuntu it'll be 'sudo badblocks', of course.

I had an old hard drive that failed a while ago, and at first I just noticed a few little problems like you have now. Then each time I ran these commands it would fix it for a while, but the hard drive kept getting worse at a faster and faster rate until it eventually failed for good.
I agree with stchman, hard disks are not very expensive, and in my laptop anyway, they're easy to change. I wouldn't play around if you have important work in there. At least make sure you make good backups much more frequently. 

There's a new app in Ubuntu for monitoring the state of our hard drives, it's called **[[B]smartmontools**]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fsmartmontools.sourceforge.net%2F&ei=sLybRt_nJJO-hAO9gKmrCQ&usg=AFQjCNFHAfqn1W6m4Enqyfmm0VtIsmFdUA&sig2=N33_NMnjUtS33xJyNyJfGw"). [/B]I haven't tried it yet but I have read good reports about it. You should be able to install it in Ubuntu through apt-get or synaptic. 

I don't think you need to pay for any commercial software, I think you'll find that the free software is actually better. :)

Regards, Herman :)

---

### Post by allspiritseve on 2007-08-26
OK, I think I have an idea where all these errors are coming from... since I am dual-booting, I have my home directory on an ext3 partition and it seems like whenever windows has a problem, locks up, or isn't shut down right, then linux finds errors whenever it boots. It is pretty much always that partition that has problems, and pretty much always either my firefox or my thunderbird profiles that are messed with (which are shared over the dual-boot). Is there maybe a problem with the app I use to read/write ext3 with windows?

Cory

---

### Post by hessiess on 2007-08-26
> Well I can use ubuntu (and windows, I have a dual-boot system) just fine... I don't think I'm at the point of data recovery just yet, I just want some sort of app to diagnose my HDD and see if it's near dying.

and

> Is there maybe a problem with the app I use to read/write ext3 with windows?

i had exactily the same problem, cept loosing data all the time, the instant i nuked the win partition, all the problems just vanished, i was also usting the ext3 win driver, so i suspect it has somthing to do with this.

have you ever powerd off windows with the power button with the ext3 partition mounted? i red somwere that this can cuse problems

---

### Post by allspiritseve on 2007-08-26
Oh, lots of times... I believe the program I'm using is ext2fs. Is there a better one? It really is handy to share my firefox/thunderbird profiles though, I wouldn't want to lose that capability.

Cory

---

### Post by hessiess on 2007-08-27
> I believe the program I'm using is ext2fs. Is there a better one?a

not as far as i know;(

only thing you can do is make sore you ALWASE shut down windows propaly
could you manage with just the ntfs3g drivers insted? or have a extra shared partition for sharing data

somthing i uset do do was shere files using a sd card, a memery stick would work just as well

---

