---
title: "Installed Wubi and after doing updates in Ubuntu, can't get to bootloader anymore"
date: 2007-06-30
forum: General Help
---

### Post by ratatosksv on 2007-06-30
I'm running Windows XP MCE and I installed the most recent version of Wubi with Ubuntu.  After the install in Windows, I booted into Ubuntu from the bootloader menu to complete installation.  Then I booted into Ubuntu again and everything was operating fine.  I decided to install all of the package updates (71 total) and then performed the requested reboot.  Once I rebooted, before it got to the bootloader, it rebooted again.  Now, unless I power down, it will just keep looping this way, never making it to the bootloader.  So now I'm left with no way to boot into Ubuntu or Windows.

The Wubi virtual partition was installed on my Windows boot partition on my first hard disk (C:).  The disk also has a second partition (D:) where I keep all of my data (including my Desktop, My Documents, etc.).  If I have to format the C: partition, I can survive, but I would prefer not to (especially considering all of the tinkering I had to do to get MCE working decently).  Both of these partitions are formatted in NTFS.

I booted the computer up with an Ubuntu LiveCD and I can mount the D: partition, but not the C: partition.  I get the error "mount: wrong fs type, abd option, bad superblock on /dev/hda1, missing codepage or other error".

I've read that Wubi doesn't mess with the MBR, but obviously something got screwed up here.  Anyone have any suggestions?

I'll keep reading through the forum in the meantime, but hopefully someone has an idea of what's going on here.

---

### Post by ratatosksv on 2007-06-30
Well, fortunately running chkdsk from my Windows XP MCE install CD's recovery console solved the problem ([http://ubuntuforums.org/showthread.php?t=469977](http://ubuntuforums.org/showthread.php?t=469977))... But what the hell?  This seems like a pretty common problem with Wubi.  

