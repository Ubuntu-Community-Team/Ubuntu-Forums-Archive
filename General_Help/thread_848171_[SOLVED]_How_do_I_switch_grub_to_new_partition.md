---
title: "[SOLVED] How do I switch grub to new partition?"
date: 2008-07-03
forum: General Help
---

### Post by brundlelinux on 2008-07-03
Long story short... I installed a second Ubuntu on a separate partition.  I then deleted the first partition.  As expected, grub must be switched up to take into account the changes.  However, the partition the grubs boot files were on no longer exists.

What is the procedure for doing a fresh grub install so that my new Ubuntu has the grub files and that the portion of grub residing on the MBR uses those and doesn't try to find the old ones that don't exist anymore?

Also, take into account that because of this, I am currently unable to actually boot into any OS, and I'm using a LiveCD for all access.

Thanks in advance!!

---

### Post by drs305 on 2008-07-03
Take a look at this link:
[How to restore Grub from a live Ubuntu cd]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by brundlelinux on 2008-07-03
Yup.  Already did that.  Problem is, as you read down, you see that some of the grub is actually stored on a partition, not just in the MBR.

For me, this has the effect of restoring the old grub, but giving me the same choices I had before the partition deletion.  I know this is because I have to edit the grub list and I can do that later.  My issue now is that not one of the choices it gives me actually boots me anywhere.  All I get is the error "no bootable at that location" or something to that effect.

And that's where I am now.

---

### Post by eotakos on 2008-07-03
if you don't have time to fix and you're in a hurry...

i would recommend super grub [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

it will help you boot anything available on your pc.  you can download a cd - it's about 4MB - (see on the right-hand side on the webpage) and burn it using the ubuntu live cd.

it's a nice tool to have for tough times :-)

---

### Post by drs305 on 2008-07-03
> **brundlelinux said:**
> Yup.  Already did that.  Problem is, as you read down, you see that some of the grub is actually stored on a partition, not just in the MBR.
And that's where I am now.

I suppose you have also reviewed the grub-update man page and are familiar with the fdisk commands (and which partitions are bootable) and how to inspect your grub menu.lst...

+1 on Super Grub Disk

---

### Post by eotakos on 2008-07-03
by the way! i love your signature line!!!

Ah! something else - using supergrub, you could boot up to your new ubuntu partition, try a grub -install (see the man page for sure) and then you could edit the menu.lst file from there

(at least that's what i would do - i'm a relatively new guy with ubuntu too, but i already have some experience with the grub stuff :-))

---

### Post by brundlelinux on 2008-07-03
Just to expand on my issues a bit more.

I started using Ubuntu back on Edgy.  I did a lot of experimenting and whatnot to get familiar with Ubuntu, and along the way, installed several different desktop environements and Kubuntu desktop.  And all of this along the way with full upgrades to Feisty, Gutsy, and now Hardy.  All-in-all, this left me with a LOT of unwanted artifacts that I wanted to ditch and go to a "cleaner" OS with now that I've figured out what I like and don't like.

Instead of doing it bit-by-bit (especially with a lot of off-repository source installs NOT using checkinstall), I just installed the fresh OS, copied over the media I wanted to keep (700+ ripped music cds) via a mount point, and all was well.  Then it came time to reclaim my old space.

I went to a Gparted liveCD, deleted the old swap partition (the new install added a second) and the original Ubuntu partition.  While there, I went ahead and switched the flag for "bootable" to the new Ubuntu partition.

I now have two issues running concurrently.  First, my grub issue.  Secondly, even when running Gparted from a liveCD with nothing mounted or locked, I cannot resize my Ubuntu partition any larger than it was before, and I have two unallocated areas just sitting there for the taking.  It would make my day if I could get both of these issues fixed.

I'm not familiar with supergrub, but luckily I do have a second functioning Linux box (my wife's comp) to do all my burning and investigating on.

I'm now going to see where the before mentioned ideas get me, and if things go sour, I'll post.  You can bet on it.  ;-)

---

### Post by drs305 on 2008-07-03
> **brundlelinux said:**
> Secondly, even when running Gparted from a liveCD with nothing mounted or locked, I cannot resize my Ubuntu partition any larger than it was before, and I have two unallocated areas just sitting there for the taking. 

Are the unallocated areas adjacent to your ubuntu partition? What error messages do you get when you try to expand your ubuntu partition into the others?

---

### Post by brundlelinux on 2008-07-03
> **drs305 said:**
> Are the unallocated areas adjacent to your ubuntu partition? What error messages do you get when you try to expand your ubuntu partition into the others?

