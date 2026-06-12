---
title: "AutoFsck V2.5 - much improved - loose the annoying boot up check."
date: 2007-10-03
forum: General Help
---

### Post by musther on 2007-10-03
I've just finished testing AutoFsck v2.5 and now released it.

For those who don't know, AutoFsck, is a script I wrote to move the annoying automated disk check (fsck every 30 or so boots) from boot up to shutdown.  It was initially rather crude, but has now come a long way.

This new version is neater than the old ones, and has resolved the main issue which people had with it, namely that it used to reboot the computer in order to run fsck.  Now I've managed to sort that out, and fsck is run on system shutdown

When your filesystems are about due for checking, you're notified when you shut the computer down, and given the chance to check them then, and then power off the machine - while this is happening you're free to do whatever you want.

For more information and downloads, see:
[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

If you've already got AutoFsck 2.0 or later installed, you can simply install 2.5 over the top.

---

### Post by dcstar on 2007-10-03
> **musther said:**
> I've just finished testing AutoFsck v2.5 and now released it.

For those who don't know, AutoFsck, is a script I wrote to move the annoying automated disk check (fsck every 30 or so boots) from boot up to shutdown.  It was initially rather crude, but has now come a long way.
........

So using the **tune2fs** utility to change the default fsck of every 30 mounts on an EXT filesystem was too hard?

The whole point about doing a fsck at startup is so you know that you are about to use a system that has a clean filesystem **before** you commence doing anything important on it, having the check done at the end is pretty pointless as any filesystem corruption then found (and fixed) may well wipe out any data you have changed since the boot up with a corrupt filesystem!

---

### Post by musther on 2007-10-03
Of course using tune2fs isn't too hard, ant it's still an option to regulate how often you want the check to be forced.

When your filesystems are mounted during boot, if they are not clean they are checked, this is the way it should be, and AutoFsck doesn't interfere with that.

But if you have mounted your filesystems more than the max-mount-count number of times, a check will be forced, and routine checking is also important.  The problem is that this routine check (not due to any errors, but just a check run every n boots) may occur when you need your system up in a hurry.  AutoFsck is aimed at desktop users - such users may be wanting to give a presentation, or type notes at a meeting, if their laptop has a 250Gb drive, that's going to take an unacceptable amount of time.

Don't for one moment think I'm disputing the need of checking non-clean filesystems on boot, that would be stupid.

---

### Post by nowshining on 2007-10-03
cool, i'll check this out, :) and thanks for making it.

---

### Post by nowshining on 2007-10-03
need beep or something, then an error on gutsy "installArchives() failed" it could not install for me..

---

### Post by musther on 2007-10-03
It*** wa***s working on Gutsy, but as Gutsy is development, something could have changed.  I'll make sure it works when the final is out though.

---

### Post by nowshining on 2007-10-04
Great. :) on the beep insalled fine, it was just the main script which didn't - i removed beep since i don't need it now.

---

### Post by mpec82 on 2007-10-21
It works on gutsy final?? :confused:

---

### Post by musther on 2007-10-21
Yes it does, see:
[http://wiki.ubuntu.com/AutoFsck](http://wiki.ubuntu.com/AutoFsck)
for download and install instructions.

---

### Post by mpec82 on 2007-10-22
Great, thx :)

---

### Post by zoroko on 2007-10-23
I've used the previous versions and it worked fine for me under feisty. Then I upgraded to Gutsy and reinistalled the new version of the script via .deb. My system hangs and never executes fsck, I'll do some more testing later to determine where it hangs.

Also, is the beep really necessary? Is there anyway to remove it and keep autofsck? The beep is really annoying and inappropriate in situations where very loud beeping is bad, e.g. class, library ...etc.

---

### Post by musther on 2007-10-23
As for the bug on your machine, let me know what you find out when you've had a look, and feel free to email me to discuss it.

