---
title: "Computer won't load and MPhys work is on there!"
date: 2014-03-18
forum: General Help
---

### Post by nutfreeangie on 2014-03-18
Hi
My daughter is right at the end of her MPhys. She has 4 years of college work including her final project on her laptop (all Ubuntu), hence urgency. She has run Ubuntu on her laptop OK up to now then it stopped loading properly (sometimes taking 3 or 4 days to finally load), then it said it could only run in low graphics mode but it couldn't actually do that. After 4 days it switched on but says it can't load as there isn't enough space on the hard drive, although she doesn't believe this is correct. In hindsight she should have had a much better processor and probably not run it on a laptop along side Microsoft, but we are where we are now.
Any ideas or help? 
Thanks in advance
Angie

---

### Post by dragonfly41 on 2014-03-18
Since this is your first post we must assume that we need to start from basics.

No point giving lectures to explain that your daughter should keep backups as an insurance policy against such failures.

From your explanation there is both Microsoft and Ubuntu installed on the laptop.

Some questions below which might help us to respond ..

Q1. When you write "along side Microsoft" how was Ubuntu installed.  In a separate partition?  Or is this a dual boot configuration?

Q2. Can you launch the laptop into windows instead of Ubuntu?

Q3. What is the exact message which pops up saying "there isn't enough space on the hard drive"?

Q4. Do you see a dual boot Ubuntu grub menu at startup?   Can you go into Ubuntu recovery mode from that menu?

Q5. Do you have another laptop or PC (you must have to post this to this forum) which could download a Ubuntu iso and burn as Ubuntu Live CD which can be used to inspect your daughter's laptop?

Q6. Do you have experience in removing the laptop hard drive (only if it proves necessary) to place into an external drive enclosure (bought from a shop like Maplins) to be interfaced via USB port on another working laptop?   This option will be a last resort option to consider if your drive cannot be fixed in situ in your laptop.


...

So here are some of the options in a nutshell ..

Can you launch into Ubuntu recovery on grub menu?

Or into Ubuntu command terminal?

If you can launch into Windows we can approach from there.

Otherwise a Ubuntu Live CD as next option.

Finally removing the drive as last option.

...

The MPhys data should be recoverable .. but one step at a time.

---

### Post by ajgreeny on 2014-03-18
If it's not possible to boot to ubuntu it may be more difficult to start sorting out the problem, but I suggest you boot to a live system, either from a DVD or a USB, mount the installed system partitions, and then try to find out what is using all the space.  It may even be possible to clean up the filesystem folders from the live OS and make enough space to get the installed OS running, then it will be a lot easier to look in more detail.
Start with terminal command **df -h** which will show all the mounted partitions, their sizes and percentage used, then we can move on from there.

Is this a full partitioned installation of Ubuntu or is it installed via Wubi, ie from inside a running Windows OS; I am a bit confused as you say the laptop is all ubuntu, then go on to say it is running alongside Microsoft.  Tell us more, please and we'll do our best to help.

At the very worst, it should be relatively easy to get all the important files needed from the laptop hard drive copied to a USB drive and then work on them on another machine, but let's see if we can figure out the main problem and get it running properly.

---

### Post by bookrt on 2014-03-18
I did have an issue one time where ubuntu crashed and generated random files until hdd was full and computer wouldn't boot. I agree with poster above, best thing to do is to make a bootable rescue disk and use it to see what is going on. Start by making a copy of the important data, then see decide if you can delete the erroneous files or do a fresh reinstall.

---

