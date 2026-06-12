---
title: "Perfect management of directories in Ubuntu 16.04"
date: 2016-11-22
forum: General Help
---

### Post by SnuKies on 2016-11-22
Hello,

I'm currently running linux 16.04 but thinking of going back to 14.04 because of a lot of bugs and mostly because I want to do a fresh install. Also I want to install it along with Windows 7 just for some games.Thus being said, I'd like to tell me how to manage my linux partition (or partitions? is it okay the have one only?) :

1) how much should I have in my swap partition? Are the other partitions I should know about and leave space for them?
2) is there a way I can get my programs not to install in my home directory? Or is it ok for them the be installed there?
3) is it ok to have specific files in specific folder (pictures -> picture, videos->video ...eytc)
4) are 120GB enough for Ubuntu? And is it good to have only 1 linux partition and not 2 like in Windows ? (c:/, d:/ )
5) Do you have any more recommendations? I want to keep new install for as long as possible, so anything si more than welcome.

Looking forward for your hearing.

---

### Post by kpatz on 2016-11-22
1) There's no hard rule for swap size, but I usually make it the amount of RAM plus a little, in case you want to use hibernation.
2) Programs don't install in home (unless you manually download them), just your data goes there.
3) Absolutely.  You'll find default folders such as Documents, Downloads, Pictures, Music etc. in your home folder, and you can create more just like in Windows.
4) 120 GB is more than plenty for Ubuntu.  You can have 1 partition, but you may want to put /home in a separate partition to make reinstalls/upgrades in the future easier.  You could make the root partition 20 GB and the rest for /home.

---

### Post by Mark Phelps on 2016-11-22
Let me try to answer your questions ...

1) Swap: see this article: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

2) Installation: the apps will install according to instructions provided in their packages -- you should not mess with those.

3) Specific files: you can store your personal files anywhere you want, not just in $Home

4) Partitions: Linux will consolidate ALL the partitions into a single filesystem.  I have three different drives that include over a half-dozed partitions and they are ALL accessible in the Linux filesystem.  Windows uses C: and D: to distinguish between the collection of OS-related files and apps (in C:) and personal data (often in D:).  You don't need to make this distinction in Linux because the OS and apps are spread across a lot of different directories.  So, you can keep everything in one partition.

5) Sorry, don't know what you mean by "keep a new install for as long as possible"

---

### Post by papibe on 2016-11-22
Hi SnuKies.
> **SnuKies said:**
> 
1) how much should I have in my swap partition? Are the other partitions I should know about and leave space for them?
The standard is to match your RAM, so can sleep or hibernate the machine. If you don't much RAM, say like 1-2 Gigs, it would be better to have more swap space so your system can handle more applications open at the same time, for instance 4Gb instead of 1 or 2.
> **SnuKies said:**
> 
2) is there a way I can get my programs not to install in my home directory? Or is it ok for them the be installed there?
By default applications are installed someplace else, like /usr/bin for example, not in your directory.
> **SnuKies said:**
> 
3) is it ok to have specific files in specific folder (pictures -> picture, videos->video ...eytc)
That's is common practice. It is not mandatory, it is a personal preference.
> **SnuKies said:**
> 
4) are 120GB enough for Ubuntu? And is it good to have only 1 linux partition and not 2 like in Windows ? (c:/, d:/ )
More than enough for the system. You can install a Ubuntu desktop on about 5 Gigs.

Having more partitions it is usually considered 'better' when you have more experience. It makes some things easier, but it requires a bit more care. The common practice would be to have 2 partitions: one for the system, and one for your personal files. They usually call / (root) and /home. Here you can read more about it: [Partitioning Schemes]("https://help.ubuntu.com/community/PartitioningSchemes").

Having said all that, It would be totally acceptable to just have one partition.

