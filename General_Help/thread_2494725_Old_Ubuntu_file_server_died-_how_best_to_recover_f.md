---
title: "Old Ubuntu file server died- how best to recover files. 12.04 I think.."
date: 2024-01-25
forum: General Help
---

### Post by cruiserandmax on 2024-01-25
I had a Ubuntu file server that recently died- I suddenly could not access it from other machines on the network, and now when I try to reboot it the machine will not even display a video signal (built-in HDMI/DVI motherboard video) on boot (though the power light is on and the machine fan runs and I think I hear some hard drive tick noises). I tried waiting a while after rebooting and then ssh'ing into the machine (which I have always been able to do in the past) to see if it was just the motherboard video that went bad, but no response there either- so I think the machine is "dead"... Ubuntu was installed on one drive, and all the files were on another drive. I am mainly interested in recovering the files off the files drive. I was running 12.04 LTS (I forget the sub-version) if that matters.. 

What is the easiest way to mount an read/recover files off the files drive at this point? I have two Windows machines in the house, and a mac laptop, but the machine I was running Ubuntu on is the only nix based machine I had... 

Thanks for any help or guidance!!

PS- I had been running this machine (with the same harwdare/drives!!) starting on 8.04 LTS somewhere in 2012- and besides the week I upgrade to 12.04, and a few updates somewhere along the line, it has run without a reboot happily reading/writing files from our other machines on a samba share- what a great deal!

---

### Post by guiverc on 2024-01-25
What file-system is being used is what detail I'd look for first (the OS on it only matters if it's running, if it's not, its the file-system you read to get data off it)

I'd boot a *live* system and explore the disk from there, starting first by checking out the drive health (ie. querying it's health using its SMART capability).

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) maybe helpful.  

I'd use a *live* system here (probably different hardware) so the drive wasn't in use, as the data will come from the *chips* on the drive, and will let you see if the drive itself is DEAD, dying (*inc. on life support*) & thus you can plan what to do.

If it looks good there, I'd just mount it & explore what is there.  Methods as to mount & where I'd go would vary on details you didn't provide (eg. file-system), as file-system checks maybe needed (*command to perform that varies on fs involved*), as if file-system checks discover errors, you may find it boots normally.

Ubuntu when installed allows you to select the file-system being used, so look at whatever documentation exists on the machine, notes from whomever installed/maintained it etc.

Ubuntu 12.04 LTS is years beyond it's EOL though. 

