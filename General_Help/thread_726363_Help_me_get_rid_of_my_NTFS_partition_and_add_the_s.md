---
title: "Help me get rid of my NTFS partition and add the space to my Ubuntu install!"
date: 2008-03-16
forum: General Help
---

### Post by HunterK on 2008-03-16
I want to get rid of my NTFS partition and convert my PC to ALL Linux ext3!  I have attached a screen shot of my current partition setup taken from GParted.

The NTFS partition is at the end of the drive. How would you allocate that left over space?  Do you think my 10GB is enough for the ROOT partition? (It's already half full?!)  Should I just turn off swap temporarily and then tack on the 60GB to my /home partition?

I am the only user of the PC and just use it for home stuff, internet, music, movies etc.  I have my Gutsy install configured just the way I like it and don't want to reinstall if possible.

Can I add some space to the ROOT partition or would that be a pain as it is *before* the /home partition and can't be resized?

Thanks for your help!

---

### Post by logos34 on 2008-03-16
That's plenty for root.  Leave it.

Two approaches as I see it:

1) copy every on the ntfs to /home.  Delete sda2.  Do 

sudo swapoff -a 

to unmount swap.  Delete it.  Make a new /swap at the end of the disk and grow /home sda3 to take up the freed space. Edit swap line in /etc/fstab.  (And possibly /boot/grub/menu.lst if you have a 'resume=' option on your kernel line).  Delete ntfs entry in fstab.

2) Shrink ntfs partition down and make a new ext3 storage partition out of the freed space.  Add it to fstab.

---

### Post by R15I23D05D14Y on 2008-03-16
More importantly, back up everything important first. Not on the same computer. The easiest way to accidentally lose everything is by experimenting with a partition editor.

I personally use the Ubuntu CD/GParted/QParted liveCD ( [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) is good, [http://www.sysresccd.org/Quick-start-guide_EN](http://www.sysresccd.org/Quick-start-guide_EN) for a quick guide, and you have lots of tools handy if you do something wrong) so that there is less worrying about mounting/mounting.

---

### Post by HunterK on 2008-03-16
Thanks.  So, you feel the 10GB is fine for root eh?  What about Virtual Box virtual disks?  Do you know if they will exist in "/" or will I have the option of putting them in /home?

---

### Post by logos34 on 2008-03-17
My only experience in the virtual machines area was with VMWare Server (Xp as guest os).  It's been a while.

---

### Post by bodhi.zazen on 2008-03-17
> **HunterK said:**
> Thanks.  So, you feel the 10GB is fine for root eh?  What about Virtual Box virtual disks?  Do you know if they will exist in "/" or will I have the option of putting them in /home?

You can put them where you will.

---

### Post by jocko on 2008-03-17
> **HunterK said:**
> What about Virtual Box virtual disks?  Do you know if they will exist in "/" or will I have the option of putting them in /home?

I think the default location is in /home/<username>/.Virtualbox/, but you can choose to store them wherever you like.

---

### Post by HunterK on 2008-03-17
Thanks, I thought so.  Well, that clears it all up for me.  I will report back with my results.

---

### Post by HunterK on 2008-03-18
Alright, I took care of this no problem.  First I cleared the line in fstab that auto mounted my ntfs drive.  Rebooted to make sure everything worked correctly.  Then I booted into GParted LiveCD and deleted the ntfs partition and rebooted.  (Tested everything and it worked fine.)  Then finished off the process by deleting the swap, creating it at the end and then and growing /home.

I changed the fstab to use the new UID of the new swap.  

All is well!  Thanks guys!

---

