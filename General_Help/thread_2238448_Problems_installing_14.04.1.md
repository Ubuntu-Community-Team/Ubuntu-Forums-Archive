---
title: "Problems installing 14.04.1"
date: 2014-08-07
forum: General Help
---

### Post by ibates on 2014-08-07
Several times in the past several years, as a result of difficulties, I have threatened myself with dumping Ubuntu altogether and simply reverting to Windows.  But each time, I have managed to somehow work out a way to overcome the difficulties, frequently with the assistance of members of this forum.

But this time I have just about had it.

I had been using Ubuntu 12.04 LTS, virtually since day one of its release, and one day, right out of the blue, the splash screen changed itself (well at least I did nothing I know of to change it) to Edubuntu, and then hung.  Dead stop.  I have not been able to recover from that in the last six to 9 months.

So, being a gluton for punishment, I forked out for a new HDD and re-installed 12.04 LTS on that disk and continued on my merry way.  It wasn't so traumatic in that I was still able to access the "failed" previous Ubuntu 12.04 so I could retrieve all my data onto the new disk.

But then, about a month ago, I received a message during an Update that support had been stopped for some graphics thingy in 12.04 and that I should install such and such a package to overcome the problem.  I did.

Big mistake.  Now I have two Ubuntu 12.04 HDD, neither of which work completely.  Even this new HDD results in a message about a system error each time I log in.

So, with the release of 14.04.1 LTS, I decided to upgrade to that.  I downloaded the .iso file, checked the MD5Sum, and set about installing it on the first failed HDD.

It was a trouble free installation.  All the right answers appeared.  Except for one problem.  When I then attempted to boot up, no grub!  Just a grub rescue error message.  So I installed it again.  Same deal.  I can access only access the HDD by booting up on the second "failed" 12.04  HDD, but not from the new 14.04.1 drive.

Much to-in and fro-ing on this forum has yielded much help, but no solution.  So I decided that the best bet would be to do a complete re-format of the HDD just in case something was being carried over from the previous installation.

Amd that is where the problem now lies.  No matter what I do, (I have gone through GPartEd as well), each time I attempt to install Ubuntu, there is no sign of the blank disk until I select "Something else", and then eventually "Install now".  Then each and every attempt results in a dialogue telling me that there is no "root file system" to be found, and the whole business comes to a grinding stop.

I have run out of ideas.  I have studied and applied every way I can find to re-format the HDD and to install from the Live DVD on to it.  But no joy whatsoever.

It is starting to feel like I have no choice whatsoever than to revert to Microsoft rubbish because I can no longer get Ubuntu to work.

I am not a technician, and that is no doubt a limiting factor in this whole saga.

If someone can straighten me out on how to install 14.04.1 on an blank disk, I would be most grateful.  I do run Windows secondarily on this computer, but it is on a completely separate HDD and has been for years.  I can now only access it by booting up on the suspect Ubuntu 12.04 HDD from Boot menu, and from whence I do get a grub menu, which by the way, does not show the 14.04.1 installed disc.

I realise that this post may well be in the wrong category, but be that as it may, at least I can post my problem.

---

### Post by QIII on 2014-08-07
Honestly, you might want to take a breather.  Do something relaxing until tomorrow.  Go out to a movie.

No.  It's not worth it to get so frustrated.  Really.  I'm not trying to be smart.  There's nothing wrong with using Windows if it works for you.

If you want to try installing Ubuntu again, come back tomorrow and see if anyone has answered.

But before you go, please give a good rundown on the specs of your machine.  Also, were these disks ever part of a RAID?

---

### Post by coldcritter64 on 2014-08-08
> **QIII said:**
> Honestly, you might want to take a breather.  Do something relaxing until tomorrow.  Go out to a movie.

No.  It's not worth it to get so frustrated.  Really.  I'm not trying to be smart.  There's nothing wrong with using Windows if it works for you.

If you want to try installing Ubuntu again, come back tomorrow and see if anyone has answered.

But before you go, please give a good rundown on the specs of your machine.  Also, were these disks ever part of a RAID?

