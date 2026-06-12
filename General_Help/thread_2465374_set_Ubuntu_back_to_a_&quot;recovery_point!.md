---
title: "set Ubuntu back to a &quot;recovery point!?"
date: 2021-07-31
forum: General Help
---

### Post by steveson on 2021-07-31
Hi out there

I&#7743; new to Linux world (:D and pretty proud that I've setup everything well so far)

Then I tried to install PGP GPG (KGPG and openPGP applet) for private messaging and now my sytem is mis-configured. At least some programs are missing... what else i&#7743; not sure yet.

I remember from windows that one could set the system back to a point, where it all still worked.

Does this exist for Ubuntu? How can I set back?

Thanks for help and cheers!
Steve

---

### Post by mikewhatever on 2021-07-31
No, Ubuntu is not Windows. There aren't any restore points, unless you make one.

You can reinstall the default set of programs by reinstalling the "ubuntu-desktop" package, which may have been uninstalled.

> sudo apt install ubuntu desktop

---

### Post by dragonfly41 on 2021-07-31
The equivalent might be "versioned backups".
Search the forum (advanced search) targeting posts by the user - TheFu - who is an advocate on this subject.
This will also give you experience in using self learning "advanced search" feature (see top right of this page)

---

### Post by steveson on 2021-07-31
thanks

---

### Post by steveson on 2021-07-31
alright, I'll try this. thanks.

---

### Post by scorp123 on 2021-07-31
> **steveson said:**
> Does this exist for Ubuntu? 

