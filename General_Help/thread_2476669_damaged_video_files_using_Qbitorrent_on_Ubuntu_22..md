---
title: "damaged video files using Qbitorrent on Ubuntu 22.04"
date: 2022-07-02
forum: General Help
---

### Post by marklyn on 2022-07-02
I've got a Windows share that I use Qbitorrent on Unbuntu to download to but any files that are downloaded to that share are "damaged" in that they won't open (text files are blank; video files report damaged).  Oddly though, if I change the file location to download to the /home/xxxxx/downloads folder, then copy them to my Windows share, they are fine.
I've tried another share location, problem still exists.  The file downloads, the size is what is expected but the file is somehow damaged.  Text files open empty, video files reported as damaged by the player.
My Windows share was set up via Nautilus as a SMB share if that helps.
I'm at a loss to understand why downloading to my /downloads folder works changing the download to my Windows shares breaks files.
My Ubuntu ver is 22.04 and Qbitorrent is 4.4.3.1

---

### Post by TheFu on 2022-07-02
A web search for "Qbitorrent cifs problems" found a number of issues, including a bug in qbitorrent which has a few option changes: [https://github.com/qbittorrent/qBittorrent/issues/16525](https://github.com/qbittorrent/qBittorrent/issues/16525) suggested for specific versions of the tool.

Below is added for consideration, not directly related to "make Qbit.... work using CIFS". Ignore if you like.

I can only recommend trying a different network file sharing protocol, perhaps nfs, though it appears that NFS might have an issue as well.  

I've used NFS with Windows as a server in an enterprise with about 600 client systems, but that was very, very, long ago, a huge hassle, and we paid for a commercial NFS implementation. Eventually, we replaced a number of expensive Windows Servers (necessary for performance) for 1 Unix workstation (50% less cost) running as an NFS server to fix all the issues, plus the Unix workstation integrated into the x.500 directory server, so daily, manual, uid/gid maintenance wasn't necessary. 

When I was a cross-platform developer, we'd code the desktop GUI on Windows first, but all the server stuff was mainly built on Solaris.  Sure, we listed AIX, HP-UX, OSF/1, DigitalUnix, Irix, and a few others as supported platforms, but I can promise you that all our heavy, expensive, tools to make better code ran on Solaris and nowhere else.  Our QA teams tested all the platforms with automatic test tools exactly the same, but when they were following a gut feel for a bug and searching for ways to break the code, they always used the main platform. Always.  That's because getting a developer to dig into a platform they don't prefer is much harder than one that they work on daily and actually love.

This taught me a huge lesson. Use the native OS versions of everything whenever possible, regardless of claims by the vendor that X on A is identical to X on B.  Those are lies.  Use the platform that the developer primarily develop on. That's the rule.  The compiled code is always different on every platform. No way around that.

---

### Post by Morbius1 on 2022-07-02
> My Windows share was set up via Nautilus as a SMB share if that helps.
I'm at a loss to understand why downloading to my /downloads folder works changing the download to my Windows shares breaks files.

Does the same thing happen when you change the download location to the CIFS mount instead of the Nautilus ( gvfs / smb ) mount:
[ATTACH=CONFIG]290686[/ATTACH]

---

### Post by marklyn on 2022-07-02
Thanks for the info. I'm beginning to believe it is something with qbitorrent vs windows shares (cifs).
Makes me think that even more since I can download anything to a local ubuntu directory, copy it over to the same window share, and it works/views fine.
I'll look into the search recommendation, thanks.

---

### Post by marklyn on 2022-07-02
Morbius, I will have to try that later, leaving for a bit, but that was a good thought.

---

### Post by Morbius1 on 2022-07-02
Just to clear one thing up.

When you access then mount something in Nautilus you are using samba ( actually gvfs > samba client library ).

When you mount something with CIFS you are using the Linux kernel itself.

mount.cifs knows nothing about any samba client modules. These are two different processes.

What may be a problem with a gvfs / smb mount may not be a problem with a CIFS mount.

---

### Post by marklyn on 2022-07-02
> **Morbius1 said:**
> Just to clear one thing up.

When you access then mount something in Nautilus you are using samba ( actually gvfs > samba client library ).

When you mount something with CIFS you are using the Linux kernel itself.

mount.cifs knows nothing about any samba client modules. These are two different processes.

What may be a problem with a gvfs / smb mount may not be a problem with a CIFS mount.
It sounds like there are two ways to mount something.  I need to research how to mount via CIFS I guess, because I've tried multiple ways to mount using Nautilus.

---

### Post by marklyn on 2022-07-02
> **marklyn said:**
> It sounds like there are two ways to mount something.  I need to research how to mount via CIFS I guess, because I've tried multiple ways to mount using Nautilus.
I did a temp connection through CIFS:  (sudo mount -t cifs -o username=user_name //192.168.0.1/d /mnt/waterlooD)
I was prompted for my Windows share pw.
I could see my window shares and manipulate files via Nautilus; however, when I set my file location in Qbittorrent to /run/user/1000/gvfs/smb-share:server=waterloo,share=d/uTorrent Downloads, 
The files download file, file size is as expected but the files are still 'damaged' and won't play.
I changed the file location to /mnt/waterlooD and they wouldn't even download at that point.

This is driving me nuts.  I really like Ubuntu and want to embrace using it and working with it, but it seems like it should just be easier using it to connect to a Windows share.  I've spent 2 days solid working on this and still nothing.
Think I better call it a night, I'm getting cranky. :)

---

### Post by Morbius1 on 2022-07-03
More and more I think the Qbitorrent program is not a deb but a snap. A snap-based application restricts what it can access.

Not an expert on snap but I believe if you run this command it will tell what applications you are using are snaps:
```
snap list
```

---

### Post by marklyn on 2022-07-03
It's not listed...

marklyn@marklyn-virtual-machine:~$ snap list
Name                       Version           Rev    Tracking         Publisher   Notes
bare                       1.0               5      latest/stable    canonical&#10003;  base
core20                     20220527          1518   latest/stable    canonical&#10003;  base
firefox                    102.0-2           1498   latest/stable/&#8230;  mozilla&#10003;    -
gnome-3-38-2004            0+git.891e5bc     112    latest/stable/&#8230;  canonical&#10003;  -
gtk-common-themes          0.1-81-g442e511   1535   latest/stable/&#8230;  canonical&#10003;  -
snap-store                 41.3-60-gfe4703a  582    latest/stable/&#8230;  canonical&#10003;  -
snapd                      2.56              16010  latest/stable    canonical&#10003;  snapd
snapd-desktop-integration  0.1               14     latest/stable/&#8230;  canonical&#10003;  -
marklyn@marklyn-virtual-machine:~$

---

### Post by Morbius1 on 2022-07-03
So I installed this crazy thing and did a test.

I'm running Ubuntu 22.04 in a VirtualBox guest.

I added a mount declaration in fstab to mount an smb share on my network:
```
//srv1.local/Public /mnt/WinShare cifs guest,uid=tester 0 0
```

I set the download path in QBittorent to that mount point.

I rebooted the Ubuntu VirtualBox guest. - The CIFS mounted automatically.

Decided to download Ubuntu Server 22.04 via a torrent:
[ATTACH=CONFIG]290687[/ATTACH]
Everything seems to be working so far:
[ATTACH=CONFIG]290688[/ATTACH]
And here is the finished file:
[ATTACH=CONFIG]290689[/ATTACH]

I'm going to stop tormenting you about this since I clearly cannot reproduce your error and my Qbitorrent and VMWare experience is zip.

---

### Post by marklyn on 2022-07-03
Morbius1, you aren't tormenting me, I am doing a good job of that myself by the amount of research I'm doing with what appears to be promising leads but end up not working :)
However, can you do me a favor with your suggestion?
Please download 1-2 video files and see if you can play them on your Windows share.
Thanks

---

### Post by marklyn on 2022-07-03
I should also mention that all of the files I downloaded had the expected file sizes, so at first glance they looked good, until I tried to open or play them.
Text files opened blank, video files wouldn't play, whatever player I was using would either give me an error or never loaded the file.
That being said, I may have found a solution in VMWare, I'm going to test it a few times before I post here.
I will also fire up virtualbox, where I have a clean Ubuntu install, and look at your method to try.
Thank you!

---

### Post by marklyn on 2022-07-03
I'm happy to report that a solution has been found, actually excited.  It's amazing how many different, yet similar "solutions" are out there for accomplishing the same thing!
My solution involved going back to the original idea of using VMWare's shared drive mappings, native to VMWare when building a VM.
I turned on drive mappings for two window share drives, D: and E:
then I eventually found this info on the web:
sudo mkdir /mnt/hgfs
edit fstab and add:
vmhgfs-fuse    /mnt/hgfs    fuse    defaults,allow_other    0    0
sudo mount -a  (remount)  & then restart the machine; should see D & E under /mnt/hgfs

Using the mount points in my Qbitorrent program didn't cause my files to be damaged!  That was the goal here.

This worked, so I logged out and back in to see if it still worked, it did.  Then I did a shut down/restart, logged in, and it still worked so it appears to be 'survivable' for restarts.
I learned a lot during this process and appreciate various people sticking by me (Morbius1 and TheFu, and others).  I'll post this in the networking thread as well so that thread can show 'solved'

Morbius1, I'll try the suggestion you had above with a virtualbox vm.  It'd be good to know how to do this in both environments.

---

### Post by Morbius1 on 2022-07-03
> **marklyn said:**
> Morbius1, you aren't tormenting me, I am doing a good job of that myself by the amount of research I'm doing with what appears to be promising leads but end up not working :)
However, can you do me a favor with your suggestion?
Please download 1-2 video files and see if you can play them on your Windows share.
Thanks