As for the beep, when testing I found that laptops (all the ones I got my hands on) route the PC speaker beeps through the soundcard speakers, meaning that in quiet situations where you have the speakers turned down, the beep won't be audible either.  However, if you're referring to desktops in the library or classes, then I take your point, and I'll release a .deb which doesn't depend on beep soon, then installing (or not) beep will be your option to have it beep or not.  

For now, if you email me, I'll tell you how to stop it from beeping by editing the script.

---

### Post by zoroko on 2007-10-23
I actually found a way to stop the beep in another post, I removed it from the kernel modules and blacklisted it. I don't need/want the beep for anything so blacklisting it solved the problem pretty easily. Thanks though for taking into consideration about releasing a package without the dependency on beep.

I do have a question though, Is there suppose to be a popup everytime you shutdown or just when it needs to do a fsck ?  Now, and always everytime I shutdown it asks me whether or not I want to perform a check.


btw.. great script and great idea! I loathed having to wait through the check, and they happened at the worst times. Thank you immensely! :)

---

### Post by musther on 2007-10-23
Hmm, that's interesting, you're the third person who keeps getting the popup every time they shut down.  It's happening to a few people, but still quite a small minority.  Anyway, it seems to be something to do with one of your partitions having a somehow oddly behaving combination of mount count and max mount count settings.  To fix this, download and use the script on the AutoFsck page which changes the frequency of the checks, it can be found (including instructions) here:

[https://wiki.ubuntu.com/AutoFsck#head-ad1707927bc4b1c47386c1f0c53fc5068889a90e](https://wiki.ubuntu.com/AutoFsck#head-ad1707927bc4b1c47386c1f0c53fc5068889a90e)

That should sort it out, if it doesn't, let me know and we'll try to get to the bottom of it.

---

### Post by zoroko on 2007-10-24
This is the last line where it hangs

network manager: <info> SUP: sending command 'Disable_network 0' 

obviously there is trouble shutting down the networking, but why?


Also, I ran that script you pointed me to, to set the count. It didn't work, I still get the pop up on every shutdown.. any ideas?  :confused:

---

### Post by musther on 2007-10-24
Firstly, did you only start getting the hanging problem after install AutoFsck?  It shouldn't do anything until well after the network is shut down.  

Try uninstalling AutoFsck and see if it still hangs.

As for the other problem, can you send me the output of this command:

sudo tune2fs -l /dev/sda2

where sda2 is replaced with one of your mounted partitions.  Please repeat this command for each partition you have.  To see what partitions you have, run this command:

sudo fdisk -l

Don't bother running the command on swap partitions.

You can email me to continue this troubleshooting if you want, it may be quicker and easier.
[email]jmusther@gmail.com[/email]

---

### Post by wesleyer on 2007-10-25
Any chance we might get a Kubuntu-compatible version ?

---

### Post by musther on 2007-10-25
I'd love to provide a Kubuntu version, but currently it's called by GDM when the user ends their session.  It would be possible to use it with KDE, but you'd have to be using GDM as your graphical login manager.

I've asked around a lot, but nobody seems to know how I can call a script, as root, when KDE exits - I'm still working on it though.

Some people are just unwilling to help too, you'd be amazed at the negative reception AutoFsck gets from a lot of die hard Linux users, look at any of the blogs, or the digg pages which have talked about AutoFsck, they're full of comments like:

"what, tune2fs was too hard for you"

"unmm, dude, man tune2fs. ubuntu uses are dumb."

"Why do you reboot your machine so often? I reboot my desktop at work once a month, if that (kernel upgrades are the main reason), my desktop at home less than that"

"My Linux boxes stay up for weeks"

"It's just five minutes"

"Smells like the Windows to Ubuntu switchers are carrying over their stupidity."

"i bet you really like broken filesystems ?"

Thankfully there are also a lot of people who see that most of these comments are narrow minded, why should I only reboot once a year because they do, what a waste of power.  
And for the record, (and for the millionth time), the only fsck which AutoFsck interferes with is the 'just in case' one which happens periodically.  This check will not make your date a lot safer generally, but it will catch any errors which sneak in, and as such it doesn't matter when it's run, as long as it is reasonably regularly.  Also, if you read the info about how AutoFsck works, you'll see that it doesn't even interfere with the periodic check, it just does it before the counter trips it on boot.

Anyway, if anyone can help with a Kubuntu (or xubuntu or whatever) version, please email me and we'll get one working.

I'll keep you posted about the dev process.

---

### Post by wesleyer on 2007-10-26
Hi Musther,

I believe Xreset does that in KDM. Did you have a look at it ?

---

### Post by musther on 2007-10-29
Well done that man!

So, now you can expect a version which works with Ubuntu, Kubuntu, Edubuntu, Xubuntu (which uses GDM interestingly), etc.  Basically it will work with any system running either GDM or KDM.

I was going to make a 2.6 release which was basically the same as 2.5, but also for KDM, but there are a lot of other things (well a few) I can incorporate too, so I'm going to a version 3.  

It's all written and currently being packaged by the very kind volunteer who has been packaging AutoFsck for several versions now, then it'll be tested, and then it'll be released sometime in the next week (if all goes well).  Version 3 will have:

Support for KDM and GDM.
A GUI configuration script which can be accessed through a menu item.
The ability to disable and enable the audio prompt which accompanies the dialogue.
The ability to configure the interval of the checks (the max mount count of the filesystems) from the GUI config script.

And to be honest, I can't think of anything else anyone could want from it, but if there is anything, let me know.

---

### Post by musther on 2007-11-01
Yesterday AutoFsck popped up and aksed me to check my disks, I said yes, it began to shut down, and seemed to hang on shutting down the network, just as zoroko mentioned.

Well, I've done a lot of testing and poking around, and it turns out that it's not hanging, AutoFsck is running normally and is in fact checking the filesystems.  Unfortunately, an update to Gutsy (no idea what) seems to make outputting to the terminal impossible after a certain point, the last line output before that point it the one about shutting down the network.

So, the bottom line is that AutoFsck is working, it's just not telling you that it is, which is a pain.  I don't really think there's anything I can do about it though.

---

### Post by nowshining on 2007-11-02
well on my side AUTOfsck doesn't run at all or asks to, and the script to change the fsck check times didn't seem to work unless I did boot 50 times or rebooted actually and the number was wrong cause it said i rebooted about or more than 20 times as it says by default..

---

### Post by ssam on 2007-11-03
> **dcstar said:**
> The whole point about doing a fsck at startup is so you know that you are about to use a system that has a clean filesystem **before** you commence doing anything important on it, having the check done at the end is pretty pointless as any filesystem corruption then found (and fixed) may well wipe out any data you have changed since the boot up with a corrupt filesystem!

that does not really make sense.

for example, say that i turn my computer on every morning and off every evening.

if fsck would normally run on wednesday morning, what is the harm in running it when i shutdown on tuesday night?

fsck has still run before i do any work on wednesday.

the only case where your argument might hold would be if corruption is most likely to occur when the computer is off. i am pretty sure this is not true. if it was then everybody would be doing a fsck every time they turned the computer on.

---

### Post by musther on 2007-11-03
I have spent a long time trying to explain this to people, and you're absolutely correct, the check is only periodic, so doesn't run before you do any work, any time, it only runs every time you've gone through say 30 boot-work-shutdown.  Unless you're particularly unlucky, and something very bad happens to your disk, which doesn't flag it unclean, and which happens to occur just when you reach that magic 30th boot, then having fsck on boot won't help - and of course the very unlucky thing could happen just before you shutdown, in which case, AutoFsck will help.

As for more damage to the filesystem occurring when the system is running, as far as I have managed to research, you're correct again.  This is because most damage comes from 'software behaving badly' rather than hardware issues.

---

### Post by musther on 2007-11-16
V3 is out, and it supports KDM!

[http://ubuntuforums.org/showthread.php?p=3784742#post3784742](http://ubuntuforums.org/showthread.php?p=3784742#post3784742)

---

