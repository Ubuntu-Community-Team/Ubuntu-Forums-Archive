---
title: "Copying external HDD data to new NTFS external HDD using Ubuntu 18.04 LTS on USB..."
date: 2020-10-30
forum: General Help
---

### Post by eddie-catflap on 2020-10-30
Hi all, I had a failing (5TB, NTFS) external HDD so bought a replacement. Plugged new 6TB replacement in under Windows 10, created 1 big NTFS partition, tried copying files from failing 5TB external to new 6TB external but got multiple filesystem errors (due to failing 5TB) which lock/freeze/hang Windows 10 (tx MS....).  

 So to test new drive I copied 1.5TB of backup data from another (old 2TB) HDD to the new 6TB external HDD and all good - Windows sees files and they're usable...etc. Boot into Ubuntu 18.04 LTS from a USB, because I'm sure Ubuntu will give me less grief than Win10, and I can see and use test files on new external 6TB HDD fine. Plug in failing 5TB drive a few times before it shows up as stable. Can access all data on 5TB drive, so test the waters by copying a few folders from 5TB to 6TB. All good.  

 Next, copy remaining folders across from 5TB to 6TB, getting a few file related errors which I can skip and the errors don't hang the Ubuntu OS (hooray). Hours later, about 2TB copied across (giving 3.5TB total) to the new 6TB external HDD. I can see and use all files. Reboot into Win10 and it only shows the original 1.5TB of test files I copied.

 When I look at the properties of the new 6TB drive it says FS type: fuse. Calling it fuse may be misleading according to other posts I searched for and read. Looking at GParted the 6TB HDD FS shows as NTFS. The msftdata flag is already set on the new 6TB HDD (read this as a suggestion on another post) - so n/a in my case. Next, Google issues, read several posts around the Web which don't seem to fit my problem... So I'm a bit stumped as to what to try next. Any thoughts welcome, cheers, EVC

---

### Post by oldfred on 2020-10-30
Fast startup sets hibernation flag.
If filesystem hibernated, you normally cannot write to it if hibernated.
The NTFS system is restored to as it was when hibernation set, so anything after that is lost.
Not sure then if you wrote data when hibernated, which should not a have worked or some other issue.

How did you mount new drive and what tool did you use to copy data?

There is no native NTFS driver as proprietary to Microsoft. So reversed engineered under FUSE.
*FUSE* (Filesystem in Userspace)
Nicknamed:  FUSE -   Famously Underwhelmingly Slow Effort.
[https://en.wikipedia.org/wiki/NTFS-3G](https://en.wikipedia.org/wiki/NTFS-3G)
Various settings when mounting can improve performance.

Potential for improvement:
[https://www.phoronix.com/scan.php?page=news_item&px=Paragon-Read-Write-NTFS-Linux](https://www.phoronix.com/scan.php?page=news_item&px=Paragon-Read-Write-NTFS-Linux)

---

### Post by eddie-catflap on 2020-10-30
Thanks oldfred, I think it may have been a filesystem hibernated / locked issue. I say that because I booted in and out of Win10 and Ubuntu 18.04 several times, same deal, then added a text file to an "invisible to Win10" folder using Ubuntu, just now I reboot into Win10 and bam!, everything appeared.

All copying and mounting was done via Ubuntu 18's std file explorer... Nothing special done really, just plug and play. Cheers

---

### Post by HermanAB on 2020-10-31
BTW when copying a few files, cp is good since the risk is low, but when copying bazillions of files, you should use rsync, since it uses checksums to ensure it was done right.

---

