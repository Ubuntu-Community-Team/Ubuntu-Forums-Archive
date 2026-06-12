---
title: "Root partition space issue"
date: 2015-05-26
forum: General Help
---

### Post by kuckunniwi on 2015-05-26
Hi,

I'm asking for help/advice here for a strange issue with my Xubuntu 14.04. First, here goes a bit of context: The system has a 10 Gb root partition and a 70 Gb /home. A fresh install of Xubuntu 14.04 LTS was made less year ago (prefer sticking to LTS). The system is used for bare essentials, so it doesn't have much software that didn't already come bundled with the OS. The only additions are VLC, Skype & Dropbox. Literally, that's it.

A couple of days ago I got an error message saying my the system couldn't install update packages because it was out of space. I move several music and movie folders to an external HD and tried again, then realized that it was my root partition that was out of space. Out of a 10 Gb HD, it had 500 Mb free. All user files, including Dropbox folder, are in a separate /home partition. 

I ran *sudo apt-get autoclean* and *apt-get autoremove*, which managed to clean about 100 Mb of space, then installed Bleachbit, which was able to remove another 400 Mb. With almost a GB of space now, and wondering why my disk was so full, I decided to install filelight to figure out where my root disk space had gone. Filelight apparently requires kde dependencies to install, so setup failed, as it ran out of space. I tried to remove it but I get an error messed up dpkg and am told to run apt-get install -f. I've tried that, which attempts to fix unmet dependencies by downloading the 39MB package it's missing, but it fails due to lack of disk space.

What I don't understand is that, since then, I've cleared Firefox caché, history and temps files, run Bleachbit again with deep scanning options on and freed an extra 150 Mb of space (this is reflected in Gparted), yet despite having over 600Mb of free space on root partition, system won't let me install the 39 Mb of dependencies that it's demanding in order to perform any operation whatsover using apt. So, in short...I can't update, can't autoremove, autoclean, install or remove anything until I sort this out. And then, I'm back to my original problem: freeing disk space on root. How can Xubuntu's root have used up 10 Gb in about....8 months, with no big apps installed?

Any help would be greatly appreciated!

---

### Post by oldfred on 2015-05-26
Did you use sudo to copy something and it really copied into / (root)?
I have run my rsync backup without mounting /mnt/backup and it just copied into / and almost filled my /. But I had lots of room.
Did you empty trash & root's trash?
Housecleaned old kernels?
       df -Th | sort
Inodes:
 df -i
cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null
to also see hidden in /root folder
sudo du -sh /root/.[A-z]* /root/*
#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

    
Some general info:
 Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

---

### Post by kuckunniwi on 2015-05-26
Wow, that was fast! Thanks.

Actually, it's my sexagenarian mother's computer, who is unaware of what sudo means or that there's such a thing as root, so I doubt it. I'll check out your suggestions ASAP, do you reckon have any trouble running nay of these commands via Teamviewer...?

---

### Post by kuckunniwi on 2015-05-26
Wow, that was fast! Thanks.

Actually, it's my sexagenarian mother's computer, who is unaware of what sudo means or that there's such a thing as root, so I doubt it. I'll check out your suggestions ASAP, do you reckon have any trouble running nay of these commands via Teamviewer...?

---

### Post by oldfred on 2015-05-26
Hey, we are not supposed to talk about sex on this site, much less something like sexagenarian. :)

Of course I am one, but only for another year.

---

### Post by kuckunniwi on 2015-05-27
Only for another year? That particular number is far more suggestive than my choice of words ever was! If you'd like, we can round up your age, call you a septuagenarian and wipe our slates cllean from so much conceptual filth!

I haven't had a chance to check out your suggestions (BTW, thanks for taking the time to post so much info!), with the whole remote assistance and what not, but I was wondering, for when I do (hopefully later today), what can I do about apt's catch 22? Is there any way of resolving the dependency issue without installing it? I tried removing the dependencies it calls for (kde-runtime, e.g.), but it won't let me. Do you think any of [this]("http://askubuntu.com/questions/263378/how-to-fix-dependencies-broken-packages") will help?

Thanks and have a great day!

---

### Post by oldfred on 2015-05-27
Are you also having dependency issues, or just space issues?
You need the space first, then make sure sources has no errors, and then run the suggested commands in your link to make sure everything is sync'd.

---

### Post by kuckunniwi on 2015-05-27
I was able to free up almost 3Gb getting rid of old linux images and deleting root's trash. It's odd, because when I tried to remove the packages with broken dependencies via the terminal (sudo apt-get remove filelight kde-runtime), it wouldn't let me, but when I marked a bunch of old linux-images for removal, it automatically prompted the broken packages I'd been trying to get rid of, and removed them with no further issues).

I'll keep digging and look into the other options you posted, plus there are still several old images that can be deleted, but for now, things are working fine, root has 3.5 Gb of space and no more broken packages so I'll mark this issue as solved. 

I was wondering, though, and I don't mean to take up too much of your time, if you could take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2269978"), which has been lost in space & time for quite a while now, and shed some light on the issue, or at least point me in the right direction and I'll do my research and see if I can solve as self-sufficiently as possible. It's an issue concerning my work laptop that would save me a lot of headaches.

Once again, thanks a ton for all your help!

---

### Post by oldfred on 2015-05-28
Glad you got it resolved.

Do not know much about LibreOffice or languages. But in Firefox it regularly resets me to something other than US English and spelling then is off.

---

