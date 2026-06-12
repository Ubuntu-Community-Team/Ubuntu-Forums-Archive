---
title: "apt-get can't delete dpkg-new files"
date: 2008-03-15
forum: General Help
---

### Post by thobraa on 2008-03-15
This is my first post so if I miss something I hope I won't get scolded for it :)
I have tried searching the forum, but I haven't found anything that resembles the problem. I'm not sure what started it but yesterday I saw that when trying to update via GUI I got error message with broken dependencies. When running sudo apt-get install -f i got a message saying that it couldn't delete some file that was in this folder: /usr/share/locale/ko/LC_MESSAGES/ . I don't have the exact name of which file that was because I tried removing "backports" from sources( i just figured out what file that was, it was called compiz.mo.dpkg-new), which made sudo apt-get install -f run fine, except it uninstalled compiz which I didn't tell it to do then or earlier. Then I started running updates again cause everything looked good, when I got a problem with broken dependencies again. Same type of error except with a different file, but in the same location. Now what I get when running sudo apt-get install -f is the following:
--
ozi@ozirms:~$ sudo apt-get install -f
[sudo] password for ozi:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  vlc-nox
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 13.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 135699 files and directories currently installed.)
Removing vlc-nox ...
dpkg: error processing vlc-nox (--remove):
 failed to delete `/usr/share/locale/ko/LC_MESSAGES/vlc.mo.dpkg-new': Operation not permitted
Errors were encountered while processing:
 vlc-nox
E: Sub-process /usr/bin/dpkg returned an error code (1)
--
So the problem is that it cant delete some file, when i try to go in there and delete it, I'm not allowed either. Not as root, I tried logging in as root just to see if there is any difference, but that doesn't change anything. I find that very strange that I can't delete that file? Now here is what ls -l tells:
 -rwSrwSrwT 1 root root      0 2008-03-14 23:32 vlc.mo.dpkg-new 
Now I'm no expert in this at all, but I think the number 0 is strange here, if that tells about who has ownership of the file??
lsattr tells this about the file:
----------ZX------ ./vlc.mo.dpkg-new
which doesn't tell me much, but as far as I've figured out the ZX attribute is no good.
Any help would be greatly appreciated, thanks in advance.

Thomas

---

### Post by LeoSolaris on 2008-03-15
You may want to try a rootkit checker. There are two in the repos, chkrootkit and rkhunter.

After you download them, make sure to update rkhunter at least, which is done with 
```
sudo rkhunter --update
```

That may actually be a hack called a rootkit, which is sore of like malware and a virus for Linux. I don't actually know too much about them, I have never seen one before. Just be careful where you download things from.

Hopefully that helps.
Leo

---

### Post by thobraa on 2008-03-15
Thanks for the tip, I cannot install anything as long as I have that problem with that (i think there will be more files) file that can't be deleted. If it is a rootkit it was very unelegant to show it's presence by breaking my system :) As I said, thanks for giving thought to my problem, I hope this can be fixed without me having to reinstall. It's not the end of the world if I have to reinstall, it'll just be a drag backing up all those files and I'm looking to avoid that .

T

---

### Post by zvacet on 2008-03-15
```
sudo dpkg --remove --force-remove-reinstreq vlc-nox
```

---

### Post by thobraa on 2008-03-16
Thanks. when I try that I still get the same problem:
ozi@ozirms:~$ sudo dpkg --remove --force-remove-reinstreq vlc-nox
[sudo] password for ozi:
(Reading database ... 135699 files and directories currently installed.)
Removing vlc-nox ...
dpkg: error processing vlc-nox (--remove):
 failed to delete `/usr/share/locale/ko/LC_MESSAGES/vlc.mo.dpkg-new': Operation not permitted
Errors were encountered while processing:
 vlc-nox