Too late. I already removed Qbittorrent from the client. The mounted iso file transfered to the server seems to have all the component parts in it and the hash is correct:
[ATTACH=CONFIG]290690[/ATTACH]
So I think it all checks out/

Anyway, I think you have a better solution. A VMWare or VBox shared folder has to be far more efficient than any type of network transfer.

---

### Post by TheFu on 2022-07-03
> **marklyn said:**
> It sounds like there are two ways to mount something.  I need to research how to mount via CIFS I guess, because I've tried multiple ways to mount using Nautilus.

There are many ways to mount things, not just 2.  

Almost any GUI tool attempting to connect to Windows shares will use the same method that Nautilus uses, so when that isn't working well and many users will only attempt the GUI way, they run into issues.  Plus, MSFT changing defaults and versions a bunch over the last few years has made it difficult for anyone else to keep up.  Back when I had an OSX machine, it couldn't mount Windows shares, due to a bug that was fixed about 3 months AFTER I returned it.

With Unix systems, there are many, many, many, choices which can be daunting for end-users who expect 1 solution that is "standard".

When asking questions about Unix solutions, it is usually best to describe the end goal. Much of the time, what you guess was the "best answer" will be, but sometimes the answer will be something you've never heard about before.  For this thread, I'd think that nearly everyone would have said to use a CIFS mount for a few important reasons, like that cifs mounts happen at boot time, which is very important for server processes that run before any user logs in.  It is possible to have any process run before the user logs in. That's very uncommon on Windows, but much more common on Unix.

So, be certain you try the fstab/cifs mount, not just the gvfs/gio mount method.

---

