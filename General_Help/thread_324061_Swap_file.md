---
title: "Swap file"
date: 2006-12-23
forum: General Help
---

### Post by i386DX on 2006-12-23
I increased the capacity of my swapparition using gparted. This operation passed without any problems; but now my swapfile isn't recognized anymore on boot. i always have to execute the commands mkswap and swapon.
How can I let my swappartition mount on boot automaticaly?

---

### Post by kidders on 2006-12-23
Hi there,

Check your /etc/fstab. Depending on how you're referencing your swap partition, make sure the UUID or /dev path match the partition you want to use for swap.

If you're an Edgy user, you've probably got a UUID string in there, in which case your /etc/fstab is probably doing what it was designed to do ... ie it's treating your new swap partition as an unrecognised filesystem.

**Edit:**
When you reformat a partition, changing its UUID, Ubuntu Edgy won't (ie Dapper *will*) treat it as though nothing has happened. The default style for Edgy's /etc/fstab is motivated by the notion that treating a new filesystem the same as an old one, simply because they occupy the same /dev entry, might not be a smart idea. It also allows you to physically rearrange your hard disks, without making a mess, since the UUIDs will stay the same, despite the fact that the /dev names may have changed. If you plan on making further changes to your swap partition, feel free to refer to it as /dev/sda3 (or whatever), insead of using its UUID. That way, this problem won't crop up again ... assuming, of course, you're using Edgy!

---

### Post by masonfoley on 2007-05-21
> **kidders said:**
> Hi there,

Check your /etc/fstab. Depending on how you're referencing your swap partition, make sure the UUID or /dev path match the partition you want to use for swap.

Hmmm...I've checked my fstab and my swp partition apparently has no mount point:

```
UUID=4602f7ae-c25e-401d-9270-302fb4df36db none   swap    sw    0    0
```

I'm guessing I simply figure out which partition I have is formatted as swap and change "none" to the correct value?

[B][I]EDIT:  The more I'm reading, the more I think "none" is correct.  Anyone wanna verify that for me?

Also, I never see my swp file being utilized (always at 0%).  At what point does the system write out to the disk?  When all of the physical memory is utilized?  I just get the sense that something isn't set up correctly here.  Must be the paranoia of being a Windows user all these years.  ;)[/I][/B]

---

### Post by kidders on 2007-05-21
Hi there,

Swap doesn't use a mount point. I have no idea what effect specifying one would have, but it certainly wouldn't be good! Specifying the correct partition is all that is required. :-)

---

### Post by masonfoley on 2007-05-21
> **kidders said:**
> Hi there,

Swap doesn't use a mount point. I have no idea what effect specifying one would have, but it certainly wouldn't be good! Specifying the correct partition is all that is required. :-)

That makes sense and that's what my gut was telling me.  As far as being specified, I believe that is done by citing the UUID in FSTAB correct?

Is there a command that I can run by passing in /dev/sda7 as a parameter and it would echo the UUID?  That way I can match it with what is in the FSTAB configuration?

I'm still wondering why it doesn't appear my swap file is ever utilized.  I remember when installing the Gnome packages via Adept, (long process and gobbled up considerable memory along the way), even then I didn't see any utilization of the swap file.  The system was rather sluggish in that state and it made me suspect that the swap file configuration was incorrect some how.

---

### Post by kidders on 2007-05-22
> **masonfoley said:**
> That makes sense and that's what my gut was telling me.  As far as being specified, I believe that is done by citing the UUID in FSTAB correct?Yep. :-) In my opinion though, referring to swap using its UUID can get irritating, because (as I mentioned earlier in this thread) reformatting your swap would cause Ubuntu to drop it. Many of my machines describe swap partitions using their /dev names.

> **masonfoley said:**
> Is there a command that I can run by passing in /dev/sda7 as a parameter and it would echo the UUID?There are a few ways of doing that. Inspecting /dev/disk/by-uuid, or using the **vol_id** command should tell you what's what.