+1, posting while frustrated is never a good thing. A link that may help you OP : [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475) Particularly the "Hardware Information" section down the page a bit (Also note number 9 in the general guidlines ;)). Cheers, coldcritter64.

---

### Post by slooksterpsv on 2014-08-08
If you could run boot-repair and just have it get the info - DO NOT RUN BOOT-REPAIR AS IT MAY NOT ENABLE YOU TO GET BACK INTO WINDOWS **only** have it grab the information. It should give you a pastebin link or that that you canpost and we can take a look and see what the partitions say, what grub is doing etc.

---

### Post by ibates on 2014-08-08
Thanks for the speedy replies.  The advice to, in effect, take a cold shower and have a nice cuppa tea, is good.  And I will certainly go and do it.

But just before I go.  I need to make one comment.  "There is nothing wrong with using Windows if it works for you".  This is probably correct, but it was similar frustration which persuaded me to change from Windows to Ubuntu quite a number of years ago.  Windows probably has improved since then, but it certainly would have had a lot of improving to do.  XP is still OK, when it works.  But that is always a bit doubtful.  Security is a nightmare.

I am using a 32 bit Intel dual core processor on an ASUS motherboard, with fast graphics card.  4GB installed RAM.   I run a 320 GB HDD with Windows XP which is used for specific applications only.  There is a 1TB HDD which is used exclusively for media files (Windows format).  It was once a RAID disc, but that was some years ago.  There is a second 320 GB HDD which is an Ubuntu 12.04 HDD (and the one from which this session is booted).  This disc is mounted in a removable tray which can be removed from the computer at any time.  It was removed during attempts to install 14.04.1 which was done from the Live DVD.  It has an unknown system problem so the message keeps reminding me and apart from the odd "hang" operates reasonably reliably.  There is a 2 TB HDD which is used exclusively as a Ubuntu backup drive (not used so much anymore due to backing up to the cloud).  Then there is a 400 GB HDD which is the drive I have been attempting to format in order to attempt a re-install of 14.04.1.  This is because the first attempt to install onto that disc ended up with a grub rescue error message making it impossible to boot from, thus the attempt to re-format and start again.

The basic concept is to have Windows on one HDD and Ubuntu on another with the option to boot from one or another via a Grub menu.  It has been working well for years up until Ubuntu problems which started about the beginning of this year.

There are two DVD drives.  The Floppy drive has been disabled.

I will come back and have another try with a clear head tomorrow.

Thanks.

---

### Post by sudodus on 2014-08-08
There might be traces that cause problems on the drive that was once a RAID disk. But I think the main problem for you is the cooperation between the graphics card and the graphics driver. Please tell us about the graphics card: Brand name and model name/number.

Are you using a proprietary graphics driver? In that case, which one?

One option might be to use Ubuntu without upgrading the kernel beyond a certain point. Have you still got the kernel from before that last upgrade, where the system was borked? Then try to boot into it! If you have removed it, you can install it again

```
sudo apt-get linux-image-  # press tab to get a list of alternatives 'TAB completion'
```

---

### Post by buzzingrobot on 2014-08-08
When you use GParted, or any other partitioning tool, be sure to reboot before proceeding. Otherwise, the new/revised partition table may not be read correctly.  E.g., if you boot into a Live Ubuntu session to partition a disk, reboot before beginning the install.

---

### Post by Rev2010 on 2014-08-08
Just to address a few points in regard to the thread title.

1. Always keep a backup. I use an external hard drive and typically backup every couple of months or so unless I'm going to experiment with some things that could critically affect the OS. This way if anything does go wrong, or some new update screws everything up, I have a backup to revert to. I used to backup before trying new drivers or NVidia vendor drivers since I'd had many times I lost the gui, but now I know how to recover fully from the command line so I no longer bother.

2. If it aint broke don't fix it. If your graphic drivers are working perfectly I think it's often best to stick to using them and not to update. Again, if you have a backup or know how to recover then fine, no issue with updating.

3. Ubuntu *can* be easy to mess up, but really it's often pretty easy to recover.

Hope you get your drive issue figured out. Have you tried nuking it fully then trying again? 

*EDIT - just saw you have a backup drive, but you still decided to do a fresh install rather than a restore?


