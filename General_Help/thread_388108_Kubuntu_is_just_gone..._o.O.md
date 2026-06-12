---
title: "Kubuntu is just gone... o.O"
date: 2007-03-19
forum: General Help
---

### Post by kiratsuki on 2007-03-19
It's actually kind of funny really.. Instead of manually restarting I simply turned the power off... Ummm, after rebooting into Kubuntu, I got an error message saying that there was something wrong, and that I should "Please check installation". After trying to reboot, even in safe mode doesn't work.. I simply get a black screen, which then sends me back to the login screen, or I get to see some REALLY colorful lines fill the screen until I get tired of looking at them and turn the computer off.

Similarly, the ubuntu base upon which kubuntu is installed doesn't load... That is, none of the icons appear on the window that pops up in the center during the startup process... It just sits there and does nothing, hmmm..

I am using 6.10, edgy eft I think. Anyway, I was kind of having some problems minor problems with the install, like trying several times to install kaffiene which simply refuses to start... And then for some reason, the apt package manager simply stopped working... After telling it to download packages, it would just close. I'm not really good at computers, and I don't really use it for much except e-mail and online stuff and such. I don't mess with the settings at all, so it's very hard to understand how so many things could go wrong, I also don't visit anywhere that I might download viruses, hmmm.. I tried to reinstall, but it does not detect any previous hd partitions, and prompted me to simply delete everything and start all over again...:(:confused:  What did I do to deserve this? This is soooooo not fair... :mad: This software has shown itself to be extremely unreliable in so many ways...

I was thinking it might be the mbr? Hmm.....

And ubuntu is even worse, because I accidently deleted the menu bar, and  how I don't know to set it up the way it was when it was first installed, so I just use a terminal to load everything. ##

---

### Post by zvacet on 2007-03-19
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by kiratsuki on 2007-03-20
I  don't think this link has the information I am in need of. Unfortunately, I don't get any command prompt whatsoever. When I boot the computer, since I have both ubuntu and kubuntu installed, it gives me a promp to chose either of those, and to enter my username and password. After doing so and hitting enter, I simply get a blank screen which last for about 15 seconds, then I appear back on the same log in screen as if I didn't push anything. Twice, this was different, and it gave me a popup that looked sort of like a macintosh promp prior to OSX. That promp says something like, "There is a problem with ksmserver, please check the installation." I don't know what this means at all, perhaps it might have something to do with why my computer won't boot at all?

Maybe there is some command that I can restore my original configuration? I am running the live cd now, which does not let me access me files, but I am not sure how it works, so maybe there is a way to do so? Please please help.

---

### Post by kiratsuki on 2007-03-20
Also, now I try to start the installer from the live cd, and it always crashes every single time... Likewise, trying to install from konsole gives me "debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process".... I cannot access my desktop files at all because of this, it is like the whole installation just broke for no apparent reason, and it refuses any reasonable attempt by me to try to repair it...

---

### Post by anaconda on 2007-03-20
> **kiratsuki said:**
> Maybe there is some command that I can restore my original configuration? I am running the live cd now, which does not let me access me files, but I am not sure how it works, so maybe there is a way to do so? Please please help.

check and repair errors from the hd. From the liveCd terminal:
fsck -f /dev/hda1

just check that the partition is right.. I "assume" your linux is on hda1.

I have successfully repaired my installation with that command..

---

### Post by kiratsuki on 2007-03-23
ubuntu@ubuntu:~$ fsck -f /dev/hda1
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
fsck.ext2: Permission denied while trying to open /dev/hda1
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$ sudo fsck -f /dev/hda1
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/hda1: 174940/7162176 files (1.5% non-contiguous), 2233157/14321939 blocks
ubuntu@ubuntu:~$

There is what I get, it didn't help so much... I still can't boot into my othwer installation... I don't know what this means, should I try something else?

---

