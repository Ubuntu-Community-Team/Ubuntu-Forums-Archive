---
title: "Advice sought re merging two versions of Ubuntu"
date: 2017-11-24
forum: General Help
---

### Post by nickdc on 2017-11-24
On my rather ancient desktop I'm currently running three OS: an old WinXP, Ubuntu 12.04LTS and Ubuntu 16.04LTS. I've only recently installed U 16.04 and it's so much of an improvement even on my old pc, that I want to migrate to it entirely and ditch 12.04. I'm posting to ask advice about the best and safest way to do this, given the way in which the different OS are currently set up on my main drive.

I've attached a screenshot from Gparted of the partitions on that drive:

sda1 is of course the WinXP partition which I want to keep for the moment as is;.
sda6 (UB_OS - the next one to the right in the schematic) has just the OS for Ubuntu 12.04;
sda5 (UB_Home - largest partition on the right) has the Home directory for 12.04;
sda8 (highlighted) has both the OS and Home directory of the newer 16.04 installation.

What I'm proposing to do is as follows, and I'd be most grateful for comments from experienced users along the lines of "yes, that should be fine" or "no, you'll run into trouble at step x" or "you will have to do that using a live cd" or "a better way would be to ...." or any other helpful advice.

I propose:

1. Clear out any redundant clutter from the 12.04 home folder (sda5);
2. Back up that home folder externally;
3. Double-check that it is properly backed up!
4. Delete sda6 and sda5 using Gparted;
5. Expand sda8 to fill the unallocated space left by sda5 & 6;
6. Restore the contents of the 12.04 Home folder to the existing Home folder on sda8.

That will of course leave me with my 16.04 home folder still on the same partition as the OS, but I understand there are advantages and disadvantages in this. Also, I believe there are good guides available on to how to move the Home folder to a separate partition, should I decide to do that later.

All comments greatly appreciated, especially caveats and things to watch out for.

---

### Post by mc4man on 2017-11-24
What are you hoping to gain from using your 12.04 home folder in a 16.04 install?
(- vs. just coping any user files of value, i.e. documents, photos, music, vids, ect. & doing a fresh 16.04 however you wish to partition

---

### Post by nickdc on 2017-11-24
Thanks for such a quick response.

I'm not hoping to gain anything - all I will be doing is copying valued files across, as you say. But because the 12.04 home folder is so large, and on a separate partition, I have to wipe both it and the 12.04 OS partition, and then expand the 16.04 partition, all *before *I can copy the valued files etc back to the newer 16.04. Maybe it's all very straightforward, but I'm a bit nervous of doing it, hence the post.

---

### Post by ian-weisser on 2017-11-24
You are right to be nervous. You correctly assess the risk of data loss.

I think your proposed plan makes sense. Budget enough time for hiccups, and do it.

---

### Post by nickdc on 2017-11-24
Thanks, Ian, for your reassuring response. Much appreciated.

---

### Post by oldfred on 2017-11-24
Back up always good.

But why not mount /home in 16.04? If already a separate partition.

You have done part of this, but may want or need to copy current 16.04 /home data & settings into /home partition.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Tadaen_Sylvermane on 2017-11-24
Wasn't sure if you were planning on keeping XP on there, big safety risk to use it. That being said if you want to migrate entirely to Ubuntu and clean it up, I'd backup everything. Repartition with a root, data, and swap and reinstall to the root partition. put your data in the data partition and symlink it into your /home/$USER. This allows you to keep data fairly safe while being able to reinstall at your leisure in the future. Been doing it awhile myself and makes my life easy as I love trying new distros / reinstalling out of boredom sometimes.

---

### Post by nickdc on 2017-11-25
> **oldfred said:**
> Back up always good.

But why not mount /home in 16.04? If already a separate partition.

You have done part of this, but may want or need to copy current 16.04 /home data & settings into /home partition.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Thanks, oldfred. I had wondered about doing this, but I'm unsure about "settings". In past reading up about "what to back up from your home folder" I've come across conflicting advice about settings. And especially as 12.04 is a straight Ubuntu incarnation but with "Classic Gnome" desktop, and 16.04 is Ubuntu-Gnome, I'm very wary of risking settings being conflicted between the two by copying either into the other. I felt it was safer to stay with the settings now established in 16.04 (which are generally working well for me) and just bring back the data I want from 12.04. I hope that makes sense.

---

### Post by nickdc on 2017-11-25
> **Tadaen_Sylvermane said:**
> Wasn't sure if you were planning on keeping XP on there, big safety risk to use it. That being said if you want to migrate entirely to Ubuntu and clean it up, I'd backup everything. Repartition with a root, data, and swap and reinstall to the root partition. put your data in the data partition and symlink it into your /home/$USER. This allows you to keep data fairly safe while being able to reinstall at your leisure in the future. Been doing it awhile myself and makes my life easy as I love trying new distros / reinstalling out of boredom sometimes.

Thanks, Tadaen. Yes, I am planning to keep XP for the moment - very rarely use it, but when I do it's essential. I really like your suggestion of just keeping the data on a separate partition. What I didn't mention in my post is that I'm hoping fairly soon - some time in the new year - to upgrade to a spanking new pc; the current move is to keep me afloat until I can do that. When I get the new machine I think I'd like to try your set up. Can you expand a bit on "and symlink it into your /home/$USER" or point me to a link on this process. I more or less understand what symlinks are, but it's not familiar territory for me.

---

### Post by Tadaen_Sylvermane on 2017-11-25
Just links to another location. I have my bin, Documents, Pictures, Music, Videos that are normally in my /home/$USER on my /data/$USER location. I link them into my /home/$USER in place of the defaults there on a fresh installation. 

The whole idea of this is to keep the data separate while keeping /home in the / partition. Reasoning is that sometimes settings in config files aren't entirely compatible with another DE, or even change from release to release. Can get a clean fresh /home/$USER/ by doing this for each install. I don't like a dedicated /home for that reason, settings get carried over and can cause problems.

---

### Post by oldfred on 2017-11-25
I actually use /mnt/data the same as Tadaen_Sylvermane. 
Primarily since I like to have multiple installs but do not want settings from /home in all of them. I may be experimenting with changes or something and do not want conflicts.

Ubuntu in 16.04 is Unity, but that is now being retired (maybe still available from others) and they are going back to gnome.
I have 18.04 installed to see how it works, it mostly is still 17.10. But have installed gnome-panel/fallback/flashback in it also, as I prefer the old menus and top & bottom panels.

 The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by nickdc on 2017-11-25
Very helpful and informative, oldfred, thanks very much for sharing.

---

### Post by Tadaen_Sylvermane on 2017-11-25
Other way around oldfred. One of your posts long time ago got me to using a separate /data partition :)

---

