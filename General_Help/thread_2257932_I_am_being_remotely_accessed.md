---
title: "I am being remotely accessed"
date: 2014-12-23
forum: General Help
---

### Post by duckie682 on 2014-12-23
Hello all, I am new to the community and I am posting here because I have a serious problem going on. I am being remotely accessed by hackers as they have taken down several windows machines by barrelling through my gateway (wired) no wireless and installing linux write protected volumes. This has forced me to boot into Unbuntu and learning more than I ever wanted to. 

Here is what I now know:


1. There are at least 50 remote keys on my machines (names and emails associated that I won't post here)
2. I have created an admin account and password.
3. Logged in as root via terminal using sudo -i. Left terminal running.
4. They are using IPV6 to attack me. 
5. I have not installed Unbuntu, I am merely booted into it. Hard drive is removed from machines. Remote keys still appear when searching for remote keys. 

I am trying to delete the file that governs IPV6 access in etc/config/syst...something..I forget now but you all probably know what I am referring to. When trying to do so the system still says I am not the owner and that I do not have permissions to delete that file. 

My questions are. 

1. How do I delete that file?
2. What is the best way to lock down my freaking machine from these people that keep attacking my machine?

---

### Post by kpatz on 2014-12-23
I'm a bit confused.  You say hackers are taking down Windows machines, then you talk about them installing Linux volumes and booting Ubuntu...?

What are you using for a gateway?  A properly setup firewall (or even a NAT router) should keep them out.

How many Windows machines?  How many Linux (or Ubuntu) machines?  Which ones have been compromised?  How's your network set up?

How do you know you're being hacked remotely?  What's the evidence that clued you into this?

The first thing to do is disconnect from the internet completely (at the gateway) until you determine what's going on.

---

### Post by buzzingrobot on 2014-12-23
How are they installing anything, much less another OS, on machines with no hard drives?  For that matter, how are you running Windows on them?

---

### Post by duckie682 on 2014-12-23
No...they have installed write protected linux volumes or devices on a windows machine..FAT32 on NTFS...

I found this because I booted into Unbuntu on the windows machine and it showed me the fat32 partitions that are on my NTFS hard drive..see what I am saying?

I guess you can forget about that though, the bigger question is how do I delete that file that governs the IPV6 settings? Any help is appreciated.

buzzing...they aren't installing anything without the hardrive...they installed with the harddrive in...so because of that, I take out the hard drive and boot into unbuntu because the windows hard drive has FAT 32 partitions on them. And this happens a couple hours after I take the machine out of the box brand new!!!!!!

One of the remote keys loaded into my machine has the name Purehate@......... associated to it...WOW!!!!!

---

### Post by yancek on 2014-12-23
> I found this because I booted into Unbuntu on the windows machine and it  showed me the fat32 partitions that are on my NTFS hard drive..see what  I am saying?


fat32 and ntfs are windows filesystems and if you have newer computers with UEFI/GPT then you will have a fat32 partition on which the necessary EFI files are store.  I don't see how deleting a file on an Ubuntu Live CD/flash drive (whatever you are using) is going to have any effect on your windows system.  In fact, a Live CD is a read-only system and you won't be able to delete anything on it.  Sorry, but I can't make sense of what you are posting.

---

### Post by kpatz on 2014-12-23
Most newer pre-installed Windows machines have a recovery partition on them which may be FAT32.  That is probably what you're seeing when you view partitions from the Ubuntu live CD.  A hacker can't re-partition a hard drive while Windows is running, never mind install another operating system.

When you say there's remote keys being added, how and where are you finding them?  In what file/directory?

What are you using for a gateway to the Internet?  Have you disconnected the affected machine(s)?

---

### Post by duckie682 on 2014-12-23
kaptz....go to Passwords and keys...open it...then go to remote in the menu bar...then search for remote...tell me what you see? I have a bunch of remote keys..Do you have amything that says Purehate???????

---

### Post by QIII on 2014-12-23
@duckie682:I have edited two of your posts for language now.Your problems notwithstanding, if you cannot mind your behavior I will close this thread. Thank you.

---

### Post by duckie682 on 2014-12-23
Yancek...that's what I was wondering...since it's a live CD I guess I can't delete anything when I boot into Unbuntu but do not have it installed. I guess I will install it and delete what I want then boot into it....thanks so much!

---

### Post by kpatz on 2014-12-23
> **duckie682 said:**
> kaptz....go to Passwords and keys...open it...then go to remote in the menu bar...then search for remote...tell me what you see? I have a bunch of remote keys..Do you have amything that says Purehate???????

Is this what you see?
[ATTACH=CONFIG]258756[/ATTACH]

I got that by opening Seahorse (Passwords and Keys) and searching for remote keys with "purehate".  They're just public PGP keys used by people to sign or encrypt files.  Some of them happened to use "purehate" as their email address.  I did this in a VM booting a live Ubuntu CD.

They don't mean you've been hacked.  They exist on a public key server somewhere, and you actively queried that server and got those results.

What was the first indication that makes you think you are being hacked?  Something must have happened to start you on this chase.  The clue may lie there.

---

### Post by grahammechanical on 2014-12-23
Pure_Hate is a user name of a developer of Linux BackTrack.

[http://www.backtrack-linux.org/about/](http://www.backtrack-linux.org/about/)

Are you really running a Ubuntu live session or is it actually BackTrack that you are using.

Regards.

---

