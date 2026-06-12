---
title: "CONSTANT Drive Activity with Ext4 format (WD My Passport 2TB Ultra)"
date: 2014-07-22
forum: General Help
---

### Post by johnsmoke on 2014-07-22
Recently purchased a 2 TB WD Passport portable hard drive. Just tried to format to Ext4 with encryption in "Disks" utility and when it's complete and mounted there is constant LED flashing/drive activity. I formatted to NTFS to see if it also did that and it doesn't. I read that Ext3 wouldn't do that, so I am formatting to Ext3 at the moment and still waiting for the format to complete - taking a bit longer. I really wanted to format to Ext4 with encryption, but can't have a drive that is constantly thrashing... Anyone else have this issue? Once I format to Ext3 if that stops the drive thrashing is there a way I can encrpy with LUKS at that point?

---

### Post by johnsmoke on 2014-07-22
Just formatted to ext3 and there's drive activity/blinking every 3 seconds... not the constant thrash that it did with ext4 --- is the blinking every 3 seconds normal? I really wanted an ext4 encrypted drive.... Anyone know a way around this? Should I just return this drive and get an external hard drive that is recommended with Ubuntu?

---

### Post by johnsmoke on 2014-07-23
Anyone? I'm going to return the drive this weekend if I can't fix this issue. Any help would be appreciated.

---

### Post by steeldriver on 2014-07-23
Have you looked at what's writing to the drive? You'd need to install and run (as sudo) iotop

**Some** of the WD drives have an IntelliPark feature (spins them down to save power) which can get in a loop with some filesystems (RAID in particular) - but I don't think that should apply to the Passport series drives (or to non-RAID setups)

---

### Post by johnsmoke on 2014-07-23
> **steeldriver said:**
> Have you looked at what's writing to the drive? You'd need to install and run (as sudo) iotop

**Some** of the WD drives have an IntelliPark feature (spins them down to save power) which can get in a loop with some filesystems (RAID in particular) - but I don't think that should apply to the Passport series drives (or to non-RAID setups)

I will install iotop tonight and report back. Thanks much. Would like to keep the drive if possible, but need to figure out what is going on. Thanks again.

---

### Post by Dennis N on 2014-07-23
The 1 TB WD drive I have is formatted ext3, and if there is no data being read or written, the drive activity light shows no activity. 

That said, your drive is much newer (mine was bought in 2009) and may behave differently, so my observation may not be relevant. Could be normal behavior, but what is being read or written? I checked a  little WD Passport drive (also old, and usb powered), and no activity on that one either unless data is being transferred.

I think the newer ones have more "bells and whistles" - like automatic backup, encryption, and what not. Could that be a factor? 

The 1 TB is ext3 either because there was no ext4 support, or it was still considered new and I stuck to the "tried and true". The little Passport I left as FAT 32 and that works fine with Linux as well. Its only 250 gb.

If you do return your drive, for a desktop computer you might consider a standard hard disk (like WD blue) and put it into a drive enclosure - either usb or esata. I have an esata connected drive (WD Blue, 500 gb) in an external case, always connected to the computer. I love it.

I have bought these in the past (have 4 of them):

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136769](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136769)

---

### Post by johnsmoke on 2014-07-23
> **steeldriver said:**
> Have you looked at what's writing to the drive? You'd need to install and run (as sudo) iotop

**Some** of the WD drives have an IntelliPark feature (spins them down to save power) which can get in a loop with some filesystems (RAID in particular) - but I don't think that should apply to the Passport series drives (or to non-RAID setups)

Any idea how to specify iotop to monitor activity specifically of my external drive?

---

### Post by johnsmoke on 2014-07-23
> **Dennis N said:**
> The 1 TB WD drive I have is formatted ext3, and if there is no data being read or written, the drive activity light shows no activity. 

That said, your drive is much newer (mine was bought in 2009) and may behave differently, so my observation may not be relevant. Could be normal behavior, but what is being read or written? I checked a  little WD Passport drive (also old, and usb powered), and no activity on that one either unless data is being transferred.

I think the newer ones have more "bells and whistles" - like automatic backup, encryption, and what not. Could that be a factor? 

The 1 TB is ext3 either because there was no ext4 support, or it was still considered new and I stuck to the "tried and true". The little Passport I left as FAT 32 and that works fine with Linux as well. Its only 250 gb.

If you do return your drive, for a desktop computer you might consider a standard hard disk (like WD blue) and put it into a drive enclosure - either usb or esata. I have an esata connected drive (WD Blue, 500 gb) in an external case, always connected to the computer. I love it.

I have bought these in the past (have 4 of them):

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136769](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136769)


I tried formatting the drive to NTFS and it behaves properly with that format (no constant activity). It's frustrating because I formatted to Ext4 w/LUKS encryption and it formatted very quickly, so I thought I was good to go, then I look down and just endless disk thrash. The idea was that I wanted something about 2 TB in size and to have it encrypted with Ext4 file system. 

Yeah, bells and whistles could be an issue - a friend of mine said they try to appeals to a bunch of "Windows crap." But I formatted to Ext4, so that should eliminate the crap they put on there... although I did do a "quick" format (without writing zeroes etc..), so maybe a full one would make a difference? Would just take a very long time though on a 2 TB drive, don't know if it would even do the trick.

I guess the Linux market isn't large enough for these companies to have support for it....... Wish they would, because Windows stinks compared to Linux/Ubuntu os!

I guess I'll give this iotop a shot before returning the drive - maybe it's just a process that needs to be disabled and it'll be solved....

---

### Post by johnsmoke on 2014-07-23
Ok I ran iotop and it looks like a process called "ext4layzinit" is running. Did some research on this and apparently this is a process that will run when the drive is mounted for the first time... can take a few hrs even.... So I'm hoping that I'll re-format this drive with encryption in Ext4, then leave it attached for a while, come back later and see if it's done the ext4lazyinit process! Things are looking up! I hope this works.

---

### Post by Dennis N on 2014-07-23
That's very interesting. I googled it and found this page for my own future reference:
[http://www.thomas-krenn.com/en/wiki/Ext4_Filesystem](http://www.thomas-krenn.com/en/wiki/Ext4_Filesystem)
Looks like your problem may be solved.

---

### Post by johnsmoke on 2014-07-23
Yeah, I'm really hoping. I'm going to try it tomorrow later in the day after work, if it resolves itself with the "ext4layinit" then I will report back to this post and mark as solved. Keeping my fingers crossed!

---

### Post by johnsmoke on 2014-07-25
It worked! I formatted last night to Ext4 Encrypted w/LUKS & just let it do its thing... seemed like a good 2-3 hours, then the light went steady and all is well! It's great, it even spins down and goes to an idle state when you do a 'safely remove.' Glad I don't have to make the trip to return this drive now. I'm good to go!

---

