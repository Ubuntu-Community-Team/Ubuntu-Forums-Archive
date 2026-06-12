---
title: "Switch over to ubuntu 64 bit version"
date: 2017-10-19
forum: General Help
---

### Post by AnupamMitra on 2017-10-19
Right now I use Ubuntu 16.04 32-Bit version on my Desktop Computer (64 bit Gigabyte M/B with 1 TB RAM). 

Would it be possible to switch over to 64 Bit version of Ubuntu 16.04 or the next LTS version, i.e. 18.04 directly or I have to install 64 Bit version afresh? 

Need guidance from experts.

---

### Post by vasa1 on 2017-10-19
I remember someone managing to switch from 32-bit to 64-bit but I didn't save the link :(

In any case, my preference is for a clean install.

Here's something from 2011: [https://askubuntu.com/questions/81824/how-can-i-switch-a-32-bit-installation-to-a-64-bit-one](https://askubuntu.com/questions/81824/how-can-i-switch-a-32-bit-installation-to-a-64-bit-one)

---

### Post by oldfred on 2017-10-19
How much RAM? :)

Pretty much the rule has been use 64 bit if you have 2GB or more of RAM. If less RAM then 32 bit may be a bit better.

I have an old mostly retired now laptop with 1.5GB of RAM and did install the 64 bit version. But if more than one larger app, it would use swap and turn gray for a couple of seconds while swapping. So I learned not to open many apps.

---

### Post by AnupamMitra on 2017-10-24
@ oldfred 
Thanks for your cooperation. However, I mentioned in my Thread that my RAM is 8 GB.

---

### Post by deadflowr on 2017-10-24
> **AnupamMitra said:**
> @ oldfred 
Thanks for your cooperation. However, I mentioned in my Thread that my RAM is 8 GB.

No, you mentioned you have 1 TB of RAM
> Right now I use Ubuntu 16.04 32-Bit version on my Desktop Computer (64 bit Gigabyte M/B with 1 TB RAM). 
If you meant some other thread then that would be something missed or omitted.

To the point, the askubuntu link vasa1 posted is probably the closest you can come to a how to convert a running system.
But I would simple suggest going the easier route and backup your personal stuff and reinstall a fresh clean version.

---

### Post by oldfred on 2017-10-24
Back in 2009 when I converted from 32 bit to 64 bit, I did not know there was an easy way to backup & restore all the apps. I had added a lot.
I did install in a new partition, so ended up going back & forth to find all the apps I had installed. You can just use dpkg to export list of apps and reinstall from that. Most of your data is in /home unless you have a server type configuration with database, web or other apps in / which then also need to be backed up. Some also manually edit system configuration files in /etc and may want to back those up also. I edit so few,  I just copy those into /home to save them.

You should have your normal backup so when (not if) hard drive fails, you have all your data. So just update backup to make sure current.
If newer system with larger hard drive, you can just create a new / (root) partition of 25GB and do a new install into that. Then once configured you can move to a new /home partition if not already separate or a /mnt/data partition for all your data.

 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by AnupamMitra on 2017-10-25
@deadflowr
Yes, you are correct, It was my mistake. I regret.
It should be like this - Hard Disk 1 TB, RAM 8 GB.

---

### Post by oldfred on 2017-10-25
That was why I had a :) after my question on how much RAM. It seemed a bit large. And was perhaps your HDD size.

---