[https://fridge.ubuntu.com/2017/05/01/ubuntu-12-04-precise-pangolin-end-of-life-reached-on-april-28-2017/](https://fridge.ubuntu.com/2017/05/01/ubuntu-12-04-precise-pangolin-end-of-life-reached-on-april-28-2017/)

---

### Post by HermanAB on 2024-01-25
If the MB is dead, then it is usually easiest to remove the HD and put into a USB adaptor.

---

### Post by TheFu on 2024-01-25
> **cruiserandmax said:**
>  
Thanks for any help or guidance!!

Running unsupported, unpatched OSes is a liability to everyone else in the world.
Install a supported LTS. 22.04 is the current one, connect the HDD to it and mount any storage you want there.  Plan to upgrade the OS every 4 yrs, not longer.  Put it in your calendar.

Also, setup a good backup solution **AND TEST THE RESTORE** process.  You've been extremely lucky, assuming the HDD isn't dead.  Cheap HDDs tend to last 2-5 yrs, then they die.  Quality HDDs come with 5 yr warranties and last 5-10+ yrs.  I have some with 13 yrs of life now, still working, showing no signs of issues.  Many more have died over the 5-10 yr periods.  A few died around 1 yr of use. Typically, cheap 2TB HDDs.   Had an SSD from a respected brand die in the first 30 days. Had a few cheap SSDs last 2-3 yrs before death. My newer respected brand SSD are all working, but haven't hit 5 yrs yet.  It will be interesting to see how long they really last.

12.04 has lots of remote exploits. If the system was on the internet and not protected by other network equipment, it is likely completely pwned.  I wouldn't trust anything on it since around 2017, when standard support ended.

---

### Post by MAFoElffen on 2024-01-26
+1 on putting the HDD into a USB disk caddy, and boot the host from a recent/supported Installer LiveUSB, using the Try Option. 

This is why I take a Installer Live USB, and one of the pieces of gear I take on service calls is a dual-disk USB disk caddy... To recover data from one disk to another.

I won't harp on 12.04 being out-of-support for way too long. It was released 11 years ago, which means the hardware, as a server, was on borrowed time also. I'm surprised the HDD is still working. Average planed lifespan for a server's HDD is 3-4 years before changing out.

---

### Post by cruiserandmax on 2024-01-26
> **TheFu said:**
> Running unsupported, unpatched OSes is a liability to everyone else in the world.
Install a supported LTS. 22.04 is the current one, connect the HDD to it and mount any storage you want there.  Plan to upgrade the OS every 4 yrs, not longer.  Put it in your calendar.

I will take this, and the rest of your suggestions re backup to heart- thanks- this is definitely a wake-up call!

---

### Post by cruiserandmax on 2024-01-26
> **guiverc said:**
> What file-system is being used is what detail I'd look for first (the OS on it only matters if it's running, if it's not, its the file-system you read to get data off it)
...
If it looks good there, I'd just mount it & explore what is there.  Methods as to mount & where I'd go would vary on details you didn't provide (eg. file-system), as file-system checks maybe needed (*command to perform that varies on fs involved*), as if file-system checks discover errors, you may find it boots normally.

Ubuntu when installed allows you to select the file-system being used, so look at whatever documentation exists on the machine, notes from whomever installed/maintained it etc.[https://fridge.ubuntu.com/2017/05/01/ubuntu-12-04-precise-pangolin-end-of-life-reached-on-april-28-2017/](https://fridge.ubuntu.com/2017/05/01/ubuntu-12-04-precise-pangolin-end-of-life-reached-on-april-28-2017/)

So I built-intsalled the system myself in 2012.. I honestly have no recollection of the FS I used when installing. I am going to try the suggestion of booting from a liveUSB (current version) and then trying to mount the drive (I do happen to have an sata USB caddy), and see what happens. The data drive (the one I am trying to recover files from) on this machine was a separate physical drive from the OS/boot drive. But considering I cannot even get the machine to post with the drives detached there seems to be a decent chance that both drives may still be "good"- so maybe I can even recover a bunch of useful scripts I had in my home dir :D .. 

Anyway thanks very much to all for the ideas so far- I will report back on my progress- USB stick just arrived...

---

### Post by cruiserandmax on 2024-01-27
Running 22.04.03 in try mode off a USB stick, and all three HD's from the dead system show up fine via my SATA USB caddy! I went back through my receipts and found that I assembled the dead machine in 2014- so the HD's are all at about the ten year mark and amazingly all in perfect health... I will go ahead and backup all data now- and get new drives after I replace the motherboard- which after a bunch of debugging is the part that has gone south..

I had been using an Intel Celeron based motherboard TDP 10watts- it was mini-ITX and had four SATA ports on the board- All the current ultra low power Intel based motherboards (N100) seem to only have a single SATA port, any recommendations on a <=10W TDP CPU based mini-itx board that will support at least three storage devices?

---

### Post by MAFoElffen on 2024-01-27
Happy that all went well for you.

Think about migrating your data and services to Server Edition 22.04.3. There will be some changes to migrate from init to systemd, and to netplan, but nothing major. Server is Server. If you have any questions with that, feel free to ask them in the Server Section.

I've been testing Server DEV 24.04 which is due for release at the end of April. I am happy with it so far. It will be a great release. There will be little to do to migrate from 22.04.3 to 24.04.

You might also think about a Disaster Recovery Plan. Now you know that things do happen.

---