Rev.

---

### Post by Mark Phelps on 2014-08-08
> I received a message during an Update that support had been stopped for some graphics thingy in 12.04 This could mean that you're using a Radeon video chipset that is one of the HD 2x/3x/4x-series and indeed, restricted driver support ENDED for them with Ubuntu 12.04.1; since then, you're stuck using the default open-source driver.  If that's your video chipset, the same will be true of any release newer than 12.04.1.  If you don't know what you're using, run "lspci" from a terminal and look for the line containing "VGA" -- and post that info back here.

---

### Post by mörgæs on 2014-08-08
Changed the title. Seems like a regular support thread now.

---

### Post by ibates on 2014-08-09
Well; I had a few cold showers and cuppas, so here is the best I can do taken one at a time:

1.  To Mark Phelps - I am attaching the output from lspci

2.  To buzzingrobot - I note your advice about parted and rebooting.  I will check that I have done that.  Thank you.

3.  To sudus - I pasted the command line you provided.  "no such operation", or words to that effect.  But attached is the output from lshw which hopefully helps.

4.  To slooksterpsv - I am not sure as to how to "run" boot-repair, but esure that I don't "run" boot repair.  If you could spell that out for me it would help.  Thanks.

5.  And to mörgæs - Thank you.  It does sound more appropriate.

In the attached files, reference is made to a HDD with Ubuntu 12.04 as a boot disk.  This disk is being used only to access Ubuntu and is removed from the computer before attempting to sortr out installation problems.

If it would help, I can physically remove any combination of HDD quite easily.

---

### Post by ibates on 2014-08-09
An update.

While seemingly impatient, I have been continuing to work my way through this issue.  This is the latest.

I re-installed Ubuntu 14.04 LTS, note: not 14.04.1 LTS.  (I did this mainly to see if the installation program would give me the option of overwriting the 14.04.1 at installation.  It didn't).

So now I have 14.04 LTS installed.  And at boot-up, I am getting a Grub menu, but an irregular Grub menu (which by the way goes nowhere upon selecting the Linux option).

Whereas in the past, at the Grub menu the Linux option always contained the latest kernel details in first line.  Now, I am getting no reference to a kernel, simply the word Linux.  (I can't remember for sure, but it might say "Ubuntu".  And the saecond line is the same with "Recovery mode", also with no kernel details.  There are then the memtest lines, and a line for Windows, and a line for 12.04, with kernel details.

As I said, selecting the first line, "Linux", leads nowhere and I receive a message to the effect that " ...gave up waiting".

What now?

---

### Post by aaditya2 on 2014-08-10
Hey ibates,for this,

> [COLOR=#000000]When I then attempted to boot up, no grub! Just a grub rescue error message.[/COLOR]

can u send an image?

and have u messed up with the disks app?

if u have, try marking the drive bootable by live booting any live OS

---

### Post by slooksterpsv on 2014-08-10
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2014-08-10
You may be booting from an old grub?

Really need to see the info report from Boot-Repair. Just post link it gives after running report. Do not run autofix as that will just install one grub to all drives and with mulitple drives you do not want that.

---

### Post by ibates on 2014-08-14
I thank all of you who attempted to solve this riddle.  The problem is now solved.

With respect to the Grub error; I had installed the grub loader onto the incorrect HDD.  I had directed it to the Ubuntu HDD when of course, it should have been to the Windows HDD.

As for the difficulties of having Ubuntu load and run at all;  I found the solution on the Linux Mint forum.  The solution:  update-nvidia.

That done, everything now runs perfectly and quickly.

---

### Post by oldfred on 2014-08-14
Glad you figured it out.

Often better to keep Ubuntu boot loader on Ubuntu drive and change BIOS to boot the Ubuntu drive. And then keep a Windows boot loader on the Windows drive. It sounds like you had BIOS set to boot Windows drive and it had an older grub. But a few systems only boot from the first drive. 

How did you install nVidia driver. If thru repository it should auto update. But if you install from nVidia directly you have to update it with every kernel update as dpkg does not know you also installed that driver that needs to be merged with new kernel.

---

