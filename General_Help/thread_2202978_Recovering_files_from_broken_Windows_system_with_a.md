---
title: "Recovering files from broken Windows system with a LiveCD"
date: 2014-02-01
forum: General Help
---

### Post by fugazi32 on 2014-02-01
Hi there,

Been asked to recover my in-laws' files from their broken Windows system (it's still there, they're having trouble logging in to the machine as it's filled with bloatware and runs out of memory I believe) and as I know you can view a Windows partition from within a *buntu distro I was wondering if there was a way to view the files via a LiveCD/DVD (read only will do) so I can copy their photos and stuff onto an external hard drive for them?

Or if anyone has any better tips or trips to view a Windows partition so I could view/copy files I'd be much obliged!

Many thanks,
Nathan

---

### Post by howefield on 2014-02-01
You shouldn't have any problem completing the task with a Live CD just as you wouldn't with a full install.

The real problem appears to be that they have no backup solution ;-)

---

### Post by fugazi32 on 2014-02-01
> **howefield said:**
> You shouldn't have any problem completing the task with a Live CD just as you wouldn't with a full install.

So I will be able to view the contents of the hard drive from a LiveCD but not modify them?

---

### Post by howefield on 2014-02-01
Yes, boot with the Live CD (or USB) and then mount the windows disk/partition. You have full access to the files just the same as you would were you booting from Windows.

The Windows disk should show in the Ubuntu file manager as per attached example screenshot.

---

### Post by fugazi32 on 2014-02-01
Brilliant, thanks - will try this tomorrow :)

---

### Post by CeejRab on 2014-02-01
Yes, as stated above it will work without any permissions issues that I can foresee. As for a fast performance I would recommend using Lubuntu since the LiveCD runs fast and the desktop environment is very simple and fast also since you mentioned the memory gets bogged. The included pcman file manager in lubuntu should be easy to use as well for transferring files to an external drive. 

All the best,

---

### Post by Duhg on 2014-02-01
I have a similar issue. I was going through a Microsoft Windows update that didn't install properly, and when it went to reboot, it did so continuously. I pulled the drive from the PC and put it in a external box, and was unable to access the drive. Did a virus scan on it and it was showing the files as being intact. It is being listed as drive F:, as opposed to C:. I have since downloaded ubuntu  onto a dvd and booted my laptop with it, and am seeing the drive listed, and the files. I was hoping that I might be able to find some way of getting rid of the update that was downloaded and started causing the problems in the first place. I was going to do a backup using ubuntu, but it was only displaying ubuntu home as the backup source. How can I use a back up to save an 80 gb drive to my 160 gb laptop with only about 83 gb available.I was attempting to do  a copy paste, but there was not enough room. Would a backup take my files and compress them, or could I right click the files and compress and then transfer. Which would be the easiest/best method. I appreciate any help at all.
Thank you,
Duhg

---

### Post by CeejRab on 2014-02-02
Hi duhg,

Two things... What version of windows are you running, and two, does the computer this hard drive is from have a functioning disc drive?

If you have original windows discs for the machine, you can put the hd back into the computer and run a recovery from the windows discs that will restore the os to the way it should be and fix errors.

In the event that all else fails, that's where live cd's packed with open source love come in! 

I would recommend making an archive with ark or 7 zip, whichever you prefer. The archive will be one large file, easier to manage and taking less space since it will be compressed, yet without harming your data. 

As for the free disk space... Trying to put 80gb into a space with only 83gb free is pretty steep... Do you have an external drive you could put it on rather than packing it on the 83gb space? If not, hopefully making an archive will shrink the size down 8% or so and save you some room.

All the best with your project!

---

### Post by Mark Phelps on 2014-02-03
Sorry to have to tell you this, but if you changed the default partitioning scheme on your laptop (as you would in order to install Ubuntu into its own partitions), then it's nearly certain that a factory restore from the Recovery CD will NOT work.  Why? Because it expects the partitions to be their original size and placement, and will go looking for a restore image housed in a Recovery partition on the drive.

IF you really want detailed help with recovering from the Windows Update problems, you should really post your concerns to a Win7 forum -- sevenforums.com.

---

### Post by Duhg on 2014-02-03
CeejRab,
Thanks for your reply.

Windows XP home. I had 2 other drives as well, 200 GB partitioned. and 250 GB.  I was backing up to an external 1 TB drive that bit the dust, shortly after I transfered files from one of the larger drives, which I then deleted. Rather than use that drive to bawrite to, I was looking at ways to recover the data, as it has been said that the info is still there, just the beginning has been modified to make it appear gone, unless it gets written over. The only CD is the Emachines restore disk that will wipe out everything, and reinstall Windows XP.
Currently, I have copied and compressed the files to my laptop with Ubuntu 12.04.3 LTS in Trial mode I have also done a backup with the deja dup backup tool.
I have not done a full installation of Ubuntu to my laptop due to the confusion of whether I will lose files, and the partition aspect, which I am not totally sure about. Partitioning a blank drive is no problem, as I wouldn't be worrying about losing anything.
Last night I put the drive in the PC and did the restore option, with windowsbeing installed again, However, it didn't come up with any screen after the initial windows thingy where the dots scan on by.
Guess it is a question of whether to do restore the backup, with the update fault still in the backup. I did find a .ini file that explained errors occurring during the intallation that caused the issue.

---

### Post by Duhg on 2014-02-03
Mark,

Thanks for your reply.

I have not installed Ubuntu yet. I can guarantee that I will be installing Ubuntu on both computers, as soon as I get around the partitioning and space requirements. My laptop is as is just using the Ubuntu in trial mode.. My PC, C: drive is the one with issues, and I am using an external connection as well as Ubuntu to get access to the files. I tried to use my win7 to access the files originally, and windows wouldn't allow access. So I tried Ubuntu after a flash of inspiration, and was extremely and pleasantly surprised at the access to my files. Definnitely a convert. I tried a Windows forum, and was told I needed to change permissions to get past the denied access prompt.

---

