---
title: "Using home on two different versions?"
date: 2017-04-16
forum: General Help
---

### Post by garyed on 2017-04-16
I want to set up another partition & install another version of Ubuntu. I already have a home partition on my current version of Ubuntu. Can I leave it as is & use the same partition between both versions? If so what is the recommended way to install the new version so I can. I already have a clean 30 gig ext4 parttion set up for the installation.

---

### Post by oldfred on 2017-04-16
I am one that says not to share /home.
But then use a shared data partition at /mnt/data and link all your normal /home folders into each install.
Your data can easily be shared, but settings may conflict if in one /home.

Many that say you can use same /home really mean two different users in the /home partition. Then settings & data are still separate.
Some do say they have used /home and different versions must not have had any settings that overlap or user did not notice.

I keep /home inside my / (root) in a 25GB / partition. And I also move some of the larger hidden data folders normally in /home like Firefox & Thunderbird profiles and use profile.ini to link them  to each install.

       The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by garyed on 2017-04-16
Neat idea, Since my existing home partition is about 500 gig what about just sharing the home partition. I'm thinking of creating a new folder in my existing home partition called Ubuntu-1610. Then when I install 16.10 use that folder for my home in 16.10. I'm having some problems with a few programs in my existing distro so I'm wanting to gradually delete & clean things up on my existing home partition & gradually build up my new install. Then I want to remove the old distro completely & start with a fresh install of another distro. Do you think that would work?

---

### Post by oldfred on 2017-04-16
If just upgrading to a new version, you can usually use same /home.
It just that some changes to a new version may then now work in old version. 
For example I use keepassX. When I converted from 14.04 to 16.04, I had to upgrade database for passwords. Old version does not know about new version.
Some software may just have a setting or two that are new or other minor changes.

If issues with current system are you sure it is not related to user settings that are in /home. Or new install using same /home has same issues?

Even back in my XP days, I preferred to separate system from data. 

You also can test if your backup procedures are valid, by using backup in new install.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by garyed on 2017-04-16
I've actually have quite a bit of problems with my existing 16.04 ever since i upgraded from 14.04 so I really want to do a clean install instead of upgrading. I've been using Ubuntu since version 6.10 & always did a clean install when i upgraded & never had a problem. This is the first time i used the upgrade feature & have had errors & problems with programs I never had before so I want to do another clean install & eventually get rid of my existing install. Whether my problems are distro related, dependency related, compatibility related or whatever I just want to start fresh but not lose my data. I figured i could gradually install what i need & then move my data one program at a time.

---

### Post by oldfred on 2017-04-16
I started with 6.06 and upgraded thru 9.04. Then conversion to 64 bit required new install and that worked so well that I never do upgrades, anymore.

But I typically use current LTS as main working install and have several other test installs and want same data in all of them. So I use the shared data partition.
It also makes it easier to to main system upgrade. I still have my working? (but now not booted for months) 14.04. When I install new version, I can still boot older version to find anything I missed in backups & update backup procedure to be sure to include everything. I also have script(s) to do a lot of update & configuration and I like to test them with every install.

---

### Post by ajgreeny on 2017-04-16
I concur fully with oldfred on this; a shared data partition using symbolic links to the  folders in that data partition is the safest way to go, and is what I now have just started to do on my second machine and will move to when I update my current 16.04 to 18.04.

However, prior to my recent change to a data partition, I had always used a separate /home partition, and left it untouched from one Ubuntu version to the next Ubuntu version.

Only once did I have a problem, and I can not now remember what application it was that caused the difficulty, (perhaps scribus or inkscape?) but after opening an existing file with the application I was warned that it was created by an earlier version of the application and if I now saved it I would be unable to open it again with the previous application version.

At that time I still had the previous OS version on disk, as I still do now with 16.04 as my main OS, and also 14.04 on disk but unused for several weeks; it was retained as a fallback in case of problems with 16.04, but there really were none that could not be quickly sorted out.

---

### Post by SeijiSensei on 2017-04-17
I've shared /home with Fedora and Ubuntu distros, and with Kubuntu and Ubuntu as well.  Applications these days are pretty careful about keeping to themselves (e.g, ~/.gnome and ~/.kde), and many of them have begun using ~/.config for all settings regardless of desktop environment.

---