In another thread on this issue ([http://ubuntuforums.org/showthread.php?t=468445](http://ubuntuforums.org/showthread.php?t=468445)), ago stated, "There are many reasons why that might happen which have nothing to do with wubi. Sometimes hard reboots cause that too. There are lots of windows-only users with such issues."  I've used every Windows OS from 3.1 to Vista (except ME) on dozens of computers, and I haven't needed to run chkdsk to fix problems since the MS-DOS 5/6 and Win3.1 days.  

I'm glad to see CrazyGuy123 working to try to solve these problems ([http://ubuntuforums.org/showthread.php?t=478838](http://ubuntuforums.org/showthread.php?t=478838)), but despite the disclaimer of warranty in the FAQ section of the Wubi website, I have to take issue with the contentions on the website that "Wubi is Safe" or "Simple" if using Wubi can cause these problems.

---

### Post by ago on 2007-07-02
Most (in fact all) of the cases so far, have been with people that hard rebooted their machines. Hard reboots can live the filesystem (any filesystem) corrupted. They are even worse in wubi since it is a nested filesystem. But that mostly makes makes the hosted filesystem (ext3) which becomes more fragile than it would normally be, the hosting filesystem (ntfs/fat32) is as vulnerable as always. Hard reboots are a russian roulette, many times you go through without any issue, but sometimes you compromise your filesystem. We took steps to reduce the damages but we cannot completely protect from hard reboots or other dumb actions.

---

### Post by ratatosksv on 2007-07-02
In my case, I did not do a hard reboot before the problem occurred.  I initiated a soft reboot by clicking on the button to reboot after updates were performed and then ended up in the rebooting loop.  I didn't do a hard reboot until I was forced to because of the never-ending loop.  

I'll admit that I don't know much about file systems beyond writing a basic one almost 10 years ago, but it seems odd to me that a soft reboot (or even a hard reboot) would be corrupting boot information (MBR or otherwise) to make a system unbootable.  

And I think what you said supports my point that these issues don't make Wubi seem "Safe."  You plainly state that it makes the ext3 filesystem more fragile.  You also say that you can't protect from "hard reboots" or "dumb actions," but I think most computer users take "dumb actions" and typically try to solve computer lockups (or perceived lockups) with a hard reboot.  And I've also never seen a hard reboot render a machine unable to get to the bootloader (whether the bootloader was from windows, or lilo, or boot camp).  Even if you put "DO NOT PERFORM HARD REBOOTS" on every window of the installer, I'm sure there are plenty of people out there who don't even know what a hard reboot is.  

Maybe I'm just unlucky, and the people I've read about having similar problems after seeing Wubi mentioned on a blog and then installing are far from the norm.  I wouldn't care about these issues if Wubi weren't being promoted as safe/simple.  

I certainly admire Wubi's goal and appreciate the work that has been put into the development of the project.  But with Wubi trying to become part of Gutsy and with computer users saying, "oh, this seems like a great way to try that Ubuntu thing I've been hearing about," I fear for those people who end up losing time and/or data due to these issues.

---

### Post by ago on 2007-07-03
Let's explain the problem clearly for the benefits of others. 

First, you have to realize that at any time in wubi you have 2 separate filesystems working: the hosting filesystem (generally ntfs, which is used to read the partition containing the virtual disks) and the hosted filesystem (ext3 the one used to read inside the virtual disks). A hard reboot affects both the hosting filesystem and the hosted filesystems in different ways. Problems to the hosting filesystem and hosted filesystem are different and should not be mixed up.

Let's get the myths out of the way first.

Hard reboots are always bad, they are little better than kicking your computer. 

Hard reboots do happen in windows whether you have wubi or not (see for instance [http://everything2.com/index.pl?node_id=1016818](http://everything2.com/index.pl?node_id=1016818) ). There are several thousands windows users each day which end up with a corrupted filesystem and a full (quite profitable) software industry has born to address those issues. MS did not create chkdisk because it is fun, but because windows filesystem does get corrupted. The claim that hard reboots are not an issue in windows is pure bulloks. Ever rebooted you XP to see a blue screen saying something about your disk being checked? I bet you have. That is fs corruption. Whether you can boot or not from a corrupted fs depends on what section of the filesystem gets corrupted. You can usually recover from that using chkdisk or equivalent programs and if you cannot boot you have to run such tools from a CD.

So the question is whether wubi creates more HOSTING filesystem corruption than normal. I can recall 3 people that were not able to boot windows after a hard reboot... ...out of more than 100,000, that's 0.003%. I really do not think that we are out of the ordinary here, particularly considering that people tend to hard reboot in Wubi far more than they do with any other apps (which is normal since wubi installs a full operating system which is way more complex than any other app and new users do not know what to do when they get stacked). Hence I do not think that claims that wubi is "unsafe" are substantiated. When you hard reboot you may corrupt your windows filesystem. Full stop. Whether you use wubi or not is inconsequential. 

There where far more claims about people not being able to boot Ubuntu as a consequence of hard reboot (while still being able to access windows). This is a completely different issue, and it is due to the HOSTED filesystem corruption. Is this because ext3 is more fragile than ntfs? Nope. Ext3 is in fact far more robust than ntfs. But in our case ext3 is nested inside ntfs. What is the implication? The issue is that ext3 tries to save some data to disk to protect against hard reboot, but what happens is that such data instead of ending up on the disk, gets handled by ntfs, which in turn might delay disk writing. If you hard boot such data can get lost. So ext3 might think that its data is recoverable (journal is on hard disk) when that is not the case. Hence ext3 becomes more vulnerable than usual to hard reboots and you might not be able to recover your Ubuntu files after a hard reboot. Differently from the hosting filesystem which is a general problem, in this case the situation is due to wubi configuration (filesystem nesting), you'd have the same problem in any nested configruation (including virtual machines). If hard reboots are a problem for you, the only way around is a full installation. And yes, in Linux you can usually avoid hard reboots, but you have to know what to do (see for instance alt+sysrq key combinations).

Can hard reboots issues be improved for the HOSTED filesystem. A little bit by reducing the time when the filesystem waits before writing out the data. We have already tweaked the linux filesystem in the last release, and since then we had far less reporst about hosted filesystem corruption. Again, that only affects the hosted fiilesystem robustness.

Would a normal Ubuntu installation be more resilient to hard reboots as far as the linux filesystem goes?  Yes, a normal installation journal would not get corrupted as it may happen in a nested setup.

Would a normal Ubuntu installation be more resilient to hard reboots as far as the windows filesystem goes?  Yes and no. If you have the windows partition mounted for writing and you hard reboot while you are writing you can still corrupt ntfs. This is the same whether you use Linux, Windows or any other OS. The issue with wubi is that ntfs is always mounted and every time you write to a linux drive you also write to the windows filesystem, so you are more exposed.

---

