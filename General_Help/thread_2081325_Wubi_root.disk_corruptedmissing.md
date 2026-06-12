---
title: "Wubi root.disk corrupted/missing"
date: 2012-11-06
forum: General Help
---

### Post by shashwat723 on 2012-11-06
So, let me get this straight.
My question is not exactly the same as the thread but is very similar and related to it.
I did the wubi install as well. For some reason or the other(maybe due to Hard Reboots), I have been unable for a while now to logon to ubuntu (takes me straight to the GRUB PROMPT). 
I have spent around 2-3 days now browsing through forums - some of them talk about fixes without Live CD or USB, some of them talk about fixes through the grub prompt itself, some of them talk about replacing wuibldr files in the windows partition(that still works), some of them ask to do the chkdsk /r. NONE of them have worked.
But, infact what I noticed was in my particular case the root.disk file has been completely erased, don't know how that happened.
Today I stopped trying all the methods that dealt with trying to work around having a live cd. I went and got myself a bootable USB for the same ubuntu version 12.04 LTS that I was previously using. Then I started reading about tools which help recover data, after which re-installing ubuntu wouldn't be a problem. That's when I came across stuff like Testdisk, Photorec but in the countless forum posts I've read (it's hard to find something specific - wish there was an official post talking about it one way or the other because The dreaded grub prompt error is a common thing dual boot people face - and it's even more dreaded on wubi based ubuntu)
My question is simple - Are there any data recovery tools out there that can possibly work on file systems that run on virtual drives - basically mounted as an application on top of another file system? If yes, pray tell what are these powerful secret tools that one could use?
Thanks in advance,
Shashwat.

---

### Post by houseworkshy on 2012-11-06
I only saw this because I'd posted in the thread and automatically  subscribed.  Wasn't sure if I should post again as it is rather ouside my  knowlage area but It looks like an emergancy, lost data is the worst of problems, so I'm bumping.  
I don't  like wubi at all so don't use it but have played with virtual box and  think that you are looking at file rather than disk recovery.  The tools  are'nt secret and if you use the link  to the search on distro watch [http://distrowatch.com/search.php](http://distrowatch.com/search.php)  you'll find a lot of live cd's which could be useful.  Tick the boxes  which match your needs; rescue, phorensics, live medium, whatever your  architecture is etc and you'll find a lot.  I'd go with a live cd method  as the virtual drive will now be a deleted file on your ( ntfs or fat ?)  drive.  You'd need compatability with the windows drive and whatever file system the  virtual drive used.
Even though I use a duel drive system I've had  the grub prompt thing too "sudo start gdm" has always got me out of it  and back into the GUI.  I'm aware that it is probably too late this time  and mention it only because you may face this issue again.
If  someone doesn't respond here soon you could try reposting your question  as "need help recovering lost virtual drive on ntfs wubi install" or  something like that.  Specific titles often get the quickest and most  informed responces.  Welcome to the forums, I hope you get the problem  solved soon.
Bump.

---

### Post by shashwat723 on 2012-11-06
Yes, the virtual drive i.e. root.disk was where the ubuntu (ext2?) filesystem was mounted on and it showed up as a file on my NTFS file system(windows). I don't think stuff like sudo works on the grub console. That command prompt says it's "Bash-like" but only supports stuff like ls, mounting based on version number and loop number such as /vmlinuz.....However, since my root.disk file is completely erased( I can see it's 0KB under C:/ubuntu/disks/root.disk) these version numbers etc. do not show up.

---

### Post by shashwat723 on 2012-11-06
I did a deep search using "testdisk" on Deleted partitions under the single partition that I have which is an NTFS partition, the same drive has both windows and the wubi-installed ubuntu.

What happened was that on doing the deep search as mentioned above, I was returned 5 Linux disks, but a message accompanied it saying these drives are not recoverable. What are these linux disks that show up in testdisk?

---

### Post by bcbc on 2012-11-06
The only way I know of to recover a missing root.disk is to run chkdsk and look in the \found.000 (found.???) folders. 

If the root.disk is corrupted and/or moved to the \found.000 folders then there is no 'deleted' file to recover. It's either corrupted, or it's just referenced by a new file name/location. 

I assume you've seen[ this]("http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html") in your search... if that doesn't work, then I would suggest using photorec or something like that to see if it can extract raw files from the disk.

---

### Post by shashwat723 on 2012-11-06
Hey bcbc,
First of all, good to see your comment online. Thanks for all the help you've been providing people about stuff like this. I'm sure it's very valuable, the time of yours that you choose to spend it on threads like these. Extremely fruitful for us I must say.

Anyway,  it's not the missing root.disk that's the problem. It's more that it's been corrupted i.e. completely erased. I can't find another file in found.00x that might resemble root.disk or have a size close to that of root.disk.

So running a deep search on 'testdisk' on my partition /dev/sda1 actually showed me something interesting, apart from identifying NTFS(windows partitions) it actually showed me 5/6 different Linux partitions that it then flagged as "This partition cannot be recovered"

---

### Post by Elfy on 2012-11-06
moved to it's own thread

---

### Post by bcbc on 2012-11-06
It may be that testdisk sees the root.disk as a partition. In a sense, that's what it is.

In the worst case scenario, would there be certain files you want to recover? Because if that's the case, you shouldn't be using the computer (it may reuse space considered free and overwrite those files). That's the sort of thing photorec does: recover files without respect to the underlying file system. So it should work just as well on the root.disk as other places. The only issue might be the extent of fragmentation of the virtual disk.

Just curious, in the \ubuntu directory, do you have the disks  subdirectory, and then inside that just the swap.disk (and boot), or is  the disks subdirectory missing.

---

### Post by RonanHunt on 2013-04-05
Hi,
 
Iv been having the same problem as shashwat723 with the wubi root.disk being visible in windows under ubuntu/disks buts size is 0 kb. None of the chkdsk stuff seems to work. Im running a deep disk search at the moment with testdisk. Im just wondering if you ever solved this problem?

I have the swap.disk still there and looks like its intact. Thanks in advance.

---

### Post by bcbc on 2013-04-05
RonanHunt

I haven't heard of recovery from a root.disk showing 0 kb. I'm not sure how it gets like that although I speculate that running fsck when there is ntfs corruption may cause that. I always recommend to try in this order 1) chkdsk /f 2) fsck. I know that if you run e.g. boot-repair first it will fsck the root.disk (without checking if the user has run chkdsk to take care of ntfs corruption). I can't say for sure that this causes the loss, but it seems logical to approach it that way. 

The fact is it's not really clear why there ever is any corruption - and why e.g. people like myself who've run the same Wubi install for 1.5 years, including multiple resizes, copies, forks don't get that problem. And the developers think there is no problem, or at least that there used to be one, but not anymore (which doesn't seem accurate to me): [https://bugs.launchpad.net/wubi/+bug/1078959](https://bugs.launchpad.net/wubi/+bug/1078959)

I would try photorec to see if it can find important data. It's a real pain to run though - it will take forever, and find all sorts of junk - so make sure you restrict it to the exact data types you're looking for. Other than that, I recommend always maintaining data backups or better auto-synchronization of data to the cloud, especially with Wubi (although this corruption can and does occur on normal partitions, but probably not as frequently!?)

---

