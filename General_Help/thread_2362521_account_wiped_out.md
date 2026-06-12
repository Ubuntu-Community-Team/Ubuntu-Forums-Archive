---
title: "account wiped out?"
date: 2017-05-29
forum: General Help
---

### Post by jason.nickols on 2017-05-29
So I had an issues with a program running on Ubuntu 14.04 which forced me to reboot.  After rebooting my desktop all personalized settings and some scripting files were just gone.  Not much was lost except for the scripting file i created everything else has been recoverable through backups.  Unfortunately i did not have the scripting files backed up outside of my user directory.  Any idea why that would happen and if/how to get them back.  Also considering upgrading to Ubuntu 16 if i perform the update from the pop up that comes up at boot will i lose any data.  Will definitely backup before but just curious how the upgrade will operate.  Basically is it supposed to be seamless like a Windows upgrade is supposed to be?

Thanks

---

### Post by RobGoss on 2017-05-29
That's really odd you would just loose your file like that, I would not know what would cause something like that unless you made some kind of change to your system

As for the upgrade if you have **14.04,** and you want to upgrade to **16.04,** I would do a clean installation and avoid any problems you might 
run in to. forcing your system to power down is never a good thing and may cause all sorts of problems

Make sure you have a complete backup of any important data and file just in case

---

### Post by shridhar-kapshikar on 2017-05-30
Which program were you running which forced you to reboot?

I would recommend do a clean installation of Ubuntu 16.04 in order to avoid any future issues. Make sure you have a complete backup of all files in the case. Boot the system from Ubuntu 16.04 bootable device and perform a clean installation.

---

### Post by jason.nickols on 2017-05-30
yeah i'm just stumped where everything went.  thought it might have placed my data somewhere but it just blanked out and it is as if it was a new user account.  the program i was running that froze everything up is called jriver media center which i have ran for over a year or more on this system without any issues.  Aside from that I have not made any major changes.  I did recently DL a few programs from software center but had only ran one of them since installing.  the other thing i did not mention is that i am running LXDE desktop on top of 14.04.  Not sure if it matters but thought i would add that in.  The programs i installed from Lubuntu software center are; 7zip, audacity, docky, gnome commander, musicbrainz picard, terminator (multi terminal windows in one), gnome tweak tool, unity tweak tool, and VLC.  Wasn't sure which tweak tool i needed so i downloaded the both to see which would work.  Audacity may have been downloaded outside of software center but that was the only one.  The only program i actually ran prior to this problem was terminator.  Just worried the it could be some kind of virus, although I can't imagine it to be the case.  This system is not used but to serve media and backup other systems.  I have also upgraded to the latest version of a program called 'home assistant' (home automation platform; runs on python) which happens to be the program that the files i lost were for.  Aside from this stuff i have not made any config changes or anything that could affect anything afaik.  I'm still a novice when it comes to Linux but cannot imagine anything I downloaded or ran could have caused this.  It sucks that I lost the files that i did but it's nothing major that i cannot recreate.  I just really would like to know why/how this happened but doesn't look like i will get that answer.

I know this is a lot of info and most of it isn't pertinent but thought i would throw everything out there that i can think of that i have done recently as maybe something sticks out.  At this point I'm more curious what could have caused it than anything.

As far as creating backups of my critical data.  This primary purpose of this system of for serving media, all of which is on separate partitions and discs.  I plan to remove these drives from the machine before upgrading just to be safe and then mounting afterwards.  Aside from that, all i really need to back up is my user account, some config and network settings, and a mysql database.  Any suggestions for a user friendly program to help me with that?  I do use webmin and know it has some backup capabilities but not sure if it can cover all my needs.

Thanks for the help

---

### Post by cariboo on 2017-05-30
After a forced power off, restart in recovery mode, and choose root from the menu, once at the prompt type the following command:

```
fsck /dev/sdXX
```

where /dev/sdXX = the partition you have your home directory installed on.

---

### Post by jason.nickols on 2017-05-30
> **cariboo said:**
> After a forced power off, restart in recovery mode, and choose root from the menu, once at the prompt type the following command:

```
fsck /dev/sdXX
```

where /dev/sdXX = the partition you have your home directory installed on.


How do i find out what partition/directory that is?

---

### Post by howefield on 2017-05-30
> **jason.nickols said:**
> How do i find out what partition/directory that is?

From the recovery console you could try the command

```
df /home
```

eg, on this system /home is mounted on sda1

```
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1       37070220 6224728  28932724  18% /
```

so

```
sudo fsck /dev/sda1
```

would check the partition, but it would need to be unmounted for fsck to run, so probably best done from a live media.

---

### Post by Impavidus on 2017-05-30
You don't say whether your system or home directory is encrypted or not. If encrypted, that makes it easier to explain why everything is gone when you hit the power button and far harder to get anything back.

If your system is clean, release upgrades tend to work. I always keep my systems clean and upgrades always work here. Just a few minor issues, never lost any files, always got a working system. But not everyone is so lucky.

Lubuntu 14.04 reached end of life last April. The parts it has in common with Ubuntu are still supported, so you still get most updates, but those updates are no longer tested for compatibility with Lubuntu-specific packages. This also applies if you install some Lubuntu-specific packages on Ubuntu.

Have you checked the log files in /var/log? You may find something interesting around the time when you rebooted.

If you're forced to reboot, try doing so using SysRq+REISUB: the [magic SysRq key]("https://en.wikipedia.org/wiki/Magic_SysRq_key"). That at least cleanly unmounts the file system.

---

### Post by jason.nickols on 2017-06-01
@cariboo; @howefield - i ran 'df /home' from recovery and it came back with '/dev/dm-0'  "mounted on /"  is this the correct drive i need to fsck?  i was expecting something starting with 'sda' or 'sdb' so not sure this is right.  My primary (OS) drive is a SSD, is this the designation for such drives?  Also i am running btrfs but NOT on the OS drive, only my data drives.  I'm guessing that shouldn't matter unless I was using btrfs for the OS disk, which is using the default file system provided when i did the initial install of ubuntu.  

edit - i tried running fsck on /dev/dm-0 from ubuntu 16 live (try before install option) and it reported as clean, guess i'm out of luck as far as recovering lost data.  Not a big deal, wasn't much lost that i cannot recreate.

As far as backing up configuration to clean install 16.04; do you have any recommendations on how to go about that?

---

@Impavidus - The system is not encrypted. Not sure what you mean by "clean", i have made some changes to config file and added the Lubuntu desktop, and installed a few programs.  Other than that it is plain Ubuntu. When first installing.  It was recommended I use Lubuntu as it was a lightweight desktop, but seeing as how this is just a home server and not subject to heavy loads, after upgrading to 16 will start using the default desktop.

---

### Post by howefield on 2017-06-02
> **jason.nickols said:**
> @cariboo; @howefield - i ran 'df /home' from recovery and it came back with '/dev/dm-0'  "mounted on /"  is this the correct drive i need to fsck?  i was expecting something starting with 'sda' or 'sdb' so not sure this is right.

Sounds like you have used LVM for the disk ?

> As far as backing up configuration to clean install 16.04; do you have any recommendations on how to go about that?

What configuration ?

You should be able to copy files from the disk to an external disk / USB stick using the recovery mode or Live media. 

PS. This (being a server) would be better run without a desktop environment.

---

### Post by jason.nickols on 2017-06-04
I ended up doing a clean install of 16.04; I figured it was easier/less time consuming than trying to recover what was lost.  Ran into a few snags, but nothing I couldn't figure out.  Managed to save my database files, but had to redo some configuration settings.  Everything is back to the way I had set up originally; probably a little leaner/cleaner than it was before.  It was a good refresher.  Thanks for the input.

---

### Post by RobGoss on 2017-06-05
Glad you got it all sorted out sometimes a clean start it whats needed. 

I'f you resolved this issue you can mark this thread as **solved**, you can use the **Thread tool** at the top of this post

---