> **SnuKies said:**
> 
5) Do you have any more recommendations? I want to keep new install for as long as possible, so anything si more than welcome.
/ partition 20-30 Gigs
swap partition match your RAM, or at least 4Gigs
/home all the rest.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by SnuKies on 2016-11-22
Thank you all, @papibe, @Mark[COLOR=#000000] Phelps and @kpatz.
After reading your comments, I decided to have 1 partition for windows (~400GB where I will store ...thin[/COLOR][COLOR=#000000]gs), and 2 for Linux ( /root 35 GB, to be sure, /home 195 GB)

Regarding the SWAP memory, I have 8 GB RAM so I'll go for 12 GB SWAP
Also, should I leave some empty space betweend Windows partition and first Linux partition?

EDIT: my HDD will look like these:
- Partition 1: 350 GB for Windows
- Partition 2: 1 GB
- Partition 3(Extended):
    - 3.a ->12 GB for SWAP
    - 3.b ->124 GB for /home
    - 3.c -> 30 GB for /root
-Partition 4: 204 free. What should I do with these? Another Windows partition well I'll store some old files?

(the install I will be done next wednsday. I'll post the results);[/COLOR]

---

### Post by papibe on 2016-11-22
No need to leave space between partitions.

I'd recommend starting the process in Windows. Create as much space as possible there by reducing your partitions to leave space for the Linux installation. 

The installation would do a good job reducing and creating partitions, but it would be an extra step to keep peace of mind.

Sometimes you can't reduce too much at once. Usually if you defrag, and then reduce, you get better results.

Regards.

---

### Post by kpatz on 2016-11-22
You don't need 12 GB swap.  8.1 GB should be plenty.  If you aren't going to use hibernation, you could get away with a smaller swap like 2 GB since Ubuntu uses less RAM than Windows.

You also don't need 124 GB for the root.  Make that one 30 GB and use the rest for /home.  Or make your Windows partition bigger.  Are you going to share files between Windows and Ubuntu?  Are you going to store... "things" in Ubuntu or will you continue to do this in Windows?  That'll determine what you might want to use that remaining space for and what filesystem to format it as.

---

### Post by SnuKies on 2016-11-22
@kpatz yeah, instead of /home I wrote /root.

Well, I was thinking that I could keep torrents, photos, songs in a mutual partition, so ther are accesible from everywhere

---

### Post by Mark Phelps on 2016-11-22
> **SnuKies said:**
> @kpatz yeah, instead of /home I wrote /root.

Well, I was thinking that I could keep torrents, photos, songs in a mutual partition, so ther are accesible from everywhere

To do that, you want a shared DATA partition, formatted NTFS.  Linux can read and write NTFS partitions just fine, and since the data partition is not bootable, you don't have to worry about filesystem corruption, as you can easily correct any filesystem problems in Windows by running CHKDSK.

---

### Post by SnuKies on 2016-12-02
I'm coming back with a question: Can I make ubuntu to look like this(debian)  : [https://distrowatch.com/images/cgfjoewdlbc/debian-small.png](https://distrowatch.com/images/cgfjoewdlbc/debian-small.png)

I like the sidebar that way and the top search button

---

### Post by vasa1 on 2016-12-02
> **SnuKies said:**
> I'm coming back with a question: Can I make ubuntu to look like this(debian)  : [https://distrowatch.com/images/cgfjoewdlbc/debian-small.png](https://distrowatch.com/images/cgfjoewdlbc/debian-small.png)

I like the sidebar that way and the top search button
Please start a new thread for your latest question and mark the existing one [SOLVED] if the questions you asked in the first post of the thread have been satisfactorily answered.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

It's preferable to limit a thread to one issue, as far as possible, and to provide an informative thread title so that future users who have similar issues may easily locate the thread.

---

### Post by SnuKies on 2017-11-30
I'm coming back with a question: I bought an SSD (Kingston UV400) and I'm planning to move onto it. Should the partitioning be any different? (I read somewhere that I do not need the SWAP anymore)

---

### Post by leunam12 on 2017-11-30
> I'm coming back with a question: Can I make ubuntu to look like this(debian)  : [https://distrowatch.com/images/cgfjo...bian-small.png]("https://distrowatch.com/images/cgfjoewdlbc/debian-small.png")

I like the sidebar that way and the top search buttonThat is the Gnome shell, I think Ubuntu 17.10 comes like that by default and future versions of Ubuntu will have Gnome3 instead of Unity. I imagine you can just install it and log out and log in in Gnome instead of Unity.

---