As others have said: Linux is not Windows. The closest thing you could have to this, is if you used **ZFS** as filesystem during installation (it's marked as being an "Experimental feature").
[https://ubuntu.com/blog/zfs-focus-on-ubuntu-20-04-lts-whats-new]("https://ubuntu.com/blog/zfs-focus-on-ubuntu-20-04-lts-whats-new")

If ZFS was used during installation you could basically *"go back in time"* and boot your whole system like it was at the time a particular system state was saved:
[https://didrocks.fr/2020/05/28/zfs-focus-on-ubuntu-20.04-lts-zsys-general-principle-on-state-management/]("https://didrocks.fr/2020/05/28/zfs-focus-on-ubuntu-20.04-lts-zsys-general-principle-on-state-management/") 


If you did not install your system with ZFS then you will need to resolve your issue the old-fashioned way: Get rid of the offending package via "Software" management and also get rid of any configuration files it may have left behind.

"Linux is not Windows" is a good thing too here: There's no "Registry" that can so easily be corrupted and Linux is actually quite easy to repair. The ability to *"go back in time"* thanks to ZFS is just an added bonus but Linux can do fine without it.

But if this is a feature you really really want then consider choosing ZFS for your next installation?

---

### Post by grahammechanical on 2021-07-31
And there is also the B-tree file system (btrfs). I experimented with this a few years ago with Ubuntu desktop. It works. We can create a system snapshot and when we are at the Grub boot menu and select Advanced Options for Ubuntu and select a kernel with recovery mode we get a recovery menu that will include an option called apt-snapshot which has its own menu where we can create, revert to, delete-older-than, list-older-than, list-snapshots and take-apt-snapshot. Mind you this was a few years ago. Things might be a bit different now. Things progress.

Keep in mind that this discussion is two years old.

[https://discourse.ubuntu.com/t/switch-to-btrfs-by-default/9783](https://discourse.ubuntu.com/t/switch-to-btrfs-by-default/9783)

Regards

---

### Post by Tadaen_Sylvermane on 2021-07-31
Is also LVM snapshots but that isn't a live thing. Would need to restore it, when it's done reboot. I think it would work that way anyway. I've messed with it on vms before. Takes awhile though. Not sure if it qualifies really as a restore point.

---

### Post by GhX6GZMB on 2021-07-31
Just use Timeshift backup/restore. I always do this when fiddling with my system. Needs a reboot after restore, though.

---

### Post by ActionParsnip on 2021-07-31
Could boot to live CD and make an ISO of the boot disk (I assume that /home is on a different disk and the root file system is a smaller file system)

---

### Post by steveson on 2021-08-08
Thanks to all, I'll try out what suits best to me. And yes, Linux is not Windows. But I'm happy I did the change, even if it is a bit difficult to understand at the beginning

---

### Post by monkeybrain20122 on 2021-08-08
As others say there is nothing like "restoring point" but Archlinux and derivatives allow you to downgrade packages should something go wrong, this is probably the closest thing to "restoring" without restoring the whole system from a snapshot (creating by something like clonezilla or fsarchiver, say). AFAIK this is a unique feature to Arch not available in other distros. E.g if some upgrade in Ubuntu messes up your system there is usually no easy way to go back since the earlier versions are no longer available, reinstalling the package would just give you the same defective version, in Arch you can downgrade it to the previous working version.

---

### Post by TheFu on 2021-08-08
Versioned backups are the ideal, gold-standard, solution.  They've worked for 50 yrs on all computing platforms. Nothing new needs to be invented.
In the Unix world, you could create something like a "restore point" with a little scripting, but that would be on you. It would be much easier to create versioned backups - and everyone needs those anyways, so there is little demand for keeping track of exact config files and exact software versions installed.  Though it wouldn't be hard at all.

To get the list of installed packages, including versions, 
```
dpkg -l

```
All system config files are in /etc/ - which is a fairly small directory, include that in your "restore point" file.

Any personal seeing will be in the HOME directory of each user on the system. You could guess that most of them will be in ~/.config/ but that isn't the only location. Some programs put their config files either in .files or .directories under the HOME.  There are lots of temporary files that get placed into those as well, so whether you want those or not makes it just a little more difficult.  Either include only the stuff you want or exclude the stuff you don't want. Whenever a new program gets installed, that could create a new .directory/.file that should be included. Hard to say, since Linux isn't a dictatorship. It is more like a bazaar with thousands of tiny shopkeepers each doing their own thing.  That's fantastic and terrible at the same time. ;)

With a list of the APT packages, you have those and can feed that list into a package installation tool like apt or aptitude.

That's nearly everything.

Then Canoncial started using more and more snap packages.  I think by default, 3 versions of any snap are kept, so you can change between those versions. Keeping a list might be helpful, just like keeping a list of APT packages is helpful.
```
snap list
```

So ... let's put that all together to make a "restore point" file ...

```
#!/bin/bash

# create the lists
dpkg -l > /tmp/dpkg.list
snap list >  /tmp/snaps.list

# Put everything into an archive
tar czvf /tmp/restore-pt-files-$(date "+%F").tgz /tmp/dpkg.list /tmp/snaps.list \
          /etc  ~/.config  ~/.thunderbird  ~/.mozilla

echo "Done."
```
Then make the script executable and run it:
```
$ chmod +x mkrestore-point 
$ ./mkrestore-point
...

$ du -sh restore-pt-files-2021-08-08.tgz 
202M    restore-pt-files-2021-08-08.tgz 
```

That seems a little bloated to me.  There were a bunch of files that weren't needed. Mostly under ~/.thunderbird and ~/.mozilla  But it is better to have a file and not need it than not to have that file and really need it. 
There are all sorts of issues with that little script. We are all different, so it is likely missing something that is very important for some people, but not important to me.  

The list of snaps is tiny.
The list of installed packages is ~310KB.  
```
-rw-rw----  1 thefu   thefu   211423908 Aug  8 17:27 restore-pt-files-2021-08-08.tgz
-rw-rw----  1 thefu   thefu         847 Aug  8 17:27 snaps.list
-rw-rw----  1 thefu   thefu      311382 Aug  8 17:27 dpkg.list
```

/etc/ is 18MB on my system. 
```
$  du -sh  ~/.config
138M    /home/thefu/.config

```

If you use other programs, be certain you include those settings in your version of the script. Many will be put into ~/.config, which is already included, but a few may not. To get files from other user's HOME directories will be a greater challenge.  Use the ~{userid}/.config method, so I'd use ~steveson/.config and ~thefu/.config in my list for the tar command if I wanted both those user's config files.  Handy shortcut.

Hope this helps someone.

---

### Post by monkeybrain20122 on 2021-08-08
> **TheFu said:**
> Versioned backups are the ideal, gold-standard, solution.  They've worked for 50 yrs on all computing platforms. Nothing new needs to be invented.
In the Unix world, you could create something like a "restore point" with a little scripting, but that would be on you. It would be much easier to create versioned backups - and everyone needs those anyways, so there is little demand for keeping track of exact config files and exact software versions installed.  Though it wouldn't be hard at all.


 
I am not sure how you restore your system with that (I take OP to mean restoring to a previous state) It looks like all you did was making list of all packages installed so you can reinstall them along with the config somewhere (maybe in a fresh Ubuntu install). But you are not really making  a snapshot this way as there is no version control. So if you say restore foo it would be the same foo from the repo that caused your system to break in the first place (let's say system broke because of bad update), not the previous working one which has been removed from repo now.

---

### Post by TheFu on 2021-08-08
> **monkeybrain20122 said:**
> I am not sure how you restore your system with that (I take OP to mean restoring to a previous state) It looks like all you did was making list of all packages installed so you can reinstall them along with the config somewhere (maybe in a fresh Ubuntu install). But you are not really making  a snapshot this way as there is no version control. So if you say restore foo it would be the same foo from the repo that caused your system to break in the first place (let's say system broke because of bad update), not the previous working one which has been removed from repo now.

Restore points have to be taken BEFORE they are needed, right?

My mkrestore-point is the same. Needs to be stored off before it is needed too.  

The tgz is date-stamped. Put it somewhere that won't be lost .... but having automatic, daily, versioned, backups would likely be easier and better.  My backup technique doesn't actually backup the OS, boot stuff, or applications.  It gets the list of manually installed packages, all personal and system settings, then it goes for data.

For a restore, start with a minimal Ubuntu install, then put everything back in reverse order ... data, settings, then install the packages from the manually installed list.  This will mean that to APT, it will see both the data and the settings, think a re-install for a package has been requested and pull in any dependent packages as needed. It is surprisingly easy.  I've gone back over 30 days for a DB that got corrupted and nobody noticed. Guess it was part of a monthly process, not a daily process.  Figured out the newest version of the DB file that wasn't corrupt, and put it back along with the indexes and settings for the DBMS in that backup set.  Worked nicely.

Best of all, I wasn't constantly backing up 4-10GB of OS junk that takes 15 minutes to install from the ISO.

Getting old versions of software is something I've not had an issue. apt-cacher-ng keeps the last version or 2 of files and automatically expires them over time. That can be configured. Running an apt-cacher server probably isn't for someone new, but using LVM/ZFS/btrfs snapshots isn't either.  There is always a knowledge hill to climb the more people want to do things not commonly done.

Daily, automatic, versioned, backups are still the answer for most people.  If doing it like I do doesn't make clear sense, then don't.  Spend the extra time and extra storage on having nearly full system backups. It isn't the end of the world for 1-2 systems at home.  When I setup my backups, I was running 20 systems and having an extra 4G for each of those backups just seemed foolish.  My email gateway doesn't actually have **any** data on it. It is purely for processing email in and out of the network. Nothing else.  It is a high risk server, so I need lots and lots of versioned backups.  
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Aug  8 01:30:02 2021         63.7 MB           63.7 MB   (current mirror)
Sat Aug  7 01:30:02 2021       424 bytes           63.7 MB
Fri Aug  6 01:30:03 2021       938 bytes           63.7 MB
Thu Aug  5 01:30:02 2021       900 bytes           63.7 MB
...
Tue Apr 13 01:30:02 2021       424 bytes           63.9 MB
Mon Apr 12 01:30:02 2021       865 bytes           63.9 MB
Sun Apr 11 01:30:03 2021         1.29 KB           63.9 MB
```
Daily backups going back to April are using 64MB on that system because it is just config files and firewall rules. In theory, I can bring a new system up in less than 30 minutes from those backups.  They are also a great way to move from system A ---> system B when new hardware arrives. I get faster processing AND a chance to test the backup/restore process.

The really great thing about the restore process is that it isn't tied to any hardware or file system layout.  I can change anything, provided the directory structures remain consistent. RAID, LVM, ZFS, whatever doesn't matter. Rip one out and put a completely different one in. It works that way for all my backups versioned backups.  Media files only get a mirror backup. I just don't have the money to spend on versioned backups for 32TB of junk.

---

### Post by Advait on 2021-08-25
> **steveson said:**
> Hi out there. I&#7743; new to Linux world (:D and pretty proud that I've setup everything well so far). Then I tried to install PGP GPG (KGPG and openPGP applet) for private messaging and now my sytem is mis-configured. At least some programs are missing... what else i&#7743; not sure yet. I remember from windows that one could set the system back to a point, where it all still worked. Does this exist for Ubuntu? How can I set back?
Thanks for help and cheers!
Steve

> **ml9104 said:**
> Just use Timeshift backup/restore. I always do this when fiddling with my system. Needs a reboot after restore, though.

I want to second and reinforce what ml9104 posted. I'm also a Linux/Ubuntu newbie. Soon after I installed Ubuntu 21.04 I installed and setup Timeshift to make regular system snapshots. I then got into the habit of taking Timeshift snapshots before I installed apps or did updates/upgrades. I'm very happy I did! 2 weeks ago I installed something that was messing up my system and had no idea how to fix it. Finally I did a Timeshift restore to an earlier time and it worked great. The problem went away. So now I recommend to all Linux/Ubuntu newbies to get Timeshift up and running and get in the habit of using it. And turn on the Timeshift 'Schedule' features. I take about 5-8 snapshots everyday, just in case.

Context: Timeshift is not for backing up user files, just system files for snapshots. Use other apps to backup/sync your user files. Also learn Clonezilla/Rescuezilla if you haven't already done so; it's great for making images and clones.

---

### Post by Advait on 2021-08-25
In the future I may switch to LVM cuz from what I've read it does a better job of making snapshots. I'm a Linux newbie so I need to read more to know the details.

---

### Post by mastablasta on 2021-08-25
BTRFS (file system ) also has snapshots which are handy for this particular case. for some reason i found it would complicate my life when automatic shortcuts and such are created. so i went with the default EXT4. however if i used system only as home user then BTRFS seems a good choice for keeping version backup in case you mess up some settings.

---