Sorry, I don't know how to put it in that "code window" thing, but the response is above. So I still have the same problem, that file can't be deleted. Neither by me or sudo apt-get :(

---

### Post by mixtri on 2008-03-16
Hello Guys. I'm new to Ubuntu. After a day or so I have managed to get my sound working. I'm not sure if this thread is the right one to post in but I seem to have problems with the DPKG.
I get the following message when update manager tries to download and install new updates - 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I started getting this after running the following command  -  

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

these instructions are from the following link - [http://ubuntuforums.org/showthread.php?t=661833&highlight=STREAMING+MUSIC](http://ubuntuforums.org/showthread.php?t=661833&highlight=STREAMING+MUSIC)

The two commands above worked fine as per step 1 in the instructions.
When i tried the next set of instructions in step 2/5  - sudo apt-get remove totem-mozilla mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player

that I got the error message. it now seems to be interfering with system updates.

Please advise what to do alleviate this problem.
I am sure the error message is easy enough, but I have no idea how to  manually run 'dpkg --configure -a'.

Thanks Al

---

### Post by jocko on 2008-03-16
> **mixtri said:**
> I am sure the error message is easy enough, but I have no idea how to  manually run 'dpkg --configure -a'.

Open up a terminal and paste this command into it:
```
sudo dpkg --configure -a
```

---

### Post by thobraa on 2008-03-16
I think maybe you should have a started an own thread for that because it's a different problem, but what you need to try is to open up a terminal window and try
```
dpkg --configure -a
```
you might have to use sudo, I'm not sure. Hope it helps.

---

### Post by mixtri on 2008-03-16
I found a thread dealing with this particular problem and used the following code somebody else used which seems to have solved the problem yet generated another. the code is - sudo dpkg --configure -a

i got the following  after inputting my password -
setting up java-common (0.26ubuntu1) ...

setting up odbcinstdebian1 (2.2.11-16) ...

setting up unixodbc (2.2.11-16) ...

processing triggers for libc6 ...
ldconfig deferred processing now taking place

what does this mean.

Anyway i ran the update manager again and got this - 

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

Thanks

---

### Post by mixtri on 2008-03-16
Thanks Thobraa
Yes, I think I might go back to the other thread. But i wasn't sure what to do as didn't want to post the same message in two places.

---

### Post by mixtri on 2008-03-16
The wonders of technology!!
With regards to my last message. 

I clicked on the close button. This somehow triggered an installation of the updates.

Now the message reads: 
UPDATE IS COMPLETE
S uccessfully applied all changes. you can close the window now.
I am going to reboot my pc now just incase .

---

### Post by thobraa on 2008-03-16
Love it when it works, but it's plain torture sometimes when stuck. I still can't delete those dpkg-new files, not as root, not if i change ownership of the file, nothing. Any ideas anyone?

---

### Post by unutbu on 2008-03-16
A suggestion for the OP. I think your filesystem has become corrupted. The usual way to fix such problems is to use fsck:

Run
```
less /etc/fstab
```
Look through the output for the device name of the linux partition that corresponds to the mount point (probably '/') which contains the
file /usr/share/locale/ko/LC_MESSAGES/vlc.mo.dpkg-new

If you are unsure of the device name, post the output here. If you are sure: 

Boot from the Live CD.
Run 
```
fsck /dev/sdax
```

where you replace /dev/sdax with your device name.

---

### Post by unutbu on 2008-03-16
Make sure /dev/sdax is not mounted when you run fsck.

---

### Post by thobraa on 2008-03-16
I run less /etc/fstab and i get the following

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=08d984eb-005e-4959-b367-01fb2e5b73d6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=32012bad-a721-4b8a-aabf-8f201289d351 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```
So i guess sdb1 is the correct partition to check. I booted up in recovery mode and ran fsck on sdb1 yesterday but it didn't report any error. Think it will be better via a live cd? I have not tried that. Any idea what those files are? From the file location? I guess it would be possible to delete those files via a live cd, but I'm not too sure if that would be a smart move not knowing what those files do.

---

### Post by mixtri on 2008-03-16
Hey Guys!!
Just to say its all good here. Got everything working now! 
It is a long arduous task making the transition from Win XP to Ubuntu, but I seem to be getting there.
Theres still a lot to do, but at least my internet and music all seems to be ok now. 

As always theres a lot more to be done - like getting my favourite streaming sites and file types to work. No doubt; you haven't heard the last of me Yet! ;)

DO I have to do anything else in terms of closing my thread?

---

### Post by unutbu on 2008-03-16
If you already tried fsck from recovery mode, I don't think the result will be different from the Live CD. I'm not an expert at fsck related problems, however, so seeking out the advice of more experienced members may help.

Everything in /usr/share/locale/ko/ is related to Korean language localization. 

I don't think it wouldn't hurt to try to remove the files after booting from the Live CD, but I wouldn't be surprised if it didn't work. Booting from the Live CD can get around permission problems, but I don't think you have a permission problem; I think it is a filesystem problem.

Sorry I couldn't be more help.

---

### Post by thobraa on 2008-03-16
You're help is greatly appreciated, very strange that those files (korean language localization) is creating problems. I didn't even know I had them on my computer, hehe. It could definitely be filesystem problem, but wouldn't fsck spot it? Is there maybe a way I can make apt-get skip this removal which it is trying to do everytime i run apt-get, so that I can install other software? I've tried different --ignore arguments but it always get stuck at the same error.

---

### Post by sandysandy on 2008-03-16
have a look here

[http://users.bigpond.net.au/hermanzone/p5.htm#Fix_Broken_Packages](http://users.bigpond.net.au/hermanzone/p5.htm#Fix_Broken_Packages)

regards

---

### Post by thobraa on 2008-03-16
Thanks for the tip, but I don't think it's a problem with apt-get, the file(s) that apt-get can't get around are the same file(s) that I can't delete if i try, even with root.

---

### Post by zvacet on 2008-03-16
Try this 

```
cd /usr/share/locale/ko/LC_MESSAGES
```

```
sudo rm -r vlc.mo.dpkg-new
```

---

### Post by thobraa on 2008-03-16
```

ozi@ozirms:/usr/share/locale/ko/LC_MESSAGES$ sudo rm -r vlc.mo.dpkg-new 
[sudo] password for ozi:
rm: cannot remove `vlc.mo.dpkg-new': Operation not permitted

```
I can chown 777 it but I'm not allowed to touch it as far as delete it.
```

ls -l vlc.mo.dpkg-new 
-rwxrwxrwx 1 root root 0 2008-03-14 23:32 vlc.mo.dpkg-new

```

---

### Post by unutbu on 2008-03-16
[http://www.dbforums.com/archive/index.php/t-572063.html](http://www.dbforums.com/archive/index.php/t-572063.html)

seems to suggest you can remove the file with unlink:
```

unlink /usr/share/locale/ko/LC_MESSAGES/vlc.mo.dpkg-new

```

Ironically, this command will corrupt your filesystem.
You would then have to run fsck to fix it.

---

### Post by thobraa on 2008-03-16
That's definitelty interesting, do you think there is a big risk with executing that command? I haven't done my backup yet, but if there is no chance of losing everything I'll try it without backup, I guess the words "corrupting the filesystem"makes me a bit jumpy.

First things first, now I'm heading out to celebrate my birthday :)

---

### Post by unutbu on 2008-03-16
Hey! Happy Birthday, thobraa!!! :guitar:

I think unlinking is not overly dangerous, but I have never done it myself (and I have a high level of fear about ruining someone else's system) so I have some reservations about recommending it.

That said, this article, [http://lwn.net/Articles/248180/](http://lwn.net/Articles/248180/),
leads me to believe unlinked inodes are a common occurrence, and the tone of the articles seems to suggest it's no big deal. 

If this was my computer, I would try unlinking, but part of the reason I wouldn't mind trying is because I periodically backup my data onto DVD, so nothing catastrophic can happen short of fires, tornados, hurricanes, nuclear fallout, or feral cats eating my disks. 

The undeletable file is not urgent compared to backing up, so I would recommend making a good backup first. Even if you choose not to try unlinking, I would recommend backing up. The peace of mind is worth it. Once you have up-to-date backups (and you're reasonably certain that they work and are complete) then you can act a bit more cavalierly.

---

### Post by thobraa on 2008-03-16
Thanks, most of the backup process is finished so I'll try out unlinking tomorrow I guess, so I don't ruin a good night sleep knowing that when I start up the computer it says: 
Os not found
I'm very optimistic about this unlinking though, thanks a lot for the help so far!

---

### Post by thobraa on 2008-03-16
I tried this now, unfortunately. Permission denied for this too.

```

sudo unlink /usr/share/locale/ko/LC_MESSAGES/vlc.mo.dpkg-new 
[sudo] password for ozi:
unlink: cannot unlink `/usr/share/locale/ko/LC_MESSAGES/vlc.mo.dpkg-new': Operation not permitted

```

---

### Post by ruibernardo on 2008-03-16
Can you post the output of
```
dpkg-divert --list | grep vlc
```This should list the links of "diverts" done by the package upgrades.

Files ending with "*.dpkg-new" or "*.contrib" are files that dpkg/apt moved (renamed). This is done by the command "dpkg-divert". It does this upon upgrades to keep copies of the original files it installs along the time. Nothing can remove them (they are files that where deprecated for some reason, they shouldn't be executed by the system, so dpkg/apt "steps them to the side" because the can/are still listed in some installed package. With "diverts" dpkg/apt still can find the original file of the original package and remove all the files without problems (depending on the package maintainer and the scripts on the .deb packages).

More info about this: [http://www.debian.org/doc/manuals/reference/ch-package.en.html#s-dpkg-divert](http://www.debian.org/doc/manuals/reference/ch-package.en.html#s-dpkg-divert)

---

### Post by thobraa on 2008-03-17
First I gotta say I'm surprised at how helpful people are and even if I don't solve the problem, I learn new stuff by every post from you guys, thank you!

I'm not sure what it should return when running the command, but I don't get anything in return. Here's what happens:

```

ozi@ozirms:~$ dpkg-divert --list | grep vlc
ozi@ozirms:~$

```

---

### Post by ruibernardo on 2008-03-17
What about

```
dpkg-divert --list vlc
```or look at the complete list with

```
dpkg --list
```That file must be there.

---

### Post by thobraa on 2008-03-17
When i do dpkg --list I get a long list, no vlc but vlc-nox which looks like this:
rH  vlc-nox        0.8.6.release. multimedia player and streamer (without X su
When I try:
dpkg-divert --list vlc-nox 
I get the same as before, nothing :s But I can see that vlc-nox in the whole list is different than the others because instead of 'ii' in front of it it says 'rH'. I don't know what it means but it is different from almost all the others on the list. Hope this clarifies.

---

### Post by ruibernardo on 2008-03-17
What is the output of
```
dpkg --audit
```

---

### Post by thobraa on 2008-03-17
```

ozi@ozirms:~$ dpkg --audit
The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 vlc-nox              multimedia player and streamer (without X support)

```

---

### Post by thobraa on 2008-03-17
```

ozi@ozirms:~$ dpkg --audit
The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 vlc-nox              multimedia player and streamer (without X support)

```

---

### Post by unutbu on 2008-03-17
I noticed the error to the unlink command was 'Operation not permitted'.
It may be because the parent directory has the 'append mode' flag. (man chattr).
When a parent directory has the append mode flag set, the files it contains can not be deleted! (Files two levels down can be deleted, but that's another story.)

```

10:11:43 cyrano@farmer:~% cd /tmp
10:11:44 cyrano@farmer:/tmp% mkdir appendonly
10:11:54 cyrano@farmer:/tmp% cd appendonly/
10:12:07 cyrano@farmer:/tmp/appendonly% touch damnhardtoremove
10:12:25 cyrano@farmer:/tmp/appendonly% cd ..
10:12:39 cyrano@farmer:/tmp% sudo chattr +a appendonly/
10:12:48 cyrano@farmer:/tmp% lsattr -d appendonly/
-----a------------ appendonly/
10:12:55 cyrano@farmer:/tmp% cd appendonly/
10:13:00 cyrano@farmer:/tmp/appendonly% ls -l 
total 0
-rw-r--r-- 1 cyrano cyrano 0 2008-03-17 10:12 damnhardtoremove
10:13:10 cyrano@farmer:/tmp/appendonly% rm damnhardtoremove 
rm: cannot remove `damnhardtoremove': Operation not permitted
10:13:17 cyrano@farmer:/tmp/appendonly% sudo rm damnhardtoremove 
rm: cannot remove `damnhardtoremove': Operation not permitted
10:13:26 cyrano@farmer:/tmp/appendonly% sudo rm -rf damnhardtoremove 
rm: cannot remove `damnhardtoremove': Operation not permitted
10:13:33 cyrano@farmer:/tmp/appendonly% unlink damnhardtoremove 
unlink: cannot unlink `damnhardtoremove': Operation not permitted
10:14:10 cyrano@farmer:/tmp/appendonly% cd ..
10:14:19 cyrano@farmer:/tmp% sudo chattr -a appendonly/
10:14:30 cyrano@farmer:/tmp% cd appendonly/
10:14:34 cyrano@farmer:/tmp/appendonly% rm damnhardtoremove 
10:14:37 cyrano@farmer:/tmp/appendonly% ls -l
total 0

```

In your case you can check if the append mode flag is set with
```

lsattr -d /usr/share/locale/ko/LC_MESSAGES/

```
If you see the 'a' flag, then maybe we are on the right track.

```

chattr -a /usr/share/locale/ko/LC_MESSAGES/

```

Then you may not even need to manually delete the file within. Maybe dpkg will simply stop giving errors. If that doesn't work, you may want to check further up the directory tree to see if any other directories have the append mode flag.

PS. My info comes from
[http://lists.debian.org/debian-isp/2002/05/msg00236.html](http://lists.debian.org/debian-isp/2002/05/msg00236.html)
[http://lkml.org/lkml/1998/2/26/5](http://lkml.org/lkml/1998/2/26/5)

---

### Post by ruibernardo on 2008-03-17
That file should be listed in "dpkg-divert --list". Since it wasn't, some package or upgrade must have left it behind. I don't understand why the file can't be removed. There must be an explanation for it.

To bypass the uninstall problem, I would remove the reference of that file that must be in the file /var/lib/dpkg/info/vlc-nox.list.

This is not recommended but can solve the remove package problem. 

To do it edit the file:

gksudo gedit /var/lib/dpkg/info/vlc-nox.list

Search for "/usr/share/locale/ko/LC_MESSAGES/vlc.mo.dpkg-new", delete the line, save the file and try "sudo apt-get install -f" again.

That way the postrm script will leave the nailed file alone and "vlc-nox" will be removed.

---

### Post by ruibernardo on 2008-03-17
unutbu found out why the file couldn't be remove. No need to do what I said in my previous post.

---

### Post by thobraa on 2008-03-17
Oh my god, I don't know how you figured out the solution but that did the trick. I have been trying to fix this since Friday I think, but thought I was stuck in a catch-22 and had to reinstall. I didn't expect too much when I tried to post this thread, but all the people with their suggestions and finally the soluton!! Amazing! Another great reason for why I stopped using windows for anything but games anymore, which gets more and more seldom :) Thanks for fixing the problem, have a great day!

---

### Post by thobraa on 2008-03-17
If you have any quick insights into how or why this probably happened I'd be happy to hear and learn.

---

### Post by unutbu on 2008-03-17
Yay!!!! So glad I could help. :popcorn:

---