No error messages whatsoever.  It simply does not give me the option to resize the new Ubuntu partition any larger.  I can make it smaller, but not larger.  As for the two unallocated spaces, the only option I get with either is to create a new partition.

As for what you mean by adjacent, I must admit my ignorance with most things involving partitions.  However, applying a bit of intuitiveness and a little assumption, I gather that you are making reference to the fact that Gparted lists the partitions in two "sections" of sorts.  The first Ubuntu partition (the one I deleted) is listed on top.  It WAS sda1.  The next partition is sda3, which is listed slightly indented from the first partition and has the expand/collapse arrow proceeding it.  The next two partition in the list are "attached" under sda3.  In these three partitions, I have an extended partition, the new swap partition from my second Ubuntu install, and the actual second Ubuntu partition.  The last partition listed by GParted is the former swap partition from the original Ubuntu install, which is now 1.something gigs of unallocated space.

As a sidenote.... I just downloaded and burned Super Grub Disk.  Nice app, but wasn't able to help me in any way.  As a matter of fact, I was a little confused (and still am) as to why it only listed 2 partitions on my hard drive at all.  I followed all of the on-screen menus into different areas, but nothing worked or had any effect.  I tried just the blanket grub fix first, and then attempted to manually activate each of the two partitions.  After all the trial and error, here's what I know:

My original grub is restored.  When doing a clean boot from restart with no disk in the tray, the original grub displays, with all original options.  Any selection involving my new Ubuntu partition returns error 17:  Cannot mount the partition.  That includes the original boot, memtest, and recovery.  Any attempt to select anything revolving the older (deleted) Ubuntu returns error code 22:  No partition at that location, which again, pertains to memtest, the actual generic boot, and the recovery mode.  

So, I know I deleted the right one.  I think that's the only thing I did right.

Frankly, I'm lost.  New ideas?  Bueller, Bueller.......

---

### Post by brundlelinux on 2008-07-03
Just as a follow-up for clarification.  I am currently using Gparted from inside the Ubuntu LiveCD.  This is my current partition configuration:

  Unallocated
> /dev/sda3      extended
    /dev/sda5    ext3        (This line is indented to the right on my menu)
    /dev/sda6    linux-swap  (This line is indented to the right on my menu) 
    Unallocated              (This line is indented to the right on my menu)

Not sure if that helps in any way, but can't hurt.  BTW, thanks again to all those who have devoted their time to helping me out.  I cannot express my appreciation enough.

While following the instructions for fixing the grub, find /boot/grub/stage1 returns (hd0,4).  I have tried switching the 4 to 1-5.  Nothing works except (hd0,2), however the setup (hd0) fails on that saying that the partition doesn't exist.

If there is any other information I can provide, just tell me how to get it, and I'll get it.

---

### Post by eotakos on 2008-07-03
now that grub is running again (not booting but running) it would be nice to know which configuration file it uses. open the /boot/grub/menu.lst file on your new ubuntu partition and see if the menu discribed at the bottom of the file is the same you see when booting. if that is the case, then all you need is to fix this menu.lst (i'm attaching mine for you to have a working one)


if nothing of this works you could boot with a live-cd , do a
grub-install /dev/hda  (check that hda is your ide hard disk from gparted)

and then do a   grub --config-file=    and point it to the menu.lst of your new ubuntu part.

that's all i can think of   - hope something of this works - good luck

---

### Post by louieb on 2008-07-03
> My original grub is restored. When doing a clean boot from restart with no disk in the tray, the original grub displays, with all original options. Any selection involving my new Ubuntu partition returns error 17: Cannot mount the partition.

 Need to fix the UUID in 2 files **/boot/grub/menu.lst** and [B]/etc/fstab.
[/B]Use the **blkid** command (can be run from live CD) to list your partitions UUID. Fix as needed.

---

### Post by brundlelinux on 2008-07-03
Stick a fork in it... it's done!!!

Thanks to the earlier heads up about logical Vs. extended in my partition issues, I realized that I first had to add the unallocated space to the extended partition and then serve it up to the new Ubuntu partition.  Since that took an hour and a half, I left it to do it's thing and went out and ran errands.  I returned home to two new posts, both concerning what I had been thinking while out of the house.... that the grub was giving me a bunk report based on the fact that it was reading the unaltered files on the partition and that they needed to be manually edited.  Imagine how delighted I was that I came home to find detailed instructions on how to do the very thing I wanted to do.

My Ubuntu is up and running smoothly with 0% data loss.  

Many thanks to all who contributed.  I'm marking this solved.  Once again, the power of linux is only 50% because of the awesome code.... the other 50% is the community.  Awesome job, one and all.

---