> **masonfoley said:**
> I'm still wondering why it doesn't appear my swap file is ever utilized.Even though swap may be *available*, Ubuntu may choose not to use it, if it doesn't feel like it wants to. (Did I just personify an operating system?!) Once your allocated RAM reaches a certain threshold, swap *should* start being used though. If not, then something is wrong. It is possible, for instance, to alter your kernel's "swappiness", making it more or less inclined to make use of virtual memory.

There are lots and lots of ways of analysing Linux's memory usage. One simple one is to just type **top**, and watch what happens. If the first number after the word "Swap" is zero, then you know Ubuntu isn't using it, because it simply isn't aware it exists.

---

### Post by masonfoley on 2007-05-23
Here is another reason why I don't think my swap file is configured properly.  The computer has been sitting idle for the last two hours since I booted it up.  So I decide to fire up KDE System Guard (performance monitor).  Here are the current stats:

There are 125 processes currently.  Almost all of my 1.5 gigs of RAM are taken up.  There's less than 60mb free. Then there is another snippet of information from the app that says "No swap space available".

Am I not reading this right?

Oh, I modified my "swappiness" from 60 to 20 as well.  There doesn't appear to be any change in performance (but I know my impression can't be terribly accurate).

What am I supposed to take away from those numbers?

---

### Post by kidders on 2007-05-23
Hmm... Well, it sounds as though you don't have any swap. You should really set some up...

[LIST]
[*]Allocate at least 512MiB of disk space (depending on what you want to do with it), if necessary.
[*]Format the swap partition(s) you want Ubuntu to use.
[*]Modify your /etc/fstab if necessary.
[*]Run **swapon** on each swap partition, to avoid having to reboot.
[/LIST]

Tweaking kernel swappiness shouldn't be done lightly, as it can _very_ adversely affect performance. For instance, I would expect the change you mentioned to cause serious lag (assuming you had any swap), especially when using RAM-intensive apps like Java or KDE.

---

### Post by veerakumar on 2007-05-23
Do mkswap -v1 /dev/partition or file
swapon /dev/partition or file

For permanently 
edit /etc/fstab
add entry for swap partition
read man fstab.conf

My opionion
Half or full amount of physical RAM memory
Or as per neccessary. Anything 2Gb for some scientific apps

Thank You

---

### Post by Cruncher on 2007-05-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/90526](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/90526) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				If you do have a swap partition and it was working at one point, but no longer is, then the UUID for that partition may have changed. There is a bug tracker for this:
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/90526](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/90526)
If /dev/sda7 is your swap partition, you can find your current UUID with the hint from kidders:
$ ls -l /dev/disk/by-uuid|grep sda7
Then replace the UUID in your /etc/fstab with that new one. With the new UUID, a 
$ sudo swapon -a
should do the trick. If that didn't help, in my case a reboot did.

> **masonfoley said:**
> There are 125 processes currently.  Almost all of my 1.5 gigs of RAM are taken up.  There's less than 60mb free.
That is quite alright, Ubuntu (or Linux in general) will use any unused RAM for disk caching, which is then freed automatically on demand. Use the command "free" for a more comprehensible overview of your current memory usages: The output line "-/+ buffers/cache" is (more or less) your actual available RAM.
The "free" command will also show you whether your swap space is used - or whether you have any at all, for that matter.

> Oh, I modified my "swappiness" from 60 to 20 as well.  There doesn't appear to be any change in performance (but I know my impression can't be terribly accurate).

With no active swap space, changing the "swappiness" shouldn't do anything. If you *do* have swap space, reducing the swappiness will (try to) prevent swapping out more or less unused parts of allocated memory from running applications - or in other words, clutter your RAM with stuff that some applications hog, but almost never use.
But then I guess discussions about the "swappiness" parameter are always philosophical... :)

Cheers,
Cruncher

---

