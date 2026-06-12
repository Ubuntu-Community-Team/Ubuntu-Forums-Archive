---
title: "Archive Splitting/Backup and Restore; Kernel Not Included"
date: 2014-09-25
forum: General Help
---

### Post by SciGuy1872 on 2014-09-25
I have multiple DVD's and cannot fit the backup of / (that includes /home, /Downloads, /Documents, etc., right?  I can browse the File System and browse the aforementioned folders through the Home folder once double-clicked) onto my single, 4GB USB.  The reason I need to do this is that the kernel on this hdd is EOL, so on the other disk, I have a fresh install of 12.04 with the 3.2 kernel being supported to 2017; so, I need to backup everything EXCEPT the kernel and graphics stack.  

Since the DVD holds 4.7 GB of data, I am restricting the size of the splits to 4500m:
tar -cvpz backup.tar.gz --exclude=/backup.tar.gz / | split -d -b 4500m - /home/anthony/Desktop/backup.tar.gz. 

Is this command correct?  Then the individual files, I can burn to DVD's and paste them to the Desktop on 
the other hdd and reconstitute them, after the cd to Desktop, with the command:

cat *tar.gz* | tar -xvpzf - -C /  

Is this command correct?  

After this, I use the following command to restore the other hdd, so that it is just like this one, except 
the kernel and graphics stack, correct?

sudo tar -xvpzf /home/anthony/Desktop/backup.tar.gz -C /media/whatever --numeric-owner

What should I include for the term "/media/whatever"?  Do I need to restore GRUB?--I changed the files, but
I am still booting into Ubuntu. Is this command correct if I do need to restore GRUB:

sudo -s for f in dev dev/pts proc ; do mount --bind /$f /media/whatever/$f ; done
chroot /media/whatever dpkg-reconfigure grub-pc

I found these instructions on (the part about GRUB was not very detailed, so I'm hoping I can skip
it--because I don't really understand the command):

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

After all this is done, is there a command I can issue in the CL to hold the kernel--I figured I would just
add the question since I am already posting.

Thanks for your time!

---

### Post by ian-weisser on 2014-09-25
Most users should only backup and restore data between versions (the contents of your /home/$USER directory ).

Advanced customizations - crontabs, upstart jobs,  custom /etc files, firewall configs, links, etc., can also be backed up and restored. However, you need to know what you are doing - that's why it's advanced. Backing up most stuff outside of /home is a waste of time and space.
 
Do not bother to backup/restore applications. Install the applications from the new (12.04) Ubuntu repositories instead of a backup. The updated versions are free.

---

### Post by SciGuy1872 on 2014-09-25
I'm not sure what you mean, ian-weisser.  I have files in /usr/games, /usr/share/games, and usr/share/celestia, about different programs--don't these files need to be backedup/restored to the other drive so that, well, Celestia, for example, can function with all the data I've added on to the program?  Also, if I install applications from Synaptic, I lose all of my aircraft and scenery for Flightgear--is that not correct?

---

### Post by ian-weisser on 2014-09-25
Yes, you may lose all your customizations when you install fresh copies from the Ubuntu repositories.
Then you re-add your saved data to those applications. Jut like you added them the first time.

It also depends on where the additional game data is saved. If it's in (example) /home/$USER/.celestia, then it will be copied across to your new install, and the new version of Celestia should pick it up automatically. If it's a module you added to (example) /usr/games/celestia/addons then you must make a point to copy it across. My point is that the latter is considered 'advanced', and *don't* copy all of /usr just to get that one directory.

My own /home/$USER includes a directory of customizations, with documentation and links to their location, specifically so I don't need to backup anything else. I can reinstall my data in a new /home, refresh my links, and everything is back.

You can certainly try your original idea to restore older package files onto a newer system. But be quite prepared for it to not work, to possibly break your package manager, and perhaps even to crash your system.

---

### Post by SciGuy1872 on 2014-09-25
It's not really a newer system--it's the same Precise, just an older kernel--3.2 (the first release I think); this hdd is 3.5.0-54; EOL, unfortunately.  Does that make a difference in the warnings?; what about the commands?

---

### Post by SciGuy1872 on 2014-09-25
It's not really a newer system--it's the same Precise, just an older kernel--3.2; this hdd is 3.5.0-54--EOL, unfortunately.  Does that make a difference in the warnings?; what about the commands?

Should I have asked this question in the General Help--can I fix it by labeling the post as solved, then post to General Questions?

---

### Post by ian-weisser on 2014-09-26
The issue isn't moving between different versions or kernels - it's moving between installations. The advice is the same.
Advanced users use a separate /home partition for this use case of booting into more than one install.

You can move this thread to General Help if you wish, but many of the gurus patrol all the sections. I doubt the answer will change much.

---

### Post by SciGuy1872 on 2014-09-27
I was warned by ian-weisser about this process: 

"You can certainly try your original idea to restore older package files   onto a newer system. But be quite prepared for it to not work, to   possibly break your package manager, and perhaps even to crash your   system." 

I replied that the other hdd is not newer--just the same OS (Precise)  and an older kernel (3.2).  I have files in /usr/games, /usr/share/games, and  usr/share/celestia,  about different programs.    There may be other directories that I do not know I need to copy and  paste--Opera, for example.

Why should backup/restore crash my Ubuntu system?  I thought that this  process on Linux machines was supposed to be easy--I read a post (looked  for the original How To--an old thread, but couldn't find it) that  stated that Linux wouldn't even need to do the things Windows does--like  enter a special boot to restore.

I'd rather use the splitting procedure I wrote about, if it would be  fine, because I understand it and have no trouble with the CL.  I would  need help with GRUB if I'm going to have trouble with it.  What do you  all make of this process--would it work, or is there a chance it would  destroy my system; other options?  Would the kernel and graphics stack  be left out with tlhis splitting procedure?

---

### Post by Impavidus on 2014-09-27
This sounds like a terribly complex way to do something relatively simple. If you restore the entire system except the kernel from a backup, you'll also restore the list of installed software packages from the backup. This list contains a mention of the currently installed kernel. The package manager on the 3.2 system will think it has the 3.5 kernel and not the 3.2 kernel, so there won't be updates and the package manager will get confused. You'd still have to tell the package manager you want the 3.2 kernel, but telling this to the package manager would pull in the 3.2 kernel automatically.

Each kernel is just pulled in by a package, so I think it should be possible to just install the package for the 3.2 kernel instead of the 3.5 kernel on your existing system, reboot into the 3.2 kernel and uninstall the 3.5 kernel, converting your existing system.. I'm not on my old 12.04 system right now, so I can't give you the exact package names, but I think the 3.2 version has something like just linux-image-generic and the 3.5 version has quantal attached to its name.

BTW, I keep my flightgear stuff on a separate /usr/local partition and moved it from 12.04 to 14.04, together with some other data and script files.

---

### Post by SciGuy1872 on 2014-09-27
Thanks for the reply; are you saying that I can just use Synaptic to install the 3.2 kernel over the 3.5?  

I created another thread ([SIZE=3]Unsure Package List for Downgrading Precise kernel to 3.2.x in Synaptic)[/SIZE]
 because I thought I could use this process of using Synaptic, but deadflowr, a forum moderator wrote this:

"Like Sudodus stated, somewhat, downgrading, or installing the 3.2 kernel  is only part of the problem, and is most likely the easier part to deal  with. The real problem would be, you need to also downgrade that graphics stack, which is will be a lot more problematic".

Another responder (Bashing-om, an Ubuntu member) to the stated post said this:

"Back up your personal data and (RE-)install.  Where there is a will there is a way"

When I tried to use Package Manager to return to 3.2 (before the earlier posts were made), the Manager reported this: 

"You likely do not want to install this package directly. Instead, install
     the linux-generic-pae meta-package, which will ensure that upgrades work
     correctly, and that supporting packages are also installed".

This gives me pause.  I have a  32-bit, 1.2 GiBytes of RAM, and for the architecture, i386.

---

### Post by ian-weisser on 2014-09-27
Sudodus and Bashing-om are right.

> **SciGuy1872 said:**
> "You likely do not want to install this package directly. Instead, install
     the linux-generic-pae meta-package, which will ensure that upgrades work
     correctly, and that supporting packages are also installed".

A normal user in normal use should indeed use the metapackage.
You want to do something quite abnormal. Don't use the metapackage. Specify the kernel package (linux-image) directly.

Make sure your data is properly backed up. There is risk of breaking your system when you downgrade the kernel and graphics stack.

---

### Post by SciGuy1872 on 2014-09-28
I do not want to take the chance that this 3.5.0-54 system is broken--it  is the only drive out of the two that has all of my programs in a  current state; the other hdd has the 3.2 that only has a fresh copy of  12.04.  I have another XP partition on both drives.  If there's a  problem with manipulating the 3.2, all I have to do is install again.  

I don't think the concern from the first sentence is valid--I can just move Home, Downloads, Pictures, Music, Documents, Desktop, and File System to DVDs, then I'll always to be able to restore everything back the way it currently is, correct;?  Why can't I simply paste the aforementioned folders to the other 3.2 that just has the fresh install?--is that due to the package manager on the 3.2 system will think it has the 3.5 kernel  and not the 3.2 kernel, so there won't be updates and the package  manager will get confused, like Impavidus wrote?

I guess if I'll be safe after copying those folders, I can try to downgrade the kernel and graphics stack, if that would be more safe.  I don't really care about the time it takes, or the amount of commands I have to issue to the CL.  A poster to the Package List post, deadflowr, wrote that the more difficult task would be downgrading the graphics stack; if I go to Package Manager and install the metapackage file, is it going to also downgrade the graphics stack, too?

Bashing-om wrote that "UHMM... one can not downgrade the kernel" and that I had two options: upgrade the kernel to a supported version, or do a fresh install--followed by: "the "better" most recommended method to get the kernel ( and the Xserver  version) that you require is to do a clean fresh install of release  12.04".

Impavidus also wrote that I would need to, if downgrading does work, boot into the 3.2 and uninstall the 3.5--how do I choose what kernel I boot into (I think I select it at the GRUB menu, right)?  Is the only Package List name I need to install from Synaptic the 3.2.0-64-generic (I have 1.2 GiB of RAM) metapackage; how do I find the metapackage I wish to install?

---

### Post by SciGuy1872 on 2014-09-28
If I did paste the contents of all folders to the 3.2, and then had the problem that the package manager was confused about the kernel version, I could open Synaptic and type "3.5.0" into the search bar, then uninstall the three files the Manager lists, thereby avoiding the issue of downgrading the kernel, if Bashing-om is correct.  Right?

---

### Post by Impavidus on 2014-09-28
Sudodus and Bashing-om know what they're talking about. Reinstall may be the most reliable way. You should be able to simply backup and then restore your /home directory (which contains Document, Downloads et cetera). If you do this with system directories you can expect other problems. The things mentioned as file systems are other partitions, which  shouldn't be touched in your operation (but as always, you have backups  of important stuff on those). If you installed all your add-ons of various programs cleverly, it should not be too hard to backup just them.

---

### Post by SciGuy1872 on 2014-09-28
Okay, thanks for the advice to just backup the home directory--I have to go to Walmart and buy a 8GB usb drive for this operation.  I'm most concerned with getting back all the add-ons for programs Flightgear and Celestia; the Celestia files, I guess, I'll recover them after I install the program from Software Center, then I can just paste the files in /usr/share/celestia?  As for FG, I have Aircraft and Scenery saved in the home directory--I just hope that Software Center lets me install version 3.0.0--I have an old GeForce FX 5200 and I already get a line that says to upgrade to a level-300 driver.  Are there more clever ways?--the Celestia isn't as good as it can be, probably.

---

### Post by Impavidus on 2014-09-29
The software centre of Ubuntu 14.04 has FlightGear 3.0. I created a file **.fgfsrc** in my home directory with, amongst others, the lines```
--fg-scenery=/usr/local/share/flightgear/Scenery:/usr/share/games/flightgear/Scenery
--terrasync-dir=/usr/local/share/flightgear/Scenery
--enable-terrasync
```These are simply command line options read by flightgear in addition to the options you explicitly give on the command line. The first tells to look for additional scenery in /usr/local/share/flightgear/Scenery, the second and third instruct it to automaticall download and save additional scenery to that directory, where I gave myself write permission. Something similar must be possible with the aircraft (except the automatic downloading and installing part), but I didn't manage to do so. It seems the documentation on that point was a little outdated. I unpacked the aircraft in /usr/local/share/flightgear/Aircraft and created symlinks to all of these aircraft directories in /usr/share/games/flightgear/Aircraft, where the default aircraft are located.

My /usr/local is on a separate partition, so I can move it from one Ubuntu install to the next. Additionally, if the scenery overfills the partition it will just give an error there, without affecting either the root partition or my home partition.

I have installed celestia, but haven't really come to the point of installing a lot of add-ons. There seems to be a **--extras-dir=<extras-directory>** command line option, which I guess can be used to tell it where you installed additional stuff.

---

### Post by SciGuy1872 on 2014-09-29
I have a Celestia folder in my home directory where I unzip the downloaded file to; the unzipped files give instructions as to where to put the folders, some instructions are better than others.  I get all files for this program from:

[http://www.celestiamotherlode.net/](http://www.celestiamotherlode.net/)

Celestia is really good!  The planets all turn with time; that's interesting for Earth because I can run the program and rotate to find wherever in the day-cycle or night-cycle a given place is (GB, India).  Plus, Celestia allows for the user to travel through space--I can go to Andromeda and rotate, zoom in or out, and I am sure the Galaxy rotates with time as well.  Another way Celestia is better than World-Wide Telescope is that you can customize almost everything: in WWT there is no option to view (zoom, rotate) Titan, but Celestia does.  I wrote to MS (I was using XP) and stated that Titan should be there--it's the only moon in our solar system to have an atmosphere, and it has lakes.

---

